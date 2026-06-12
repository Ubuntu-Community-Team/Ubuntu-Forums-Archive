---
title: "upgrade to 9.04 failed. Please help!"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by zeiz on 2009-06-02
I have ATI video card, but 8.04 and 8.10 worked just fine. 

After upgrade 8.10 => 9.04 (from update manager) I got frozen screen with broken graphics.

Please help to fix or roll back to 8.10!

---

### Post by raymondh on 2009-06-02
Hello Zeiz,

Have you activated the drivers?  Check in system > administration.  Maybe, maybe, ATI has provided support/driver for your card.

What have you done so far to fix the issue?  I'm just gathering as much info as possible :)

also, pls. post the terminal output of

lspci

Regards,

---

### Post by zeiz on 2009-06-02
Thanks a lot!
The problem is that I even cannot log on. After progress bar finishes next screen appears divided on two parts: upper one in black and lower one looks like part of login screen with black strips. No cursor, no login box.
So far I tried recovery mode:
1. to autofix video - no any action seems to occur with this option;
2. to repair broken packages. It does a lot and ends up with warning: failed to fetch [http://...canonical/](http://...canonical/)...  [http://..ubuntu/](http://..ubuntu/)...
Please run apt-get update.
I did from root shell. It installs 4 packages and removes 4 packages.
After rebooting - no changes: the same broken login screen. Second attempt leads to the same warning and "run apt-get update" again and again all the same.
My card is exactly PCI-E ATI Radion X700 Sapphire.

---

### Post by merlinus on 2009-06-02
What happens if you press Ctrl-Alt-F2 when you get to the weird graphics?

---

### Post by zeiz on 2009-06-02
Alt-Ctrl-F2 gives nothing. It's completely frozen. Only power button works:)

---

### Post by merlinus on 2009-06-02
Try this at the command prompt when you boot into recovery mode:

```

[B]sudo dpkg-reconfigure xserver-xorg
[/B]
```keep the defaults but select vesa as your video driver, and restart.

---

### Post by zeiz on 2009-06-02
```
sudo dpkg-reconfigure xserver-xorg

```

This doesn't give choice to select vesa driver. Only keyboard options are changeable.
/etc/X11/xorg.conf contains Section "Device" and there is only "Configured device" there.
"Configured device", "Configured monitor", "Default screen" - nothing to configure :)
My monitor is SyncMaster2253bw, res. 1680x1050_60. Video: ATI Radeon X700 Sapphire. Maybe I can try somehow to boot with 1024x768?

---

### Post by blackandwhitepandabear on 2009-06-02
Hello all,
I think I am having the exact same problem after updating. I get as far as the Ubuntu load-up screen (with the horizontal bar turning orange from left to right). After that I get the "broken" screen; no possibility to log in. I can't seem to find any useful options from the recovery menu. 
Is there a way to revert back to 8.04?
Thanks...

---

### Post by raymondh on 2009-06-02
> **blackandwhitepandabear said:**
> 
Is there a way to revert back to 8.04?
Thanks...

As far as  I know, no automated way.  A clean re-install from the liveCD will be required.  If you do decide to, remember to backup/save your files someplace external and copy back to 8.04.

Good luck.

---

### Post by blackandwhitepandabear on 2009-06-03
Thanks Raymond - that appears to be the easiest option for me at the moment. 
Thank goodness I backed up just before the update... (which the Update Manager did explicitly suggest, to its credit)

---

### Post by zeiz on 2009-06-03
But not for me :(
That machine only accepts 7.10 from CD. 
I tried 8.04 - installation failed. Then 8.10 - failed too. Then I successfully upgraded 7.10 to 8.10 with update manager.
Maybe somebody knows how to re-upgrade under my circumstances?

---

### Post by 3startuna on 2009-06-03
I might sound like a jerk for this response but 


Just buy a nVidia card. 

ATi cards just run screwy with linux.

Plus their cards arent that expensive

---

### Post by raymondh on 2009-06-03
> **zeiz said:**
> But not for me :(
That machine only accepts 7.10 from CD. 
I tried 8.04 - installation failed. Then 8.10 - failed too. Then I successfully upgraded 7.10 to 8.10 with update manager.
Maybe somebody knows how to re-upgrade under my circumstances?

Hello Zeiz,

If you decide to "rollback", 

Save your files to an external source.  You can use the LiveCD to access your files and save/copy to a thumbdrive or external hard drive.

Consider doing a fresh, clean 7.10 install, if that is the only CD it will take.  Once done, and if possible, do

```
sudo apt-get update
sudo apt-get upgrade
```

As you know, apt-get upgrade is different from a distribution upgrade.  The intention is to be updated first before upgrading distributions.  Am not sure though, if 7.10 is still supported repo-wise.  Wouldn't hurt to try though :)  

From then on, do a distribution upgrade to 8.04. 

Good luck.

---

### Post by merlinus on 2009-06-03
+1!!!

I changed over from Matrox to nvidia, and have had no problems with upgrading to new versions of ubuntu.

And why support a company that refuses to provide open source drivers!!!!

---

### Post by zeiz on 2009-06-03
Well that's the story. This machine belongs to my daughter who is a student and lives far from my place.
I have 2 machines with NVidia (one is obsolete) and both was upgraded perfectly. That's why I suggested the upgrade to my daughter. So I'm guilty now!:cry: 
Thanks raymondhenson, I'll try that, we'll see.

---

### Post by raymondh on 2009-06-03
> **zeiz said:**
> Well that's the story. This machine belongs to my daughter who is a student and lives far from my place.
I have 2 machines with NVidia (one is obsolete) and both was upgraded perfectly. That's why I suggested the upgrade to my daughter. So I'm guilty now!:cry: 
Thanks raymondhenson, I'll try that, we'll see.

Hi Zeis,

Kindly post back results and we'll go from there ... success or errors :)

Regards,

---

### Post by zeiz on 2009-06-03
Nothing work so far and we decided to get 9.04 on CD and try clean install.
If it won't work we install 7.10 back and try upgrade to 8.04. 
Thank you guys!

---

