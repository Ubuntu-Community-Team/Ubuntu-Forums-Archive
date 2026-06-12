---
title: "webbrowsers crashing randomly"
date: 2008-09-26
forum: General Help
---

### Post by k0rfain on 2008-09-26
Im sure im not the only one who is having such problems, I did try searching on Google but I did not find any good solutions. I use Epiphany, and it just randomly crashes on me sometimes... mainly when im on a website like youtube or myspace.. so its like if the website is pretty "heavy" then epiphany would just crash. Or sometimes I could be watching a video on youtube and I might want to watch another video so I click another link, it will just freeze up and I would have to end it. Or I could have more then one tab open and it would do the same. I also notice that it freezes for a couple seconds or maybe minutes when a page is loading then it would resume. I also have these problems with firefox (3)? Thanks

---

### Post by Crafty Kisses on 2008-09-26
When the browser is open, go into Terminal and run the following command:
```
top
```
Post the results here on the forum.

---

### Post by k0rfain on 2008-09-26
oops, edit:
```
top - 18:50:43 up 1 day, 12:08,  3 users,  load average: 0.35, 0.99, 0.76
Tasks:  77 total,   2 running,  75 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.6%us,  0.7%sy,  0.0%ni, 82.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    247556k total,   243540k used,     4016k free,     2340k buffers
Swap:   722884k total,   117456k used,   605428k free,    48492k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5424 root      20   0  247m  24m 2684 S 12.7 10.3  54:26.52 Xorg               
 5736 k0rfain   20   0 60156 5400 3440 R  2.7  2.2   0:06.16 xfce4-terminal     
15763 k0rfain   20   0  141m  48m  21m S  1.0 20.1   0:08.09 epiphany-gecko     
    1 root      20   0  2044  180  176 S  0.0  0.1   0:01.22 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:08.20 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.10 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:05.94 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  112 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  151 root      15  -5     0    0    0 S  0.0  0.0   0:18.56 kswapd0            
  192 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1429 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd      

```

---

