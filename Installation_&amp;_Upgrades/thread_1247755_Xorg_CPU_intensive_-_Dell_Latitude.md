---
title: "Xorg CPU intensive - Dell Latitude"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by hrafninn on 2009-08-23
I just installed Ubuntu 9.04 (dual boot with Windows XP) on a Dell Latitude D600.

I notice that Firefox is very slow and that Xorg is very CPU intensive.  Running top, I get something like:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2591 root      20   0  167m  63m 8128 R 65.8  4.2   0:43.92 Xorg               
 3504 hrafn     20   0  183m  75m  22m R 32.6  5.0   0:26.61 firefox            
 3466 hrafn     20   0 32972  14m 9524 R  0.3  0.9   0:00.60 gnome-terminal     
 3581 hrafn     20   0  2448 1180  916 R  0.3  0.1   0:00.01 top                
    1 root      20   0  3084 1888  564 S  0.0  0.1   0:01.44 init  

Judging by the Ubuntu forum, this is a known problem and presumably has to do with my ATI card.

lspci | grep VGA
gives
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

I actually followed the procedure described in [http://audibadboy.blogspot.com/2009/05/ubuntu-904-jaunty-and-high-cpu-on-xorg.html](http://audibadboy.blogspot.com/2009/05/ubuntu-904-jaunty-and-high-cpu-on-xorg.html), but unfortunately without any luck.        

My xorg.conf looks like this:

Section "Device"
	Identifier "ATI Radeon R250"
	Driver "ati"
	BusID "PCI:1:0:0"
	Option "Accel" 
	Option "AccelMethod" "XAA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI Radeon R250"
EndSection

Can anyone help?

---

### Post by tomasrey88 on 2009-08-23
How much RAM do you have? I have a Dell Latitude and it was running unbearably slow with Xubuntu 9.04. Lagging graphics, etc. That was when I had 128 MB RAM. Then, I increased it to 256 MB RAM and it worked a bit faster, it was bearable, but still kinda slow. So, then I used a smaller footprint program than Firefox (Seamonkey in Puppy Linux) and it works just as fast as a new computer, now. You might also want to tweak xorg to work with less colors (I'm using 16 bit colors). Even without going to a different Linux distro, I think you'll do fine if you'll use xorg with less colors and run Seamonkey instead of Firefox as that would put less demand on the system.

My System: 300 mHz Dell Latitude CPi, 256 MB RAM, 6 GB HD.

Shameless self-plug:
I've helped you. Now I invite you to please help me with my problem. I don't know how to format a USB Flash with read/write permissions: 
[http://ubuntuforums.org/showthread.php?t=1247804](http://ubuntuforums.org/showthread.php?t=1247804)

Enjoy,
:guitar:

---

### Post by hrafninn on 2009-08-23
I have 1,5 GB of RAM which I assume is large enough to make Ubuntu run very well on this machine.  My disk is 40 GB, partitioned according to:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        1831    14651280    7  HPFS/NTFS
/dev/sda3            1832        2196     2931862+   5  Extended
/dev/sda4            2197        4864    21430710   83  Linux
/dev/sda5            1832        2196     2931831   82  Linux swap / Solaris

---

### Post by tomasrey88 on 2009-08-23
Seems like your computer has plenty of RAM, so I have no idea what's wrong. Is the graphics smooth or lagging? If graphics are smooth, I wouldn't worry about it.

---

### Post by hrafninn on 2009-08-23
I just installed the newest version (9.64) of the Opera browser and at first sight it seems to perform much better than Firefox.  Xorg CPU usage is still high (is it?) but much lower than when using Firefox:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2591 root      20   0  166m  63m 8936 S 22.5  4.2  20:39.98 Xorg               
25485 hrafn     20   0  128m  62m  15m S  3.3  4.1   0:18.86 opera              
 3324 hrafn     20   0 27488  18m 6740 S  1.0  1.2   0:33.28 compiz.real        
 3466 hrafn     20   0 33852  15m 9740 S  0.7  1.0   0:23.50 gnome-terminal     
 2617 root      20   0 16304 2808 2300 S  0.3  0.2   0:09.27 NetworkManager     
25475 hrafn     20   0  2448 1180  916 R  0.3  0.1   0:01.12 top

---

### Post by hrafninn on 2009-08-24
I'm afraid I announced victory too early!  I was running Opera and suddenly the computer became extremely slow (keyboard input appeared on the screen in 1-2 seconds!).

Top gives:
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2596 root      20   0  187m  84m 8836 R 78.1  5.6   9:22.27 Xorg               
11993 hrafn     20   0  110m  51m  15m S  8.5  3.4   1:53.93 opera              
14006 root      20   0  2064  508  436 R  3.3  0.0   0:00.10 hal-system-smbi    
 4547 hrafn     20   0 32588  13m 9360 S  2.3  0.9   0:03.35 gnome-terminal     
 3315 hrafn     20   0 27356  18m 6728 S  1.6  1.2   0:17.50 compiz.real        
13959 hrafn     20   0  2448 1184  916 R  1.6  0.1   0:00.90 top 

Notice 78.1% CPU by Xorg!  Hence, the problem does not seem to be only related to Firefox.  It must be Xorg and the ATI card, or what?

I have another LapTop, Dell Precision M4300 (2GB RAM) with a NVidia card. Ubuntu runs very smoothly on that one.

Any suggestions regarding what to try?

---

### Post by hrafninn on 2009-08-24
Just noticed a new thread: [http://ubuntuforums.org/showthread.php?t=1247447](http://ubuntuforums.org/showthread.php?t=1247447)

Do you think my problem is similar in nature as discussed there, meaning I might have to buy another graphics card?

---

### Post by Mark Phelps on 2009-08-25
> **hrafninn said:**
> ... meaning I might have to buy another graphics card?
While the open source drivers ARE getting better all the time, getting a newer card will enable you to use restricted drivers and get either faster frame rates, less CPU usage, or both.

Also, while I used to be a fan of ATI, their acquisition by AMD, and subsequent dropping of support for lots of legacy cards, has lead me to suggest folks consider other suppliers for future cards.

ATI is now jumping into DX-11 cards, ostensibly to get a jump on Windows 7, and while Nividia is doing something similar, I've not seen nearly the number of Nvidia-driver related posts in this forums as ATI-driver related posts.  So, it's probably a good time to leave ATI behind and switch to Nvidia.

---

### Post by dE_logics on 2009-08-25
> Judging by the Ubuntu forum, this is a known problem and presumably has to do with my ATI card.

You are right...ATI + Linux = disaster.

The same situation is with me, while doing nothing both the CPUs usage fluctuates around 8 - 40%.

Try the proprietary drivers...I think you have to live with it, like I am.

But atleast it's better than windoze....

[QUOTE=tomasrey88]I don't know how to format a USB Flash with read/write permissions: [/QUOTE]

Download GParted from the repos...select your device, set the file system, and you're done.

---

### Post by dE_logics on 2009-08-25
[QUOTE=Mark Phelps]While the open source drivers ARE getting better all the time[/QUOTE]

Man...I'm tired waiting for the new drivers!!...last news was in April...:(

Nvidia is very good...very good support for Linux...it's even gets compiled specifically for your OS.

---

