---
title: "Dell Vostro 360 doesn't even start ubuntu live cd X server"
date: 2011-10-07
forum: Hardware
---

### Post by pmatos on 2011-10-07
Hi,

I have tried already a CD and a USB and both failed (live cd for 11.04 - 64bit). 
I insert the USB and boot into ubuntu live cd, however, once it's time for X server to come up, nothing comes up. I hear the sound of ubuntu starting but the display is completely black.

Vostro 360 is an all-in-one with a 23'' touch screen display  released recently by dell.

How can I go to the command line in the livecd instead of the X server so I can try to see what's happening?

Cheers,

Paulo Matos

---

### Post by Redblade20XX on 2011-10-07
Can I ask what graphic card you have? Also can you try pressing Alt+F2.

- Red

---

### Post by pmatos on 2011-10-07
> **Redblade20XX said:**
> Can I ask what graphic card you have? Also can you try pressing Alt+F2.

- Red

Opps, forgot that detail: 1GB NVIDIA GeForce GT 525M

---

### Post by Matt_Fussell on 2011-12-13
I've managed to get Ubuntu 11.10 installed on a new Vostro 360 all in one desktop.  The key was to use the 'nomodset' option when installing and run the live installation.  I'm currently able to access the desktop by starting in recovery mode, dropping to a root shell, typing 'restart' (discovered completely by accident), and then logging in.  The resolutions is currently off; I'm working on a solution for that.  I'll post more when I make some progress.

---

### Post by pmatos on 2011-12-14
> **Matt_Fussell said:**
> I've managed to get Ubuntu 11.10 installed on a new Vostro 360 all in one desktop.  The key was to use the 'nomodset' option when installing and run the live installation.  I'm currently able to access the desktop by starting in recovery mode, dropping to a root shell, typing 'restart' (discovered completely by accident), and then logging in.  The resolutions is currently off; I'm working on a solution for that.  I'll post more when I make some progress.

Thanks Matt, I also got that far. Please check the follow-up: [http://ubuntuforums.org/showthread.php?t=1860360](http://ubuntuforums.org/showthread.php?t=1860360)

---

### Post by Matt_Fussell on 2011-12-14
Done and done - new inquiries will be made there.

---

### Post by pmatos on 2012-04-30
After thousands of problems with my Dell I returned it for a refund. It's the end of my adventure with Dell. Never again.

---

