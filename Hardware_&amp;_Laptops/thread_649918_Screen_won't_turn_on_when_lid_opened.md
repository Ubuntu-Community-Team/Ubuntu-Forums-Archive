---
title: "Screen won't turn on when lid opened"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by shoofy on 2007-12-25
Ever since installing the latest ATI Catalyst driver on my Dell E1505 with an ATI Mobility Radeon X1400, if I shut the lid and then the screensaver locks the screen or if the screen is locked and then I shut the lid, when I open the lid again I can't get the screen to go back on and I have to reboot the computer. If I shut the lid without the screensaver going on it turns on like normal.

Does anyone know why this might be happening? I like having my screen lock when I shut the lid or else I wouldn't care about this issue. Is there a way to solve it, or do I have to downgrade the ATI driver?

---

### Post by blukis on 2007-12-31
I had the same problem with my Dell e1505 pre-loaded with Ubuntu 7.04.  I remember this fixing it for me:

[http://ubuntuforums.org/showthread.php?t=377873#post2871705](http://ubuntuforums.org/showthread.php?t=377873#post2871705)

(To make matters confusing, I have notes to the effect that I actually installed "xserver-xorg-video-i810" to get it fixed.)  But now I upgraded to 7.10, and the screen won't come on again with I open the lid.  Reinstalling these packages doesn't seem to help...  :(

Update: I hate to add to the mix of fixes for this I'm seeing on the forum, but some combination of uninstalling and reinstalling "xserver-xorg-video-i810" and "xserver-xorg-video-intel", plus doing the change in the thread below worked for me.

[http://ubuntuforums.org/showthread.php?p=3038240#post3038240](http://ubuntuforums.org/showthread.php?p=3038240#post3038240)

---

### Post by shoofy on 2007-12-31
Thanks for the reply, but I have an ATI card, not intel, so installing intel drivers almost defintitely wouldn't help. My problem also is not with suspend/hibernate. Thise are known not to work with Gutsy and the latest ATI fglrx drivers.

My problem is definitely tied to gnome-screensaver, since it works fine if I disable the screensaver. I'm home now, so I have more resources available to try to troubleshoot the probelm. I'll try sshing in and seeing what's preventing the screen from going on.

---

### Post by shoofy on 2007-12-31
hmmm... seems that activating the screensaver, closing the lid and opening it again disables the ssh, vnc, and samba servers, so I can't get in to do anything. It kind of seems like the screensaver is overriding my gnome-power settings and telling it to suspend (which usually causes thee sorts of problems) when the lid is closed. I guess it's time to look into how gnome-screensaver handles power settings.

---

### Post by shoofy on 2008-01-01
I rolled back to the 7.11 Catalyst driver and the problem is gone. 7.12 didn't work especially well for me even without this particular problem, so I'll just wait for 7.13 before upgrading again.

---

