---
title: "Install Freezes (9.10) - Checking/Detecting File System"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by XtremeSki2001 on 2009-11-01
Hi All,

Finally getting around to installing 9.10.  I used to have Edgy installed, went back to XP - looking forward to seeing the progress Linux has made since last time I tried it!

Anyways - I was installing from the ISO via CDROM and during the install process it freezes during the checking/detecting (not sure which word it actually uses) file system.  

After freezing ... the screen blinks 7 times, stops for a few moments and blinks 7 times and it does this until I have to hard reboot the system.

Tried booting into the Live CD portion and I come into the same problem.

Any ideas what the problem is?  I haven't come across this in my Google and Forum searching efforts.

Thanks in advance!

---

### Post by XtremeSki2001 on 2009-11-02
Really?  No one has a suggestion?  

Seems like there are quite a few problems with this install and not many are resolving their issues.

Is the message to use 9.04 instead?

---

### Post by bhospadaruk on 2009-11-03
Same problem here

---

### Post by techweenie1 on 2009-11-06
Having the same problem with Ubuntu PPC

---

### Post by dhavalbbhatt on 2009-11-06
Have you guys tried installing using the alternate CD for 9.10? I ran into the same issue trying to install using the desktop installation CD, however, I could install using the alternate CD just fine.

---

### Post by bigsuccess on 2009-11-26
This is occurring to me also while trying to install. I have tried 32 bit and 64 bit. I've given up on that for a while and I'm going to try a few other things to work around and report back.


In the meantime I applied today's updates on my work desktop (64 bit karmic) and instead of going into the desktop on reboot it all of a sudden has the same issue.

The bootup was receiving messages from virtual box and then it dumped me to a text login and started blinking.

The update put me from kernel 2.6.31-14 to 2.6.31-15, when I select the older one from grub I am able to login fine.

I'm not sure if they're 2 separate issues but certainly the same symptom so I thought I'd add it here if it helps anyone.

Interestingly also the difference on my install computer between 32 and 64bit was where they failed and started blinking (64 bit on "detecting file system 0%) and the 32bit somewhere else.. neither seemed related to what it was actually showing it was doing to me...

---

### Post by bigsuccess on 2009-11-28
Alternate cd install worked for me (as in the install works) but even though it finished successfully i still get dumped to tty during bootup and the blinking screen returns... so basically i cant use the newly installed OS.

hunt continues

---

### Post by bigsuccess on 2009-11-28
I decided it was the video drivers so I used recovery mode with net support to install nvidia drivers.

GDM loaded and I'm now in the GUI - shame my monitor is not detected and the highest res is 640x480...still i think -this- problem was solved with video card drivers.

cheers!

---

