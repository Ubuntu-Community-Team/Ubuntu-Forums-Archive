---
title: "Ubuntu 9.10 FAIL - will not boot after clean install"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by jaime256 on 2009-11-03
I used the same cd that was used on a sony laptop where Ubuntu was slow to install. Now a few days later with the same i386 cd on a Toshiba satellite A15-S127 and Ubuntu doesn't work after the computer reboots. This is the error I get:

error: no such device: e1fd4751-d683-4105-a799-e1f73c1dff91
Failed to boot default entries.
Press a key to continue.

When I press a key to continue I get the same message. I got pictures I will post in a bit when I get home, maybe this will help you guys figure out what's going on. Still at the other persons house. Oh yeah, this CD was downloaded on the day Ubuntu was supposed to be released. About 9:30am Los Angeles time, but from the UK server, I also downloaded it again at this house from an LA server, and both still say beta4 on them! WTH?

Currently installing 9.04 onto the laptop, again for the second time since I had already wiped the darn thing. It has a WD 160GB HD so space is no problem and 9.04 boots up fine. Too bad the HP 1020 is still a royal pain in the butt to get working.

Of course it didn't help that I found this after I had tried my install and failed miserably.
[http://www.theregister.co.uk/2009/11/03/karmic_koala_frustration/](http://www.theregister.co.uk/2009/11/03/karmic_koala_frustration/)

I should note that recovery doesn't do anything either. Notice the beta4 on the top of the last picture??? This is from the download I did today. What happened to the actual release?

I should also make it clear that I'm still having problems printing from Windows 7 RC to the nas printer as well. So nothing is perfect, I know.

---

### Post by jaime256 on 2009-11-30
I just tried to do a fresh install on a Dell D600 laptop with the i386 disk I used to install on the Sony and Toshiba laptop. Ubuntu 9.10 Fails again on this other laptop. I only get a blank screen after booting and choosing to install. The screen just goes blank and the dvd drive stopped spinning. Well, I don't feel like bothering with this version again, ever. I'll probably stick with 9.04 or something else if things don't stop working on 9.04. Currently downloading another distro to test.

---

### Post by jaylsi on 2009-11-30
The beta you see is for GRUB software, not 9.10 beta. You probably have downloaded the correct version. Have you tried 9.10 live CD? Did you do the install with wiping out the whole drive or still keep the existing OS?

---

### Post by presence1960 on 2009-11-30
I would start at the beginning. Did you:

[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
MD5SUM[/URL] the downloaded iso prior to burning as an image to CD?

Did you burn the iso as image to CD at 4x-8x speed. This critical since burning an iso image is far more intricate than copying data, video or music files. It is ok to burn them at a high speed, but with an iso image one little miscue can render the install no good or even the CD useless. If your software doesn't allow you to choose burn speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.

When booting the Live CD choose check disk for defects prior to installing Ubuntu or choosing try Ubuntu without any changes to your computer.

---

### Post by jaime256 on 2009-11-30
Yes, disk check is fine. I was able to kind of install it on the sony. It gave some errors but installed on that one. The Toshiba and Dell, no luck. I have had no problems installing 9.04 on all of them though. Thought you would like to know.

> **presence1960 said:**
> I would start at the beginning. Did you:

[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
MD5SUM[/URL] the downloaded iso prior to burning as an image to CD?

Did you burn the iso as image to CD at 4x-8x speed. This critical since burning an iso image is far more intricate than copying data, video or music files. It is ok to burn them at a high speed, but with an iso image one little miscue can render the install no good or even the CD useless. If your software doesn't allow you to choose burn speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.

When booting the Live CD choose check disk for defects prior to installing Ubuntu or choosing try Ubuntu without any changes to your computer.

---

### Post by jaime256 on 2009-12-17
I'm able to use the Sony with the 9.10, but does anyone have a clue why it takes longer for the wireless to connect. I also tried to force it like I used to on the previous version, but it's grayed out. See the attached screen shot. And also, if I turned off the bluetooth, it comes back on all the time after rebooting. Is there any way to make it stay off until I want to use it without turning off the wireless too? I know the old version was like that. That would save me battery if I can turn off just one, but I'm not sure if this works on this version either.

---

### Post by Julita on 2009-12-17
You can disable bluetooth, running

```
update-rc.d -f bluetooth remove
``` There is also sysv-rc-conf where you can manage all your services.

---

### Post by jaime256 on 2009-12-18
Thank you, I'll give that a shot.

> **Julita said:**
> You can disable bluetooth, running

```
update-rc.d -f bluetooth remove
``` There is also sysv-rc-conf where you can manage all your services.

---

### Post by Tsenra Tretsom on 2010-01-25
The IBM Travelstar 20GB harddisk of my old Compaq Evo N610C laptop was full with bad sectors. It had Xubuntu 9.10 alternate (XFCE) and worked fine. But the harddisk failed and I had to replace it.
I bought a Western Digital 160 GB 5400 rpm PATA harddisk replacement. I tried to do a clean install of Xubuntu 9.10 alternate. The laptop would not boot and i got the same error message as commented here. Then I tried Ubuntu 9.04 i386, Ubuntu 9.10 i386, Ubuntu 9.10 i386 alternate, Xubuntu 9.04 alternate but they all showed me the same mentioned error.
And unfortunately i am quite a Linux novice i am not able to fiddle around this problem.
So I installed Ubuntu 8.10 i386 and was a bit surprised that it would boot. So my laptop is a live again, but not with the desired OS (Xubuntu 9.10 alternate). I am really wondered why Ubuntu OS versions above 8.10 are not able to boot and can not find the appropriate harddrive partition. That is my guess, conclussion. Is there an explaination for this behavior and is there a (simple) workaround? I can not believe that a brand new (simple) harddisk is not supported by brand new Linux OS version of (X)Ubuntu or that is mix up the boot order in some way.

Another issue i forgot to mention when trying to install (X)ubuntu 9.04 and higher. The graphics support (ATI Mobile graphics chip) for my old Compaq Evo when installing (X)Ubuntu is getting slow untill you are not able to select anything during the setup. Even screens "disappear" and I had to break of the setup because there was no setup dialog.

---

