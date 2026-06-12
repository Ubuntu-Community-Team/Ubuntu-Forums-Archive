---
title: "New to Ubuntu/Linux"
date: 2008-10-28
forum: General Help
---

### Post by smithers102 on 2008-10-28
Hey folks, I'm a complete newb when it comes to Linux,  I successfully installed Ubuntu, but it boots to the kernel.  My question would be how do you load the desktop from the kernel and is there any way i could bypass the kernel on start up?

---

### Post by Titan8990 on 2008-10-28
Did you install the server version by mistake?

The kernel is the low level of the OS. It basically IS the OS. Everything more or less runs on top of the kernel. I believe you may have "kernel" confused with "shell".

---

### Post by smithers102 on 2008-10-28
I'm almost positive I installed the desktop version 8.04.1 is exactly what i installed.  I do have kernel mixed up with shell.  My bad.

I'll post pictures of the screens that come up throughout my boot up.


Here's the boot screen, I always boot the first one.

[ATTACH]89974[/ATTACH]


Here's the loading screen, which seems to take about 5 - 6 minutes, very long I thought.

[ATTACH]89975[/ATTACH]


Finally here's the screen it goes too once It's done loading.  This is where I'm stuck.

[ATTACH]89976[/ATTACH]

---

### Post by Titan8990 on 2008-10-28
So after you boot you get something like this:


YOURUSERNAME@YOURCOMPUTERNAME:~$


over top of a black screen?

---

### Post by smithers102 on 2008-10-28
See updated post above    / \
                           |
                           |
                           |
                           |

---

### Post by jespdj on 2008-10-28
It does not "boot to the kernel" - you are dropped into a BusyBox shell for some reason. I had this happen once because the CD that I was booting Ubuntu from had an error on it.

Try booting from the Ubuntu CD and select the option "Check CD for defects", and see if it comes up with any errors. If it does, then re-burn the CD (and reinstall Ubuntu from the new CD).

What hardware do you have (processor, amount of memory, video card, and other hardware)? What CD image did you download; the normal Ubuntu Desktop version, or the Server or alternate install version? Note that Ubuntu Server doesn't come with any GUI desktop out-of-the-box.

---

### Post by Titan8990 on 2008-10-28
Thats actually not even the real shell but a failsafe one. I have only seen that happen once and I was booting a live CD on a computer that it was not compatible with.

I don't know much about the busybox shell...

Hopefully another user will come by who does.

---

### Post by smithers102 on 2008-10-28
Heres my hardware

MOBO:ASUS Maximus II Formula
CPU:Intel Core 2 Quad Q9550 2.83 GHz
RAM:Corsair XMS2 Dominator PC8500 4GB
GPU:GEFORCE GTX 280 SSC Edition
Primary HDD:Seagate Barracuda 250GB (This is what i'm dual booting windows/linux on, my 1000gig isn't plugged in at the moment)

I downloaded the desktop version for standard personal computer.

---

### Post by Titan8990 on 2008-10-28
Ehh, that hardware is very new. Typically, Linux runs best on hardware that is about a year old.

Also, I have found that those high end Asus boards are hit or miss on whether or not they will be pulled off shelves due to being plagued with issues....

---

### Post by smithers102 on 2008-10-28
> **Titan8990 said:**
> Also, I have found that those high end Asus boards are hit or miss on whether or not they will be pulled off shelves due to being plagued with issues....

Damn i hope not, that thing is the center piece of my new rig.  My disk didn't have any errors on it when checked also, so perhaps it is a hardware issue.  I'm gonna be disappointed if I'm unable to run Ubuntu because my rig is just too new.

---

### Post by tuskenraider on 2008-10-28
i got the busybox issue once as well.. and im not cutting edge.  I ended up having to use the cd i burned as a coaster... and i trashed the iso..   go download a new iso from the web... reburn and reinstall  Ill bet the iso crapped out on you and thats your issue.  just my 2cents


tusken

p.s dont worry... we all have minor issues.. once you get ubuntu up and running youll love it... also  go to 

down.codeweavers.com and request a serial... you never know you may need the software some point in time.. oh and its FREE today 10/28/08

---

### Post by Portmanteaufu on 2008-10-28
I'm with TuskenRaider on this, I suspect you just got a wonky copy of the .iso somehow.

However, if it's actually the case that your hardware is just too new and awesome for Hardy, it's possible that installing Intrepid Ibex (either the RC or the final version in a few days) to take advantage of the added hardware support in the newest kernel (2.6.27) would be beneficial.

---

### Post by smithers102 on 2008-10-29
Well, i downloaded a new .iso for the desktop install and it didn't work yet again. Sigh, i give up.

---

### Post by Titan8990 on 2008-10-29
I recommend giving another distro a try.

---

### Post by Sef on 2008-10-29
Try the alternate cd.  Sometimes it can work when the Live CD does not.  Just click on the box below the green arrow on the get Ubuntu page.

---

