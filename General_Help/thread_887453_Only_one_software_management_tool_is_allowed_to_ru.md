---
title: "Only one software management tool is allowed to run at the same time"
date: 2008-08-12
forum: General Help
---

### Post by Achilles124 on 2008-08-12
Hello all,

This is the message I get: Only one software management tool is allowed to run at the same time. 

I have typed: [COLOR="Blue"]sudo dpkg --configure -a[/COLOR]  and this is what I get:

Instellen van language-support-fr (1:7.04+20070209) ...
Generating locales...
  fr_BE.UTF-8... 

It hangs and I don't know where I can find it in my system monitor nor do I know how to close it.

---

### Post by null byte on 2008-08-12
Press Ctrl + C in the terminal tab where you put that command :|

---

### Post by Achilles124 on 2008-08-12
that doesn't work

---

### Post by SunnyRabbiera on 2008-08-12
Well its possible something is hanging, did you try a logout or restart?

---

### Post by Achilles124 on 2008-08-12
yes, i restarted... but that didn't work either.

---

### Post by Achilles124 on 2008-08-12
I restarted again,,, it is still busy...
Where can I found it in the system monitor?

---

### Post by null byte on 2008-08-12
Processes - Press the **% CPU** button so the arrow is up.

Tell us the name of the process eating most of the CPU.

---

### Post by Achilles124 on 2008-08-12
This is weird,,,the program that uses the most CPU is the terminal (2percent). The rest is sleeping. But when I watch it graphically (resources), the two cpu's are going like crazy.

---

### Post by Achilles124 on 2008-08-12
That is weird, the progam that demands the most CPU power is the terminal (2%) but when I watch the CPU in resources, I can see that they work like crazy.

---

### Post by Achilles124 on 2008-08-12
This is the result after using the command top:
 6581 root      25   0 55176  52m  900 R   99  2.6  11:45.02 localedef          
 5566 root      15   0  295m  15m 7288 S    8  0.7   1:19.82 Xorg               
 6527 ecmpeek   39  19 73576  24m 9.9m S    2  1.2   0:13.31 beagled-helper     
 6711 ecmpeek   15   0 36052  20m  14m S    1  1.0   0:21.91 gnome-system-mo    
 6109 ecmpeek   22   7 78328  27m 9548 S    1  1.3   0:09.17 beagled            
    1 root      18   0  2948 1856  532 S    0  0.1   0:01.18 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.05 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0 


Localedef uses 99% cpu... close it????

---

### Post by null byte on 2008-08-12
Kill it!

---

### Post by Achilles124 on 2008-08-12
lol, what should be the commandline???

---

### Post by null byte on 2008-08-12
> **Achilles124 said:**
> lol, what should be the commandline???
Right click localedef, Kill process.

or pkill localedef

---

### Post by Achilles124 on 2008-08-12
pkill localedef doenst work.
and I cant find localedef in my system monitor....

---

### Post by null byte on 2008-08-12
Kill the terminal then.

---

### Post by Achilles124 on 2008-08-12
Can I use the PID ... it says PID 6581

---

### Post by null byte on 2008-08-12
sudo kill -9 6581

---

### Post by Achilles124 on 2008-08-12
Tried that,,,, it doesnt work...

---

### Post by null byte on 2008-08-12
Some guy solved it by hard resetting (pressing the Reset button).

---

### Post by Achilles124 on 2008-08-12
Yes, that worked. Thank you null-byte. I have tried it before but it worked now. Thank you again.

---

### Post by null byte on 2008-08-12
> **Achilles124 said:**
> Yes, that worked. Thank you null-byte. I have tried it before but it worked now. Thank you again.
No problem, this was a confusing problem, at least for me :)

---

### Post by Achilles124 on 2008-08-12
The problem has returned,,, i am at a loss. Worked a lot with microsoft XP in the past but never have I experienced something like this.

---

### Post by null byte on 2008-08-12
:| 

Did you execute the same command again?

Paste the output of **top** here.

---

### Post by Achilles124 on 2008-08-12
localedef has 7881 as ID now., 100% CPU. And yes, I have tried all kind of things.


 7881 root      25   0 55180  52m  900 R  100  2.6  11:14.54 
localedef          

 5559 root      15   0  298m  18m 6548 S    1  0.9   1:51.65 Xorg               

    1 root      16   0  2952 1856  532 S    0  0.1   0:01.19 init               

    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           

    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        

    4 root      34  19     0    0    0 S    0  0.0   0:00.15 ksoftirqd/0        

    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         

    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        

    7 root      34  19     0    0    0 S    0  0.0   0:00.14 ksoftirqd/1        

    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         

    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           

   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           

   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            

   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          

   32 root      10  -5     0    0    0 S    0  0.0   0:00.01 kblockd/1          

   33 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpid             

   34 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify

---

### Post by null byte on 2008-08-12
Just found this link, the dude has the same problem as you, try it:

[https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)

---

### Post by Elfy on 2008-08-12
It was bit of an issue a short while ago - this appears to have worked 

[http://ubuntuforums.org/showpost.php?p=5558932&postcount=15](http://ubuntuforums.org/showpost.php?p=5558932&postcount=15)

---

### Post by Achilles124 on 2008-08-12
I am reading it. But there the problem arises when upgrading. One more question. Can the program Kleansweep maybe help? That is removing obsolete files before the problem arises again after booting?

---

### Post by Achilles124 on 2008-08-12
Followed the instructions of Alecz20 on the page:
" I just want to mention a possible important aspect:
This bug is not limited to OS Upgrades!

I tried adding another language via System->Administration->Language Support, and got the exact same issue: hang when generating locales.

The "work around" that made my machine able to install stuff was:
1) reboot (the only way to kill locale-gen)
2) sudo rm /usr/bin/localedef (deletes all localization)
3) sudo dpkg --configure -a ("fixes" the package manager so u can install stuff)"

It works. I can use Synaptic manager again.

---

