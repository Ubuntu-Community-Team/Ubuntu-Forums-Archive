---
title: "TP T40 + Gutsy + ATI R250 [Mobility FireGL 9000]"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by Waikei666 on 2007-11-16
Hello,
First I must admit I am completely new to Ubuntu and after reading from this community I have decided to give the latest release a go.  I currently own a Thinkpad T40 which has the ATI Mobility FireGL 9000.

I have installed Gutsy, dual booting with the original XP.

Whilst impressed with the speed at which Ubuntu loads, I have not been able to get the Desktop effects to work ("Desktop effects could not be enabled" prompt)

Admitting to be an absolute noob on this,  the wording I use to describe what I did here maybe abit confusing.
Having browsed through various threads here I have already noted that there are some additional configurations that need to be done in order to get it working.  I don't know whether what I did was correct thought (but at least I did back up the default xorg.conf file!)

First I used the update manager and installed all the updates (incl. compiz, fglrx etc) (I think I then tried to do it again on the terminal with commands but it verifies that I already have the latest things installed)

1. I went into the xorg.conf file and changed the "ati" driver to "radeon" and I was thrown into reduce graphics mode so I changed it back to "ati"
2. I went into the xorg.conf file and changed the "ati" driver to "flgrx" and I was also thrown into reduce graphics mode
3.  Of course, desktop effects is still not able to work

Ultimately, I would like to achieve (being realistic I will be happy if I can solve (a) in the weekend!):
a) Desktop effects to work
b) Compiz fusion to work
c) Dual screen with my Samsung external monitor (think its a SyncMaster)
d) For Hibernation and Suspend to work (somehow Suspend does not work on lid close and last time I Hibernated and came back the next day when I booted up the computer the Fan stopped working (!!??))
e) To enjoy Ubuntu so much that I can remove the XP!

So.. if anyone could give me some guidance on that would be fab.

I am at the office right now so won't be able to post the xorg.conf here...

Cheers,

Vicky

---

### Post by overdrank on 2007-11-17
Hi and welcome, this thread may help
[http://ubuntuforums.org/showthread.php?t=550082&highlight=Gutsy+ATI+R250&page=2](http://ubuntuforums.org/showthread.php?t=550082&highlight=Gutsy+ATI+R250&page=2)
Good luck!

---

### Post by Waikei666 on 2007-11-17
Thanks! the first issue is solved!

(by by pasing the quicktest done by Compiz)

---

### Post by zefgi on 2008-03-21
I have the same configuration of hardware (Thinkpad T40, ATI Radeon RV250 (Mobility FireGL 9000) with Ubuntu 7.10.  I am having difficulty getting compiz to work.  I have tried to alter my xorg.conf file as described in the link above, but I can't get it to work.  

I still have fglrx.  Do I need to swap fglrx for glx because I wasn't sure if that was just for Nvidia graphics cards.  If so, how do I do that. (Someone mentioned in the posted link above that they did a fresh install and to get rid of the ATI driver.  I was never given a choice and I just installed Gutsy 2 days ago.)

Any help?  Is this post still alive?

---

### Post by zefgi on 2008-03-22
> **zefgi said:**
> 

I still have fglrx.  

I guess I am not running this driver.  I'm using the ati driver.  I looked in the compiz file and the ati driver is whitelisted.

When I run compiz I get:

zach@ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 


I tried the fix by making changes to xorg.conf and running again with flags:

zach@ubuntu:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:zach@ubuntu:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

Then the screen gets all weird and I lose the right quarter.  I made the changes to the xorg.conf file from the post above to correct that, but still nothing.

Waikei666, what did you do to your installation to get compiz working?

---

