---
title: "Problems after update from ubuntu 8.10-&gt;9.04"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by Abdujaparov on 2009-05-14
Hi,
I updated ubuntu to 9.04 but now I have problems. The systems seems to be unstable.
In particular I see the hd works a lot many times when I opened only firefox. When I try to close the session or restart the computer or shut down the screen becomes black and the computer is blocked without end the operation.
When I open amule, after few minutes the system is blocked.
When I open virtualbox and the I try to shut down the os guest ubuntu is blocked. Why? How can I solve?


I executed top and this is the result:

```

top - 08:03:33 up 10 min,  2 users,  load average: 1.49, 1.40, 0.86
Tasks: 155 total,   2 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.6%us,  9.5%sy,  0.2%ni, 31.2%id, 34.5%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:   3998964k total,  1351168k used,  2647796k free,   232420k buffers
Swap:  4345540k total,        0k used,  4345540k free,   452576k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4460 angelo    20   0  246m  56m  16m R   29  1.4   1:57.01 npviewer.bin       
13641 angelo    20   0  187m  15m  10m S   11  0.4   0:01.19 gnome-terminal     
 3519 root      20   0  203m  46m  21m S    9  1.2   0:39.50 Xorg               
 3959 angelo    20   0  299m 6240 4492 S    3  0.2   0:11.78 pulseaudio         
13278 root      30  10  4076  920  588 D    3  0.0   0:01.82 updatedb.mlocat    
 4400 angelo    20   0  620m 186m  28m S    2  4.8   1:18.10 firefox            
 4106 angelo    20   0  148m   9m 7636 S    2  0.3   0:01.96 gdl_box            
 4059 angelo    20   0  271m  44m  17m S    2  1.1   0:07.92 compiz.real        
 4337 angelo    20   0  158m 3652 1792 S    2  0.1   0:02.31 gnome-screensav    
 4062 angelo    20   0  438m  22m  15m S    0  0.6   0:01.03 nautilus           
13660 angelo    20   0 19116 1348  988 R    0  0.0   0:00.10 top                
    1 root      20   0  5244 2036  632 S    0  0.1   0:01.02 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        

```

Thanks, bye bye.

---

### Post by Peter09 on 2009-05-14
This thread has a couple of options for you

[http://www.linuxquestions.org/questions/linux-software-2/npviewer.bin-eating-my-cpu.-help-711097/](http://www.linuxquestions.org/questions/linux-software-2/npviewer.bin-eating-my-cpu.-help-711097/)

---

