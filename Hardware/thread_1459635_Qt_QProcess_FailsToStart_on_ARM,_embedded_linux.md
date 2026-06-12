---
title: "Qt QProcess FailsToStart on ARM, embedded linux"
date: 2010-04-21
forum: Hardware
---

### Post by Krzysztow on 2010-04-21
Hi everyone,

I have this problem and can't overcome it. Maybe someone of You has an idea. I would really appreciate it. So goint to the problem...

In my application I need to start mplayer with radiostation url. And it works for few first times. After I play with some gui in the application and want to start the process again, I get FailedToStart error and nothing happens. The arguments are the same, and the program "mplayer" still exists.
In the documentation, they write:
"The process failed to start. Either the invoked program is missing, or you may have insufficient permissions to invoke the program."
However this is obvious, none of the cases apply to mine. But it still fails.
Additionally, this happens when the program is run on Embedded Linux. Running on Ubuntu, haven't gotten this kind of problem.

Thank You in advance, for any help.

---

### Post by Krzysztow on 2010-04-22
Hi, me once more...

So I run my application and on the second consloe observe the "top" output. And this QProcess::FailedToStart comes out, when the VSZ (Virtual Memory Size) approaches 270m. But from the console mplayer may be played, so this is not a physical limitation of the hardware, but probably some limitation to a process. 

So this is the state (top process run) when mplayer is running correctly:

```

  PID  PPID USER     STAT   VSZ %MEM %CPU COMMAND
 2289  2229 root     R    16244  26%  12% mplayer -demuxer aac http://gr-relay-3.gaduradio.pl/45 -ss 0 
 2144  1919 root     R     3044   5%   4% top -d1 
 2096   951 root     R     3044   5%   3% top -d1 
 1918   899 root     S     2348   4%   3% /usr/sbin/dropbear -r /etc/dropbear/dropbear_rsa_host_key -p 22 
  950   899 root     S     2348   4%   2% /usr/sbin/dropbear -r /etc/dropbear/dropbear_rsa_host_key -p 22 
 2229  1138 root     S     276m 461%   0% ./myapplication -qws 
  913     1 root     S    16628  27%   0% /usr/bin/commserver 
 2292  2289 root     S    15984  26%   0% mplayer -demuxer aac http://gr-relay-3.gaduradio.pl/45 -ss 0 
  951   950 root     S     3044   5%   0% -sh 
 1919  1918 root     S     3044   5%   0% -sh 
 1138  1137 root     S     3044   5%   0% -sh 
  902     1 root     S     2928   5%   0% /sbin/syslogd -n -C64 -m 20 
  860     1 root     S     2868   5%   0% udhcpc -R -n -p /var/run/udhcpc.eth0.pid -i eth0 
  904     1 root     S     2864   5%   0% /sbin/klogd -n 
 1137   899 root     S     2348   4%   0% /usr/sbin/dropbear -r /etc/dropbear/dropbear_rsa_host_key -p 22 
  899     1 root     S     2172   4%   0% /usr/sbin/dropbear -r /etc/dropbear/dropbear_rsa_host_key -p 22 
  909     1 root     S     1904   3%   0% /usr/sbin/bftpd -d 
  929     1 root     S     1828   3%   0% /sbin/getty 115200 ttySAC0 
  306     1 root     S <   1808   3%   0% /sbin/udevd -d 
    1     0 root     S     1572   3%   0% init [5]   
  280     2 root     SWN      0   0%   0% [jffs2_gcd_mtd4]
  135     2 root     SW       0   0%   0% [pdflush]
  136     2 root     SW<      0   0%   0% [kswapd0]
    5     2 root     SW<      0   0%   0% [khelper]
    4     2 root     SW<      0   0%   0% [events/0]
    2     0 root     SW<      0   0%   0% [kthreadd]
    3     2 root     SW<      0   0%   0% [ksoftirqd/0]
  102     2 root     SW<      0   0%   0% [kblockd/0]
  109     2 root     SW<      0   0%   0% [kseriod]
  112     2 root     SW<      0   0%   0% [kmmcd]
  134     2 root     SW       0   0%   0% [pdflush]
  137     2 root     SW<      0   0%   0% [aio/0]
  138     2 root     SW<      0   0%   0% [nfsiod]
  210     2 root     SW<      0   0%   0% [mtdblockd]
  272     2 root     SW<      0   0%   0% [rpciod/0]


```

And now, when it does not start:
```

  PID  PPID USER     STAT   VSZ %MEM %CPU COMMAND
 2096   951 root     S     3044   5%   4% top -d1 
 2293  1919 root     R     3044   5%   4% top -d1 
  950   899 root     S     2348   4%   2% /usr/sbin/dropbear -r /etc/dropbear/dropbear_rsa_host_key -p 22 
 1918   899 root     S     2348   4%   1% /usr/sbin/dropbear -r /etc/dropbear/dropbear_rsa_host_key -p 22 
 2229  1138 root     S     277m 462%   0% ./myapplication -qws 
  913     1 root     S    16628  27%   0% /usr/bin/commserver 
  951   950 root     S     3044   5%   0% -sh 
 1919  1918 root     S     3044   5%   0% -sh 
 1138  1137 root     S     3044   5%   0% -sh 
  902     1 root     S     2928   5%   0% /sbin/syslogd -n -C64 -m 20 
  860     1 root     S     2868   5%   0% udhcpc -R -n -p /var/run/udhcpc.eth0.pid -i eth0 
  904     1 root     S     2864   5%   0% /sbin/klogd -n 
 1137   899 root     S     2348   4%   0% /usr/sbin/dropbear -r /etc/dropbear/dropbear_rsa_host_key -p 22 
  899     1 root     S     2172   4%   0% /usr/sbin/dropbear -r /etc/dropbear/dropbear_rsa_host_key -p 22 
  909     1 root     S     1904   3%   0% /usr/sbin/bftpd -d 
  929     1 root     S     1828   3%   0% /sbin/getty 115200 ttySAC0 
  306     1 root     S <   1808   3%   0% /sbin/udevd -d 
    1     0 root     S     1572   3%   0% init [5]   
  280     2 root     SWN      0   0%   0% [jffs2_gcd_mtd4]
  135     2 root     SW       0   0%   0% [pdflush]
  136     2 root     SW<      0   0%   0% [kswapd0]
    5     2 root     SW<      0   0%   0% [khelper]
    4     2 root     SW<      0   0%   0% [events/0]
    2     0 root     SW<      0   0%   0% [kthreadd]
    3     2 root     SW<      0   0%   0% [ksoftirqd/0]
  102     2 root     SW<      0   0%   0% [kblockd/0]
  109     2 root     SW<      0   0%   0% [kseriod]
  112     2 root     SW<      0   0%   0% [kmmcd]
  134     2 root     SW       0   0%   0% [pdflush]
  137     2 root     SW<      0   0%   0% [aio/0]
  138     2 root     SW<      0   0%   0% [nfsiod]
  210     2 root     SW<      0   0%   0% [mtdblockd]
  272     2 root     SW<      0   0%   0% [rpciod/0]

```

in ps myapplication, in current session, my application has id 2229, so find / -name limits | grep 2229 gives:

```

/proc/2229/task/2229/limits
/proc/2229/task/2232/limits
/proc/2229/task/2236/limits
/proc/2229/task/2237/limits
/proc/2229/task/2238/limits
/proc/2229/task/2239/limits
/proc/2229/task/2240/limits
/proc/2229/task/2241/limits
/proc/2229/task/2242/limits
/proc/2229/task/2243/limits
/proc/2229/task/2244/limits
/proc/2229/task/2245/limits
/proc/2229/task/2246/limits
/proc/2229/task/2247/limits
/proc/2229/task/2251/limits
/proc/2229/task/2252/limits
/proc/2229/task/2253/limits
/proc/2229/task/2254/limits
/proc/2229/task/2255/limits
/proc/2229/task/2256/limits
/proc/2229/task/2257/limits
/proc/2229/task/2258/limits
/proc/2229/task/2259/limits
/proc/2229/task/2260/limits
/proc/2229/task/2261/limits
/proc/2229/task/2262/limits
/proc/2229/task/2263/limits
/proc/2229/limits

```

The multitude (as well as more than 100% VSZ size) of tasks is due to few plug-ins loaded. All of these tasks have the same limits, which are (cat /proc/2229/task/<number>/limits and cat /proc/2229/limits):

```

Limit                     Soft Limit           Hard Limit           Units     
Max cpu time              unlimited            unlimited            ms        
Max file size             unlimited            unlimited            bytes     
Max data size             unlimited            unlimited            bytes     
Max stack size            8388608              unlimited            bytes     
Max core file size        0                    0                    bytes     
Max resident set          unlimited            unlimited            bytes     
Max processes             512                  512                  processes 
Max open files            1024                 1024                 files     
Max locked memory         65536                65536                bytes     
Max address space         unlimited            unlimited            bytes     
Max file locks            unlimited            unlimited            locks     
Max pending signals       512                  512                  signals   
Max msgqueue size         819200               819200               bytes     
Max nice priority         0                    0                    
Max realtime priority     0                    0                    
Max realtime timeout      unlimited            unlimited            us       

```

Hope this information is important and useful for solution. Please, if anyone has some thoughts on that, write them here.

Thank You in advance.

---

