---
title: "Help with usb install"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by Professor Groove on 2009-04-05
Hello, I am new to Ubuntu. I downloaded the Ubuntu 8.10 ISO and used unetbootin to put it on a usb drive. I boot from usb in bios and a black screen comes up that says "Ubuntu" and there is a loading bar. After the bar loads the screen goes white and nothing more happens until I turn off the machine.

Any suggestions?

---

### Post by TheFuzz4 on 2009-04-06
I've had this happen before with Kubuntu for some weird reason.  When the screen goes white try using a CTRL + ALT + Backspace (This will restart your X Server) and see if that helps clear up the problem.

---

### Post by tommcd on 2009-04-06
Try the Ubuntu 8.10 32 bit alternate install CD if you can't get the live CD to work. The alternate install CD is a text based installer. It is pretty easy to follow. 

And welcome to the Ubuntu forums!

---

### Post by ProfessorGroove on 2009-04-06
Thanks Tom; I'm trying that now. I'll post back here with results.

---

### Post by SR_ELPIRATA on 2009-04-06
It would also help the system specs you have. Far as I know, Ubuntu 8.10 requires 384MB RAM, so if u have less....

I downloaded, aside of Ubuntu, also Xubuntu, for those machines in which gives me problems. I also have a gOS CD, the one that used Enlightment, and many times, PCs with low specs run both of them well (xubuntu and gos).

ELP

---

### Post by ProfessorGroove on 2009-04-07
System specs: 

Thermaltake Armor Series Full ATX case
Asus Rampage Formula mobo
Q6600 Core 2 Quad @ 2.4 GHTZ
4 GB munchkin ram DDR2 800
HIS ICE-Q Radeon 4870 graphics card (1GB DDR5)
Supreme FXII sound card (comes with mobo)
1TB 7200RPM Western Digital HD
850W PSU

---

### Post by ProfessorGroove on 2009-04-10
Okay here's the deal. CTRL+ALT+BACKSPACE doesn't work the screen goes black for a moment and then goes back to being white. I tried installing using the text based 32b ISO and it gets stuck at starting up partitioner at 40% every time. I tried the "Install inside windows option" on the live cd (even though I originally wanted to install and boot from an IPOD being used as an external HD). I installed rebooted chose ubuntu as the OS and I get the same white screen problem. I can hear things going on when I hit buttons on the keyboard and it sounds like the OS is running and that it is a video only problem. I did some googling and found people with my video card commonly have this problem and the only way to fix it is to start ubuntu with the safe video option enabled and then after I properly configure my video card drivers I can change the resolution back to what I want. My question has therefore changed. How do I change ubuntu to boot in safe video mode?

---

### Post by tommcd on 2009-04-10
> **ProfessorGroove said:**
> ... I originally wanted to install and boot from an IPOD being used as an external HD).
Are you currently trying to install to the I-pod or the hard drive on your computer? I have no experience with installing Ubuntu onto an I-pod. I would suggest installing Ubuntu onto your computer's hard drive or a second hard drive if you have one.
> **ProfessorGroove said:**
>  
My question has therefore changed. How do I change ubuntu to boot in safe video mode?
This applies to the live CD. When you boot the live CD there is an option to boot in safe graphics mode. The alternate install CD is text based, so it does not have, or need, this option.
Does you screen still go black / white with the alternate CD?

---

### Post by ProfessorGroove on 2009-04-10
No, it doesn't go white with the alternate but it gets stuck at 40% of "loading partitioner" screen. Also I don't see why I woulnd't be able to install to an IPOD it's no different than an external HD no?

Also I'm not booting from the live cd anymore I choose the install in windows as if this were an application thing  so it is installed but when it loads up it gets white screened

[IMG]http://img23.imageshack.us/img23/9606/97907642.png[/IMG]

[IMG]http://img7.imageshack.us/img7/22/97328471.png[/IMG]

---

### Post by tommcd on 2009-04-11
> **ProfessorGroove said:**
> Also I don't see why I woulnd't be able to install to an IPOD it's no different than an external HD no?
It should be. I have no experience with the Ipod though; so I am not sure if I can help with that.
> **ProfessorGroove said:**
> 
Also I'm not booting from the live cd anymore I choose the install in windows as if this were an application thing  so it is installed but when it loads up it gets white screened

Sorry, but I have no experience with Wubi either.  Remember that according to Wubi's developer, Wubi is only meant for trying out Ubuntu. It is not meant for a long term install.
There is a Wubi forum here. Perhaps start a new thread about the graphics problem in the Wubi section.

---

