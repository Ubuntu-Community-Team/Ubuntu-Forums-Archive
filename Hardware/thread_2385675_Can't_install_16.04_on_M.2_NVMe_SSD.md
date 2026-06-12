---
title: "Can't install 16.04 on M.2 NVMe SSD"
date: 2018-02-23
forum: Hardware
---

### Post by David4321 on 2018-02-23
Not sure if this should be in hardware or installation, might have to be moved.
Both this computer and M.2 drive are completely new to me, never worked with an M.2 before.
Very familiar with Ubuntu, done many installs.

Hardware: 
              ASUS ROG GL703VD-WB71
Samsung 960 EVO NVMe SSD 500gb

Original OS is Win 10, I just removed that drive and set it aside.
I added a 2tb HDD and the Samsung. ASUS assures me the board is capable for NVMe, and bios sees drive.

I've now tried installing 16.04 & 14.04 from ISO via USB made with UNetbootin, and from external optical drive with disc I burned.
I tried different USB sticks, with ISO's downloaded from 3 different sources, and with data drive pulled.

First attempts installer froze with progress meter stopping before reaching install sequence.
Later I started getting crashes with long error screens in red. (I have photos but couldn't seem to insert them)

Maybe there is some issue with the drive or the computer (working fine under windows on HDD), or maybe I just don't know how to install to M.2, or maybe bios setting issue? Thanks for any help.

---

### Post by vasa1 on 2018-02-23
> **David4321 said:**
> ...(I have photos but couldn't seem to insert them)
...
Click on the paperclip icon to initiate an upload from your computer to the forum. If you don't see that icon, click on "Go Advanced" just below the posting area.

---

### Post by David4321 on 2018-02-23
Here's an update: I pulled the M.2 drive, reduced the data partition on my data drive, made a new OS partition (ext4), and tried install again from external DVD drive, disc burned from fresh download from main Canonical 16.04 page.

I got this:

[ATTACH=CONFIG]278686[/ATTACH]


Here's one from yesterday:

[ATTACH=CONFIG]278687[/ATTACH]

btw, I did know how to add these, maybe browser was glitching.

---

### Post by oldfred on 2018-02-24
Please attach screen shots as vasa1 suggested. It is the paperclip icon in the Forum's advanced editor.

       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 
    
It looks like your system also has nVidia. You probably need nomodeset until you can boot install and add nVidia driver from repository. Do not install directly from nVidia.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

This thread with older Ubuntu needed additional boot parameters.
       
 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)

---

### Post by QIII on 2018-02-24
What oldfred said.

I assure you that an NVMe drive can be used for installing the OS.  From blkid on my machine:

```
/dev/nvme0n1: PTUUID="<blah blah>" PTTYPE="gpt"
/dev/nvme0n1p1: ....
```

My boot device on this machine is the M.2 NVMe drive (a Samsung Evo 960).

---

### Post by David4321 on 2018-02-27
Thanks for all that. I stopped trying with 16.04 and went to 17.10, seemed like there was a conflict with the graphics card. Yes, I needed nomodeset, that got the installer running, but I haven't got it in yet. I changed the plan and decided to make 2 partitions on the NVMe and dual boot Windows 10 and 17.10. I got windows in, still struggling with Ubuntu, but that's a new issue, the post is here: [https://ubuntuforums.org/showthread.php?t=2385941&p=13743702#post13743702](https://ubuntuforums.org/showthread.php?t=2385941&p=13743702#post13743702)

---

