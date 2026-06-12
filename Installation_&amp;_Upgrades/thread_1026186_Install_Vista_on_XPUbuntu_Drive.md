---
title: "Install Vista on XP/Ubuntu Drive"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by chris_sj on 2008-12-30
I currently have a drive I loaded XP on and later installed Ubuntu.  Ubunto installed a boot manager so I can choose either XP or Ubuntu when starting.  I now want to install Vista, can I just create another primary parition, install vista to this then redo the Ubunto installation so I get the proper boot manager again.  I would prefer not having to overwrite my Ubunto installation , I just want to re-create the boot so I can choose between XP, Vista, Ubunto.

Thanks,
Chris

I ran gparted from my SystemRescueCD and it showed the following layout:

/dev/sda1               fat16 
/dev/sda2               ntfs          boot 
/dev/sda3               extended      lba 
  /dev/sda6             ext3 
  /dev/sda7/linux-swap 
  /dev/sda5             fat32

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
You really don't want Vista man. My PC came with it and I tried to keep it for gaming but it finally got so frustrating that I only have Ubuntu now until I can get a copy of XP. But if you do really want to try it then all you'd have to do is reinstall grub... no need to reinstall the OS.

oh yeah... [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by logos34 on 2008-12-30
> **Sin@Sin-Sacrifice said:**
> You really don't want Vista man. My PC came with it and I tried to keep it for gaming but it finally got so frustrating that I only have Ubuntu now until I can get a copy of XP. But if you do really want to try it then all you'd have to do is reinstall grub... no need toows[/url]

+1 

If you do decide to add vista, it'll place the the boot manager/boot files in the pre-existing active windows partition--i.e. XP C: drive, sda2--as well as overwrite grub on the MBR.  So after restoring grub you can continue booting XP entry, which will now give you a choice of vista or xp

---

