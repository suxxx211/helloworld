### 进程组
会话首进程,也是进程组的组长,KILL掉它,会导致SIGHUP发送给该进程组的每一个进程(就是所有父进程为3803的那些),默认情况下,SIGHUP会终止进程,所以全没了.

所有进程都是属于一个进程组的,而进程组又属于一个会话.
普通的进程所属的会话有控制终端,守护进程所属会话没有控制终端.
普通会话的首进程,同时也是建立与控制终端联系的进程,在它被KILL掉时,会向前台进程组就(a.sh)发送SIGHUP信号.默认情况下,接收到SIGHUP的进程会被终止.此时后台进程组(b.sh)不受影响.
守护进程的会话,因为没有控制终端,所以就没有前后台进程组之分,会话首进程同时也是进程组组长.它被KILL掉会向该组每个进程发送SIGHUP,导致组中进程被中止.

