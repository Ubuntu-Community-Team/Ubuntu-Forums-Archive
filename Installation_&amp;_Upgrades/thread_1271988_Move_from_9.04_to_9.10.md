---
title: "Move from 9.04 to 9.10"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt on 2009-09-21
Hi All - 

I know this is bit of a forward thinking post - but I need some information and hopefully you all will be able to help.

With Ubuntu 9.10 being released end of next month, featuring a lot of fundamental changes - the primary ones being moving to ext4 and using GRUB2 - here are the questions that I have:

1) Will it be wise to just do a fresh install on Ubuntu 9.10 - as against an upgrade from 9.04 to 9.10? Why and/or why not?

2) Given the fact that I have two HDDs, one has Windows/Ubuntu 9.04 and the other one has only Ubuntu 9.04 - what are the issues with either upgrading or doing a fresh install of 9.10 on just one of the HDDs (the root of this question lies in the fact that 9.10 moves to GRUB2)?

Of course, the best course of action will be to do a fresh install on both HDDs, but therein lies the real problem - of backing up all preferences, including the look and feel of the OS and system options, and then having to restore those in the new install. After doing that though, I am not sure whether the ext3 to ext4 will allow me to restore my preferences to what I am using right now.

Any help will be greatly appreciated.

Thanks,
DB

---

### Post by QIII on 2009-09-21
My recommendation would be a fresh install on your primary drive.  But that means you will have to live with restoring all of your preferences.
I say that because upgrading to Karmic will leave you with a "legacy" situation with regard to GRUB.  You can upgrade GRUB from legacy (there are tutorials for how to do it), but I don't know for sure at this point how well it really works.

GRUB2 (actually not 2.0, but something like 1.97 because it is currently a Beta) should, by the final release, be scripted to probe your OSs and automatically add them to GRUB2.

I say should...

I don't know if Alpha 6 does it right from a clean install because I haven't been able to get Alpha 6 to install from the September 17th iso, so I've had to the dist-upgrade route to get it to run.

I know that as of Alpha 5 you had to install os-prober, run it and then run update-grub2 to see your other OSs in the GRUB menu.

---

### Post by snowpine on 2009-09-21
A clean reinstall is always recommended. Historically, those who upgrade vs. fresh install seem to have a disproportionate share of difficulties. (Maybe Karmic will be the exception, but I doubt it with all the new features.)

ext4 alone is worth a fresh install. The performance difference has been noticable for me.

---

### Post by dhavalbbhatt on 2009-09-21
Thanks to both of you for your prompt responses. I do agree that a fresh install will be the best solution. However, it seems to me that GRUB2 (thanks QIII for pointing out the standard nomenclature) is going to be the bigger issue - if it can't multi-boot Windows and other OSs, then I am not sure how I can install 9.10 - maybe I should wait till GRUB2 has evolved a bit and allows multi-booting different OSs as an inherent task - and not as a work around that is being proposed by many others.

Opinions, thoughts?

Thanks,
DB

---

### Post by raymondh on 2009-09-21
> **dhavalbbhatt said:**
> Thanks to both of you for your prompt responses. I do agree that a fresh install will be the best solution. However, it seems to me that GRUB2 (thanks QIII for pointing out the standard nomenclature) is going to be the bigger issue - if it can't multi-boot Windows and other OSs, then I am not sure how I can install 9.10 - maybe I should wait till GRUB2 has evolved a bit and allows multi-booting different OSs as an inherent task - and not as a work around that is being proposed by many others.

Opinions, thoughts?

Thanks,
DB

Hi DB,

I have 2 HD's.  Currently, sda has a production version of Ubuntu with GRUB installed in its' MBR and is first to boot in BIOS.  Sdb has a "Karmic-to-be-tweaked" with Grub also installed in it's MBR.  When I am happy and Karmic is final, I plan to make sdb first to boot in BIOS and then use sda to start tweaking the next version ... so on and so on.

I plan to keep Karmic at it's current state (alpha) and then use the network to move if to final release.  If it borks then, I still have sda to come back to.

I also am using (and learning) aptonCD to move repos, apps, etc. to retain the same ones' I have during tweaking phase.  I also have a separate /home.  Lastly, most of my personal data is on a 3rd HD mounted to my ubuntu install.

Oh, and I actively use rsync (with grsync) and PING (to image my HD's).

EDIT : both HD's multi-boot windows XP (as back-up) as well as a virtualized XP (which I use all the time).

---

### Post by QIII on 2009-09-21
> **dhavalbbhatt said:**
> Thanks to both of you for your prompt responses. I do agree that a fresh install will be the best solution. However, it seems to me that GRUB2 (thanks QIII for pointing out the standard nomenclature) is going to be the bigger issue - if it can't multi-boot Windows and other OSs, then I am not sure how I can install 9.10 - maybe I should wait till GRUB2 has evolved a bit and allows multi-booting different OSs as an inherent task - and not as a work around that is being proposed by many others.

Opinions, thoughts?

Thanks,
DB

You can boot other OSs.  As I said, the os-prober issue in the install scripts should be resolved by the time of the final release.

As of Alpha 5, the fix was fairly simple.

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```As I said, that should happen automatically by the time of the final release.

---

### Post by bumanie on 2009-09-21
> it seems to me that GRUB2 (thanks QIII for pointing out the standard nomenclature) is going to be the bigger issue - if it can't multi-boot Windows and other OSs,Grub 2 (or as it is at present, 1.97 beta 3) boots other OSes fine. I am using it on both jaunty and karmic and it can boot windows without problems. It will take a bit to learn all Grub 2's ins-and-outs, but in the end it should be better than grub-legacy. By the way, the update to grub 2 works fine, I did it with jaunty - no problems at all. Don't worry about grub. I think your biggest decision will be whether to migrate to ext4 or not - it too seems stable as I am using it on jaunty in both 32 and 64 bit on different computers as well as on karmic. I did a fresh install and saved important /home files onto an external drive and then formatted with ext4. There are ways to upgrade to ext4 from ext3, but I believe there are some features missing by going the upgrade path.

---

### Post by dhavalbbhatt on 2009-09-22
Once again thanks guys for the inputs - this will definitely help in my decision making process.
bumanie - the ext4 is an easy decision for me, given the fact that i have been hearing that it is fairly stable now (as against in 9.04 release). 
QIII - thanks for sharing the os prober work around and the fact that it "should" be built into the 9.10 release. 
All in all, it looks like 9.10 should be a great release, will look forward to Karmic.

Thanks,
DB

---

### Post by presence1960 on 2009-09-22
> **snowpine said:**
> a clean reinstall is always recommended. Historically, those who upgrade vs. Fresh install seem to have a disproportionate share of difficulties. (maybe karmic will be the exception, but i doubt it with all the new features.)

ext4 alone is worth a fresh install. The performance difference has been noticable for me.

[size="7"]+1[/size]

---

### Post by slakkie on 2009-09-22
> **snowpine said:**
> A clean reinstall is always recommended.

ext4 alone is worth a fresh install. The performance difference has been noticable for me.

Clean installed is prefered for those not knowing how to do a propper upgrade IYAM.

That said, the ext4 bit for me would be the only reason to clean install Karmic. Grub to grub2 is pretty trivial. Although I don't dual boot so I can't say if it works well with other OS'es.

---

