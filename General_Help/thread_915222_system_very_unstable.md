---
title: "system very unstable"
date: 2008-09-09
forum: General Help
---

### Post by richardy on 2008-09-09
Hi recently installed Xubuntu 8.04 on to an ASUS desktop and it seems to be very unstable - simply locks up for no reason then i have to power down and restart - very annoying. The sort of things that cause the lock ups seems to fairly trivial, resizing a window, or even just moving the mouse can do it. The sort of apps that have been running at the time are fairly standard -  eg Firefox. The only common thread is that it usually works fine for a while (couple of hours) before it locks up. I have actually had to go back to using windows till i can get the problem sorted. I have already had to reinstall once after using the upgrade manager left the system unusable. I previously had gutsy gibbon on this machine and it worked absolutely brilliantly - i should never have dumped it.

I hope someone can help with this, i dont really want to have to go back to using windows.

Cheers.

---

### Post by LowSky on 2008-09-09
did you do a clean install of Hardy? or just an upgrade?

Whats are the systems specs and what applications are you running on a normal basis.

Could you post the results of following command form xubutu

```
top
```

you might need to ht ctrl+c to get it to stop reloading

---

### Post by richardy on 2008-09-09
Also.........
I had noticed that the graphics was very slow to update. Particularly if having to many graphics intensive operations going at once eg watching a you tube video while have a couple of other web pages open at the same time. However this was no problem for gutsy. I have hear that there are possible problems with the latest version of firefox - could this be the problem.

Cheers.

---

### Post by richardy on 2008-09-09
Hi lowsky,
Thanks for replying. Yes was a clean install of Hardy. The sort of apps that same to cause teh problem are mainly firefox - see other reply. Specs are 40g HD, 2.6g intel processsor, i'll send the other stuff when i fire it up.

Not currently in Xubuntu as it got to annoying so will fire up and run the command nad let you know.

Cheers.

---

### Post by LowSky on 2008-09-09
you can always downgrade to firefox 2 just remember to delete the .firefox folder before installing FF2
I noticed that Hardy and FF3 seems more buggy than Gusty and FF2, at least on Ubuntu compared to WinXP.
I guess its why Ubuntu released 8.04.1 a few months back and FF3.1 is being release very shortly.

You can always try a different browser or other apps for common things, like epiphany or opera

---

### Post by richardy on 2008-09-09
Hi LowSky,
Yes i will try replacing firefox and see what happens. Below is output from the top command. Thanks for your help.

top - 09:46:51 up 7 min,  2 users,  load average: 0.12, 0.45, 0.30
Tasks: 105 total,   1 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us,  0.2%sy,  0.0%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    450584k total,   391424k used,    59160k free,    18356k buffers
Swap:   827336k total,        0k used,   827336k free,   222980k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5298 root      20   0 95072  20m 7120 S    1  4.6   0:15.50 Xorg               
 1341 root      15  -5     0    0    0 S    1  0.0   0:00.02 ata/0              
 5840 richard   20   0 61048  18m 9320 S    1  4.1   0:01.44 xfce4-terminal     
 5905 richard   20   0  2308 1104  852 R    1  0.2   0:00.14 top                
    1 root      20   0  2844 1688  544 S    0  0.4   0:02.34 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.02 khelper            
   47 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0          
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
richard@Zen:~$ top

top - 09:47:27 up 8 min,  2 users,  load average: 0.07, 0.39, 0.28
Tasks: 105 total,   1 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.1%us,  0.7%sy,  0.0%ni, 97.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    450584k total,   390556k used,    60028k free,    18356k buffers
Swap:   827336k total,        0k used,   827336k free,   222980k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5298 root      20   0 94184  19m 7120 S    2  4.4   0:15.78 Xorg               
 5680 richard   20   0  142m  48m  19m S    2 11.1   0:15.80 firefox            
    1 root      20   0  2844 1688  544 S    0  0.4   0:02.34 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.02 khelper            
   47 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0          
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
richard@Zen:~$

---

### Post by nikgare on 2008-09-10
You could try disabling desktop effects, they may be aausing you problems.

---

### Post by richardy on 2008-09-10
Hi nicgare,
Thanks for the reply and please excuse my ignorance but how would i find "desktop effects" i hada look thru all the xubuntu settings and couldnt find any referencing to desktop effects.

Also, could the problems i am having be related the graphics setup in xorg.conf which seems to be a very generic one since the graphics have always been very slow to update.

Cheers.

---

### Post by Mongo5000 on 2008-09-11
I recently upgraded to hardy and also noticied very bad performance.

Found out that firefox 3 was the culpit.  Even though top wasn't showing it using a lot of resources, spent the last 2 hours using Opera and everything has been smooth as silk.

Just thought I would mention it

---

