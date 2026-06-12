---
title: "Can't Change Orientation or Resolution of Monitor"
date: 2019-12-20
forum: Hardware
---

### Post by adrian-doyle on 2019-12-20
Hi, I'm new to Ubuntu. Used Mint for a while but built a new machine recently and wanted to try this OS.

Background:
Machine I'm running uses an Aorus Xtreme x570 motherboard with WiFi antennae, Nvidia GTX 1050 TI GPU, and is running Ubuntu 18.04.3 LTS. The kernel that came with this was 5.0.0.37.40. This caused me a problem with the WiFi whereby the Ubuntu couldn't detect any WiFi hardware. I upgraded the kernel to 5.4.5 and this fixed the WiFi issue.

Problem:
Since I upgraded the kernel, I haven't been able to change the resolution of my monitor. This was working fine before but now it's stuck at 1024:768, when it should be 1920:1080. In settings there is only one option for resolution and changing the orientation does nothing.

What I've tried:
1. I rolled back the kernel to 5.3.18. This didn't fix the problem, so I rolled back again to the original kernel, 5.0.0.37.40. This didn't fix the problem, and I lost the use of WiFi again. So, I moved forward again to 5.4.5.

2. I tried changing my GPU driver from the open source one to the proprietary one. This did nothing, so I changed back.

3. I looked for solutions online and some people mentioned xrandr. I ran this command in terminal and this was the output:

```
(base) my-broken-PC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 
  1920x1080 (0x2c0) 173.000MHz -HSync +VSync
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock  67.16KHz
        v: height 1080 start 1083 end 1088 total 1120           clock  59.96Hz



```

It seems like Ubuntu isn't able to recognise the monitor anymore and I have no idea how to fix it.

If anyone could help that would be really appreciated, as I've been trying to fix this WiFi issue for days and now as soon as it has, something else has broken.

Thanks in advance.

Adrian.

---

### Post by Autodave on 2019-12-20
How is the monitor connected to the PC: what kind of cable and are there any adapters being used?

Check your connections: make sure that they are all secure.  I have had a little luck by powering down the machine, reconnecting the monitor and then powering up again.

---

### Post by adrian-doyle on 2019-12-20
HDMI cable only, from GPU to monitor. No adaptors.

Reinstalling Ubuntu solves the problem, but updating the kernel again recreates it.

---

### Post by mörgæs on 2019-12-21
How does a fresh install of 19.10 behave?

---

### Post by adrian-doyle on 2019-12-21
> **mörgæs said:**
> How does a fresh install of 19.10 behave?

I haven't tried 19. It's a PC for work so I'm a bit concerned about installing non-LTS.

---

### Post by Autodave on 2019-12-21
If 19.10 works, then you will upgrade to 20.04 when it becomes available.  I believe the reason mogaes asked about that is because it would have newer drivers than 19.04 or previous versions.

---

### Post by mörgæs on 2019-12-21
Yes. Newer drivers and less bugs. 

Especially for a work PC it's important to test a number of releases before choosing one. The length of support is less important as one will get to 20.04 sooner or later anyway.

---

### Post by adrian-doyle on 2019-12-22
> **mörgæs said:**
> Yes. Newer drivers and less bugs. 

Especially for a work PC it's important to test a number of releases before choosing one. The length of support is less important as one will get to 20.04 sooner or later anyway.

I'd like to give it a try. It'd be great if it solves these issues. Is there any way to upgrade from 18 to 19 and take my current configuration over too? Or, will I have to set everything up fresh on 19?

Alternatively, is there a way to save a copy of my 18 configuration exactly as I have it set up, so that I can roll back easily if I need to?

---

### Post by Autodave on 2019-12-22
Upgrades, while better than they used to be, still don't always work as planned.  If it were me, I would first try booting to 19.10 from a USB and see if it works.  If it doesn't, then that isn't going to help you.  If it DOES work, then I would try upgrading what you are currently using.  If the upgrade works, you're in luck.  If not, at least you would then know that a clean install would work.

---

### Post by adrian-doyle on 2019-12-22
> **Autodave said:**
> Upgrades, while better than they used to be, still don't always work as planned.  If it were me, I would first try booting to 19.10 from a USB and see if it works.  If it doesn't, then that isn't going to help you.  If it DOES work, then I would try upgrading what you are currently using.  If the upgrade works, you're in luck.  If not, at least you would then know that a clean install would work.

My confusion was with something a bit more basic. I'm pretty new to Linux, so the file structure isn't entirely clear to me yet. I was going to try booting from a USB, as you suggest, to see if that worked. If it did, I was just going to install it fresh, because I'm not aware of any other way to upgrade from 18 to 19. If this isn't the suggested means of upgrading from one version to another, please do let me know the correct way to do so. 

In any case, my question is, if I save a copy of my home directory from 18 to a USB drive, then replace the home directory on a fresh install of 19 with the copy of my old home directory, will that bring over all the configuration from my current version? Or, would doing so cause issues with the new install? Is the home directory tied to the Ubuntu version (would my current home directory only work with 18, for example)? I don't know what the extent of the contents of the home directory are, so I don't want to break anything by replacing the directory in 19 with a copy from 18, especially if it wouldn't even bring over my current settings.

Of course, if there's another way to upgrade that's slipped by me, that might be a much better option, as long as I have a way to backup what I currently have set up so that I don't lose it.

Thanks for all the help and your patience with me so far, by the way. It's much appreciated while I try to get to grips with my new OS.

---

### Post by CatKiller on 2019-12-22
> **adrian-doyle said:**
> My confusion was with something a bit more basic. I'm pretty new to Linux, so the file structure isn't entirely clear to me yet. I was going to try booting from a USB, as you suggest, to see if that worked. If it did, I was just going to install it fresh, because I'm not aware of any other way to upgrade from 18 to 19. If this isn't the suggested means of upgrading from one version to another, please do let me know the correct way to do so. 

In any case, my question is, if I save a copy of my home directory from 18 to a USB drive, then replace the home directory on a fresh install of 19 with the copy of my old home directory, will that bring over all the configuration from my current version? Or, would doing so cause issues with the new install? Is the home directory tied to the Ubuntu version (would my current home directory only work with 18, for example)? I don't know what the extent of the contents of the home directory are, so I don't want to break anything by replacing the directory in 19 with a copy from 18, especially if it wouldn't even bring over my current settings.

Of course, if there's another way to upgrade that's slipped by me, that might be a much better option, as long as I have a way to backup what I currently have set up so that I don't lose it.

Thanks for all the help and your patience with me so far, by the way. It's much appreciated while I try to get to grips with my new OS.

**All** of the software that's installed on your system is a set of packages. It can all be upgraded to newer versions. In the old days, this was done by pointing the package manager at the new repositories instead of the old ones and letting it loose. These days there is a bundle of scripts (called do-release-upgrade) that does sanity checks, so things are less likely to go wrong. Things *can* still go wrong, although I haven't personally had any problems, particularly if a user has lots of software from outside of the main repositories, or has done lots of customisation, or if there's a big structural change between the two releases. Upgrading from one LTS to the next LTS, or from one interim release to the next release, using only software from the standard install image is all that's officially tested. The further you are from that ideal the more likely you are to stumble across issues, and even in the ideal case the upgrade is not officially supported - I think Kubuntu 14.04 &#8594; 16.04 was like that, although it might have been a different version pairing. Installing fresh is quite a lot quicker than doing the upgrade.

The home folder isn't tied to anything but the user and decades of habit. The *config files* inside it are tied to whatever application makes use of them. For the most part applications can understand config files from a previous version, or - if there's been a big change in syntax or whatever - convert the old file to the new format, but that's down to the application itself to sort out. The config files in your home directory are hidden by default in most file browsers (they start with a .) so you'd want to make sure that you'd got them all when making your backup. Ownership and permissions are tied to the user's id (1000 for the first user, 1001 for the second, and so on, on Ubuntu systems) rather than the user's name, so you'd want to add users in the same order if you had more than one.

First thing is to try the live version of the new release, to see if it actually fixes anything. The thoughts about upgrading might be moot.

---

### Post by adrian-doyle on 2019-12-23
> **CatKiller said:**
> First thing is to try the live version of the new release, to see if it actually fixes anything. The thoughts about upgrading might be moot.

Just tried 19.10 from a USB drive. WiFi works and no problems with resolution. My question now is, what's the best way to upgrade to it?

Fresh install and lose all my settings, or some other way that might let me keep my config?

---

### Post by mörgæs on 2019-12-23
Take a backup copy of your old /home and store it somewhere but don't use it. 

The new install should be virgin without any cruft settings brought along from 18.04.

Please spread the word that at this day and age 19.10 should be the default version to install. 18.04 might serve a purpose only in rare exceptions.

---

### Post by adrian-doyle on 2019-12-23
> **mörgæs said:**
> Take a backup copy of your old /home and store it somewhere but don't use it.

Ok, but, if I don't use it then what do I do with it to get my configuration over to 19? Or, is it not worth even trying?

> **mörgæs said:**
> Please spread the word that at this day and age 19.10 should be the default version to install. 18.04 might serve a purpose only in rare exceptions.

I'll inform the masses.

---

### Post by mörgæs on 2019-12-23
I would begin configuring everything from scratch. If a particular application causes problems I'm sure people here are willing to help.

---

### Post by adrian-doyle on 2019-12-24
> **mörgæs said:**
> I would begin configuring everything from scratch. If a particular application causes problems I'm sure people here are willing to help.


Alright. Thanks everybody for all the help here.

Adrian.

---

### Post by mörgæs on 2019-12-25
You're welcome.
Please mark the thread solved.

---

