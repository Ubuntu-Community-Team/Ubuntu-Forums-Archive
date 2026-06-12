---
title: "Ubunu 9.04 new Install Start-up freeze"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by siabost on 2009-06-06
Hi,
I have a Dell Dimension 2400 Desktop with Celeron 2.4Ghz processor dual-booting Win XP & a newly installed Ubuntu 9.04 (which is NOT booting).

I used to run Ubuntu 8.04 (very happily) & thought I'd try the latest 9.04 version.

I had to use the alternate CD to install as the standard ones would always freeze on me but that's ok as I prefer the text-based installer anyway.

Install of 9.04 went perfectly but on reboot the boot freezes just after the Ubuntu loading screen disappears - the rotating circle logo stops after about a second and that's it.

I've tried removing "quiet splash" from the boot line but the text disappears at the same point that the Ubuntu logo does/did & I'm left with the small non-rotating circle in the middle of the screen and I learn nothing!

My computer is about 4 years old and is very useable so I don't consider it ancient, yet. I would have thought that if an older version of Ubuntu loads ok the new one should be even more considerate! 

Small grumble apart, I hope someone can help as I look forward to being able to try 9.04.

Any help much appreciated.

ADDITIONAL INFO: My comp can be a bit moody on start-up (very occasionally). On having to do multiple restarts on the button the BIOS sometimes refuses to kick in and I see nothing on screen - leaving it off at mains overnight uasually sorts this out. Even more occasionally I get a very slow BIOS load and a message containing this info (as this time on trying to boot windows xp: > The BIOS is not fully ACPI compliant. Contact vendor or visit [www.hardware-update.com](www.hardware-update.com). If an ACPI compliant BIOS update is not available ACPI can be disabled by pressing F7 when prompted to install storage drivers...
Technical: 0x000000A5 (0x00000011, 0x00000008, 0xF7ADC0F1, 0x0100000D)

---

### Post by Megy on 2009-06-06
I'm having the same trouble, and I'm virtually lost as to what's the problem. On start up, the Ubuntu icon and loading bar show up but then it goes black and freezes. I tried booting it from a previous kerenel, but that didn't work. Devsda check said everything was fine, and I can't find a broken package...

I'm at a loss and severely disappointed.

---

### Post by wpshooter on 2009-06-06
> **siabost said:**
> Hi,
I have a Dell Dimension 2400 Desktop with Celeron 2.4Ghz processor dual-booting Win XP & a newly installed Ubuntu 9.04 (which is NOT booting).

I used to run Ubuntu 8.04 (very happily) & thought I'd try the latest 9.04 version.

I had to use the alternate CD to install as the standard ones would always freeze on me but that's ok as I prefer the text-based installer anyway.

Install of 9.04 went perfectly but on reboot the boot freezes just after the Ubuntu loading screen disappears - the rotating circle logo stops after about a second and that's it.

I've tried removing "quiet splash" from the boot line but the text disappears at the same point that the Ubuntu logo does/did & I'm left with the small non-rotating circle in the middle of the screen and I learn nothing!

My computer is about 4 years old and is very useable so I don't consider it ancient, yet. I would have thought that if an older version of Ubuntu loads ok the new one should be even more considerate! 

Small grumble apart, I hope someone can help as I look forward to being able to try 9.04.

Any help much appreciated.

ADDITIONAL INFO: My comp can be a bit moody on start-up (very occasionally). On having to do multiple restarts on the button the BIOS sometimes refuses to kick in and I see nothing on screen - leaving it off at mains overnight uasually sorts this out. Even more occasionally I get a very slow BIOS load and a message containing this info (as this time on trying to boot windows xp:

Is there a BIOS update available for your computer ?  If so, have you tried to install it ?

---

### Post by Megy on 2009-06-06
> **wpshooter said:**
> Is there a BIOS update available for your computer ?  If so, have you tried to install it ?

I think I've seen that, but I'm running a memtest v2.11 right now. It seems like everything is there, it just can't boot. I'll try that when I'm done.

---

### Post by ktritty on 2009-06-06
(Similar issue with Graphical Installer crash.)

Hello, I am trying to install Kubuntu 9.04 on a friend's computer.  It says "Toshiba Satellite" (I know nothing of these).  It had Pirated XP on it (originally came with windowsmillenium edition) and had very obvious virus trouble.

I cannot get the installation to run (it always crashes about 90% of the way through the loading bar early in the install cycle).

Notes:
I can get Ubuntu Server Edition to load, install, and run flawlessly.
Windows XP is no longer on the system after Server Edition Install (it was BADLY mangled anyhow)

I see links to an alternate installer CD that is more like the server edition's.  Is also there one available for Kubuntu?  I looked, but wonder if someone may know more than I have found.

Many Thanks

---

### Post by wpshooter on 2009-06-06
Did you check the integrity of your Kubuntu CD by running the verification function that is found on the initial Kubuntu boot screen menu ?

I think there is also an ALTERNATE version for Kubuntu.

---

### Post by siabost on 2009-06-06
Hi Guys,

I think I do have BIOS trouble - BIOS loads VERY slowly, if at all, now. I will download latest and flash the BIOS.

Re someone else's comment: I had to use the alternate CD installer for Ubuntu and it installed flawlessly as it always does for me. There will be an alternate version for Kubuntu I imagine too.

As long as the text is helpful & clear I've never understood why the Installer has to be any fancier than absolutely necessary - the object being to get the thing installed & **then** enjoy all that is fancy!

I will try flashing the BIOS and report back.

Thanks.

---

### Post by ktritty on 2009-06-06
The intergrity check out okay.  I also ran md5 command in bash on my MacBook before burning, and verified using OSX disk utility, all good.

I succeeded putting Ubuntu 9.04 on it with the alternate install version.  It won't run.  I think this laptop does not get along with KDE or GNOME, because anything I've tried so far with GUI fails, but everything I've tried so far (Ubuntu Server, Ubuntu Desktop in recovery mode as command line only) work perfectly fine.

I have tried to run auto-fix of graphics problems in the recovery mode, but no avail.  I am going to post a new thread on this issue.

In the meantime, coud you maybe help me find the Kubuntu text-based installer?  I still don't see one online.

Thanks

---

### Post by ktritty on 2009-06-06
> **siabost said:**
> 
As long as the text is helpful & clear I've never understood why the Installer has to be any fancier than absolutely necessary - the object being to get the thing installed & **then** enjoy all that is fancy!

Thanks.

I FULLY AGREE!

Ubuntu Developers & Packagers:  Please Keep installers bare bones!

---

### Post by siabost on 2009-06-09
ktritty,

Re your laptop problem:

I had a problem similar to yours booting Debian on an Easynote laptop. This may be worth a try -

1. Boot in recovery mode
2. Drop into a shell (command line)
3. TYPE: ```
sudo nano /etc/default/acpi-support
```
4. CHANGE: ```
SAVE_VBE_STATE=TRUE
``` to ```
SAVE_VBE_STATE=FALSE
```
5. Press "Ctrl+O" then "Return" to save.
6. Reboot

Original thread was [https://lists.ubuntu.com/archives/ubuntu-devel/2006-April/017581.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-April/017581.html)

On my problem, I tried flashing the BIOS but it made no difference - something is definitely ropey within my hardware!

Best of luck.

P.S. Just tried the above on my Dell Desktop & Jaunty booted correctly!! A more minor problem now though: no Network Manager Applet!

---

