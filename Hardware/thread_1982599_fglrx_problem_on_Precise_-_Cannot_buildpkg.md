---
title: "fglrx problem on Precise - Cannot buildpkg"
date: 2012-05-18
forum: Hardware
---

### Post by MrMister007 on 2012-05-18
Hi Everyone,

I tried posting this in the beginner section, but got no response. Thought I would try here.

I'm having a problem generating the Ubuntu/precise package from the new 12.4 proprietary ATI driver. I was attempting to follow the guide [[COLOR="Red"]here[/COLOR]]("http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-drivers-in-12-04-lts") when it happened, and I don't know what to do.

Here's a screenshot of what I get:
[IMG]http://i.imgur.com/ZMFlP.png[/IMG]

I'm running a 64-bit HP Envy and Ubuntu Precise in case it was unclear. I can't seem to update my about me due to that 50 post rule. 

Thanks in advance, guys!

---

### Post by QIII on 2012-05-18
May I ask why you are going to that trouble?

There is a much, much simpler way to install the driver if you have problems with the graphical installer.

---

### Post by MrMister007 on 2012-05-18
> **QIII said:**
> May I ask why you are going to that trouble?

There is a much, much simpler way to install the driver if you have problems with the graphical installer.
I was following the guide that I linked to reinstall the fglrx driver, but the bigger reason is that I'm trying to get vgaswitcheroo to work with my hybrid graphics. Would it be okay to install without creating the specific package for precise?

---

### Post by QIII on 2012-05-18
The ATI 12.4 driver already exists in the Precise repo.  Did you have trouble installing it with the gui tool?

---

### Post by MrMister007 on 2012-05-18
Do you mean via synaptic or downloaded from ATI? I tried the latter but it repeatedly tells me that a previous installation is detected. I've tried to purge fglrx, but still, the same message appears.

---

### Post by QIII on 2012-05-18
Follow the instructions in my post in this thread:

[http://ubuntuforums.org/showthread.php?t=1967047&highlight=qiii+fglrx](http://ubuntuforums.org/showthread.php?t=1967047&highlight=qiii+fglrx)

---

### Post by MrMister007 on 2012-05-18
Alright thanks, I'll check it out. Right now, gotta figure out why my network is downloading at 30 KB/s...:confused:

---

### Post by QIII on 2012-05-18
Mine, too.  Something wrong with the US mirror, I think.

---

### Post by MrMister007 on 2012-05-18
Oh, good...I'm not going crazy.

---

### Post by MrMister007 on 2012-05-21
Hey QIII, sorry for the delay, but I finally was able to install the fglrx and CCC packages. Unfortunately, after reboot, I was hit with low-graphics mode and when I finally did login, I'd lost unity. And to top it off, now vgaswitcheroo is misbehaving and not turning off the unused graphics card.

---

### Post by QIII on 2012-05-22
OK.  Let me do a bit of research.

---

