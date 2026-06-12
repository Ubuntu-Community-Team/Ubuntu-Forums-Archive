---
title: "Acer Travelmate touchpad no longer works after Ubuntu 8.04 installation"
date: 2008-06-02
forum: Hardware
---

### Post by Gamgee on 2008-06-02
Hi, I've recently installed Ubuntu 8.04 on my Acer Travelmate 4230 laptop.

While having a look using the LiveCD and after installation my touchpad occasionally froze during normal use, requiring a reboot to get it working again. Yesterday I updated using using the Update Manager (which among other things installed a new kernel). My touchpad froze a few minutes later - so I rebooted, and the touchpad has not worked at all since - even in Windows! I've got an external USB mouse, which works fine.

I've had a look at the BIOS settings, but there's nothing that seems relevant (I've read about disabling Legacy USB support after touchpad problems, but my BIOS doesn't have the option). I've also looked at xorg.conf (there's an entry for a synaptics touchpad) but since the touchpad isn't working in Windows either, it seems that there's something lower-level going on.

Obviously this could be a hardware fault, but it seems a strange coincidence that the touchpad would play up just after installing Ubuntu, then stop working entirely after upgrading the kernel.

So my question is - is there any way the installation could have messed with, say, BIOS settings in such a way as to interfere with the touchpad like this?

Any help would be much appreciated!

---

### Post by Zorael on 2008-06-02
> **Gamgee said:**
> So my question is - is there any way the installation could have messed with, say, BIOS settings in such a way as to interfere with the touchpad like this?
This seems very, very unlikely.
> **Gamgee said:**
> My touchpad froze a few minutes later - so I rebooted, and the touchpad has not worked at all since - even in Windows! I've got an external USB mouse, which works fine.
I'd chalk this up to coincidence. If it has been freezing by itself for a while and then suddenly just gave up, hardware failure springs to mind. Your best bet would be to send it in for repair, if you still have warranty. Buying your own spare and installing it yourself would be iffy, since you don't know if it's the touchpad itself failing or the motherboard.

I have an Acer Aspire 9815, and under Windows I've had the touchpad freeze once or thrice. I just had to go into Mouse Settings to disable it and enable it again, then it worked. Since it never happened under linux I attributed this to shoddy Windows drivers, so hearing your account is alarming.

---

### Post by Gamgee on 2008-06-04
Hi Zorael, thanks for the rapid reply.

> **Zorael said:**
> 

I'd chalk this up to coincidence. If it has been freezing by itself for a while and then suddenly just gave up, hardware failure springs to mind. 



Well, it had only been freezing for a few hours (installed then upgraded the kernel on the same day) - it hadn't been playing up for a few days then failed...
Still, I think you're probably right - after all, unlikely coincidences happen all the time :-)

Cheers

---

### Post by stefan.ciobaca on 2008-06-20
Hi!

I have the same problem. I've just upgraded my Acer Travelmate to 8.10 and the touchpad stopped working. When I reboot to Windows, it doesn't work there either. However, hitting Fn + F7 solves the problem in Windows. After reboot, touchpad still doesn't work in Ubuntu.

Any suggestions?

---

### Post by stefan.ciobaca on 2008-06-20
Ok. I'm back with some more details.

One thing I noticed is that the device for touchpad has changed from /dev/psaux to /dev/input/event8 (or /dev/input/mouse1, it's not clear what's the difference between the two).

I checked this out by "sudo cat /dev/input/event8" at a real console (Alt+F1) (not xterm), and using the touchpad (move, click, etc).

I then messed up my xorg.conf file, which made X start in low resolution but with working touchpad (WTF -- nothing was changed in the configuration of the touchpad?). After ~ 20 varous tries with parameter settings in xorg.conf and trying to add i8042-nomux=1 to the kernel params as suggested by some other threads on touchpads, I just deleted the xorg.conf fie (I do have a backup) and restarted gdm.

Surprise result: touchpad and video working properly.

My guess is that the upgrade somehow messed up the xorg.conf file.

---

### Post by stefan.ciobaca on 2008-06-20
That being said, I think 8.04 is the worst Ubuntu so far... First Ubuntu upgrade that went totally wrong and ruined my day, xfce not starting anymore...

---

### Post by Gamgee on 2008-06-21
So simple! That's done it - easy when you know how. Thanks Stefan, that's solved a very irritating issue!

By the way, I've found Fn+F7 also works to enable/disable the touchpad in Ubuntu...

---

### Post by iTawm on 2008-06-21
I think my problem is similar, I disabled my touchpad with Fn+F7 while using another mouse and I had to shutdown my laptop, forgetting to re-enable my touchpad. Now that I've booted Ubuntu back up, my touchpad is still disabled and Fn+F7 is refusing to re-enable it.
As far as I can tell xorg.conf is unchanged though.

---

### Post by tonymaro on 2008-12-26
I'll add one thing for anyone who finds this post later...  This also drove me up the wall.  I finally realized that after upgrading to 8.10, Ubuntu had unchecked the enable touchpad option in the mouse settings.  All I had to do was log in using a USB mouse, go to System + Preferences + Mouse, click the Touchpad tab and check the box to enable the touchpad.  After that it worked, and the FN+F7 to enable / disable the touchpad on the laptop worked again in Linux.

---

### Post by bapoumba on 2009-08-24
> **tonymaro said:**
> I'll add one thing for anyone who finds this post later...  This also drove me up the wall.  I finally realized that after upgrading to 8.10, Ubuntu had unchecked the enable touchpad option in the mouse settings.  All I had to do was log in using a USB mouse, go to System + Preferences + Mouse, click the Touchpad tab and check the box to enable the touchpad.  After that it worked, and the FN+F7 to enable / disable the touchpad on the laptop worked again in Linux.

Sorry to revive this older thread, but I had the same issue on an ACER Aspire 5100 with a new karmic install. This worked for me, I even could enable edge scrolling, thanks :)

---

