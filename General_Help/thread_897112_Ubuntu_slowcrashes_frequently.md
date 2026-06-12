---
title: "Ubuntu slow/crashes frequently"
date: 2008-08-21
forum: General Help
---

### Post by Zanian on 2008-08-21
Hey,
I've been having this problem since I started using Ubuntu a couple of months ago.  When I'm running a few programs at once ( Firefox, Amarok, etc... Nothing too high maintenance) Xorg starts to drain my CPU.  After a while everything will freeze up.  Soft resets won't even work and I must do a hard reset.  Nothing significant triggers it.  It usually only happens when I have 2-3 things open or so, but happens anytime.  Thanks in advance.

---

### Post by EMCGFX on 2008-08-21
What version of Ubuntu are you running ?

---

### Post by Zanian on 2008-08-21
8.04

---

### Post by cybrsaylr on 2008-08-22
This 'crashing' seems to be a bug in 8.04.
It usually happens to me after waking up my PC after it's been idle for a few hours. Everything runs OK when first booting up but after waking it up is when 8.04 locks up on me, usually after using a few minutes, forcing a hard restart.

---

### Post by Zanian on 2008-08-25
bump...

---

### Post by ntbutler on 2008-08-25
I am having the same problem, but it was happening to me when i have been watching videos. I think it does have something to do with the sleep function of the power manager, but in all honesty i haven't looked into it fully yet.

You could try for the time being switching off all hibernating-type things (screensaver, system hibernate etc) and see if that works, but yeah, not sure...

Otherwise, do what i am doing and continue combing the forums for any help...

---

### Post by Starks1990 on 2008-08-26
Yea, im having the same problem. When i boot ubuntu up everything is fine then about 8-10 mins later, it freezes. ive tried a few things, but nothings halped me out.

---

### Post by jigsaws on 2008-08-26
Hello

Try to turn off desktop effects.
Try to change the console (alt+ctrl+f1) after it "hangs".
Try to change runlevel to 3 and check if it also hangs - to be sure it's X related problem.

---

### Post by Zanian on 2008-08-26
I turned off desktop effects and I'll see if everything goes well.  For now it's been fine.
Thanks

---

### Post by Zanian on 2008-08-29
Nevermind.  Still drudges through.  When i signed in on tty1, however, it killed x.  I don't know if this sheds some light on the situation.  When I went back though, it was still hanging.

---

### Post by Crafty Kisses on 2008-08-29
Post the results of this command > top

---

### Post by sidewinder46 on 2008-08-29
system info: cpu, ram, video card, etc..pls

---

### Post by Zanian on 2008-08-31
top - 14:21:54 up  1:11,  4 users,  load average: 13.86, 18.83, 17.92
Tasks: 130 total,   3 running, 126 sleeping,   0 stopped,   1 zombie
Cpu(s): 12.7%us,  4.0%sy,  0.0%ni,  0.0%id, 83.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    515580k total,   510200k used,     5380k free,     1352k buffers
Swap:        0k total,        0k used,        0k free,    72352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5640 root      20   0  246m  71m 2148 S  6.3 14.1   4:48.24 Xorg               
 6186 zander    20   0  144m  32m 5048 S  5.3  6.5   1:33.00 amarokapp          
 7418 root      20   0 50340  18m 2180 S  1.3  3.7   0:12.06 synaptic           
 6166 zander    20   0  190m  81m 3944 D  1.0 16.2   1:59.77 firefox            
  162 root      15  -5     0    0    0 D  0.7  0.0   0:10.22 kswapd0            
 6279 zander    20   0 77036  14m 2588 R  0.7  2.8   0:10.28 gnome-terminal     
 7436 zander    20   0 48180  12m 2352 S  0.7  2.4   0:03.82 gnome-settings-    
 7437 zander    20   0 28452  12m 6672 D  0.7  2.4   0:03.14 gnome-panel        
 7489 root      20   0 15560  12m  736 D  0.7  2.5   0:00.28 dpkg               
    1 root      20   0  2844 1208   64 S  0.0  0.2   0:01.16 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:02.74 kblockd/0          

This was while it was hanging, after about 2 hours of hanging I managed to post this.  I hate to ask this, but I can't figure out how to find my specs (I'm rather new to Ubuntu).  I know lshw posts a large list, but it doesn't provide3 much info for my motherboard, for example.

---

### Post by Zanian on 2008-09-05
bump

---

### Post by Zanian on 2008-09-29
bump...

---

