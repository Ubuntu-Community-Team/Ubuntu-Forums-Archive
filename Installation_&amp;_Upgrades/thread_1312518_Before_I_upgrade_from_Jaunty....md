---
title: "Before I upgrade from Jaunty..."
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by jauntybluefish on 2009-11-03
How painful is the upgrade likely to be?

I have read so many conflicting reports with different experiences.

The reason i am asking is that I reinstalled Jaunty a week ago and really had a good bash at sorting out all the previous reasons why I reverted back to XP
I got Skype going on the older version 2.00.72 and that had been a major obstacle/dealbreaker before.
I got wireless going on my Broadcom 4318 chip. 
I got my desktop working the way i wanted and all the apps installed that I needed.

In short i am worried that an upgrade now, will mean that all the work I have done will need to be done again.
Is it worth while doing it in your opinions?
Will the wireless need to be dealt with again after the upgrade?
Is it better for me to clean install or upgrade through Synaptic. I thought the upgrade would be better because I have a pretty clean ext3 drive to begin with.

I am currently downloading the LiveCD, in preparation for the possibility of having Karmic installed.

I appreciate any comments.
Thanks
Andy

---

### Post by tommcd on 2009-11-03
> **jauntybluefish said:**
> 
Is it better for me to clean install or upgrade through Synaptic. I thought the upgrade would be better because I have a pretty clean ext3 drive to begin with.
IMO a clean install is always safer and less likely to cause problems than doing a dist-upgrade. A clean install is the best way to avoid the problems that often come with a dist-upgrade. Configuring Ubuntu after installing gets easier the more you do it. I can install Ubuntu in less than 20 minutes. It then takes me another hour (at the most) to set things up the way I want them and install the programs that I use. I don't consider this to be a problem at all.
If you have a separate home partition then all your data is safe. If you don't have a separate home partition, this would be a good time to repartition and create a separate home.
> **jauntybluefish said:**
> 
I am currently downloading the LiveCD, in preparation for the possibility of having Karmic installed.
Andy
This is a good move. If anything goes wrong with the dist-upgrade, you can just do a clean install with the CD you will prepare before you do the upgrade.
Be sure to read the Karmic release notes for possible issues:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)
See this for doing the dist-upgrade:
[http://howtoforge.com/how-to-upgrade-ubuntu9.04-jaunty-jackalope-to-9.10-karmic-koala-desktop-and-server](http://howtoforge.com/how-to-upgrade-ubuntu9.04-jaunty-jackalope-to-9.10-karmic-koala-desktop-and-server)
and:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)

---

### Post by dhavalbbhatt on 2009-11-03
> **jauntybluefish said:**
> How painful is the upgrade likely to be?

I have read so many conflicting reports with different experiences.

The reason i am asking is that I reinstalled Jaunty a week ago and really had a good bash at sorting out all the previous reasons why I reverted back to XP
I got Skype going on the older version 2.00.72 and that had been a major obstacle/dealbreaker before.
I got wireless going on my Broadcom 4318 chip. 
I got my desktop working the way i wanted and all the apps installed that I needed.

In short i am worried that an upgrade now, will mean that all the work I have done will need to be done again.
Is it worth while doing it in your opinions?
Will the wireless need to be dealt with again after the upgrade?
Is it better for me to clean install or upgrade through Synaptic. I thought the upgrade would be better because I have a pretty clean ext3 drive to begin with.

I am currently downloading the LiveCD, in preparation for the possibility of having Karmic installed.

I appreciate any comments.
Thanks
Andy

Each install of Ubuntu is different, in my opinion. You should really run the LiveCD to figure out how the upgrade will perform on your hardware. The other thing that I'd ask is - why do you want to "upgrade"? If Jaunty is running fine, I don't necessarily see a reason for you to "upgrade". Having said that, if you want to keep all your settings, then you should "upgrade" (through Update Manager under System -> Admin) and not perform a fresh install - understand though that an upgrade will not change your file system from ext3 to ext4 (assuming you have ext3 right now with Jaunty) and your GRUB 0.97 might not change to GRUB 2.0 (this, I am not sure of). However, there are how-tos on how to do that manually, even within Jaunty.

In the past, I would have said that a fresh install is better than an "upgrade", but seeing the results of the installation/upgrade survey posted here, it seems that more people have had success with the "upgrade" option. I am sure that has something to do with the actual installation CD and not with the OS itself (I have had issues with the CD myself and have seen numerous posts with problems related to the CD and not with the OS itself).

---

### Post by tommcd on 2009-11-03
See this page from the Ubuntu wiki for how to fully upgrade to grub2 when doing the upgrade:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
EDIT: Here is another comprehensive tutorial for grub2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Go ahead and do the dist-upgrade. Read the links I posted first though. If the upgrade works, then all is well. If you develop problems that you are unable to fix, then do a clean install from the Karmic CD you will prepare (and test) before you do the upgrade.

---

