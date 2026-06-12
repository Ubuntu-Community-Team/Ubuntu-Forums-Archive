---
title: "How to install Ubuntu from Hard Disk?"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by hcchen on 2009-06-02
Install Windows from Hard Disk is easy. Copy the CD/DVD to a folder and then run the setup or install works fine. When I try to install Ubuntu from Hard Disk I have got blocked at an error message,

[FONT=courier new][!!] Detect and mount CD-ROM
Incorrect CD-ROM detected
The CD-ROM Drive contains a CD which cannot be used for installation.
Please insert a suitable CD to continue with the installation.
[Continue][/FONT]

Please help !

You can reproduce the problem by below steps, (see [very detail steps]("http://sites.google.com/site/guitardingdong/install-ubuntu-904-from-hdd"))
1. Create a 4G hard disk space (on a VirtualBox virtual machine)
 2. run cfdisk to create 3 partitions. They are,
 [FONT=courier new]    hda1. Linux partition 2G reserved to be the target partition. [/FONT]
 [FONT=courier new]    hda2.1G ext2 partition to be the installation source. [/FONT]
 [FONT=courier new]    hda3. other hundreds Mega spaces reserved for linux swap partition.[/FONT]
 3. format the  /dev/hda2  
 4. copy Ubuntu 904 Alternate CD to /dev/hda2
5. boot up to GRUB and start Ubuntu installation by below 3 GRUB commands,
[FONT=courier new]   kernel (hd0,1)/install/vmlinuz[/FONT]
      [FONT=courier new]     initrd (hd0,1)/install/initrd.gz[/FONT]
      [FONT=courier new]     boot
[/FONT]6. Installer works !
7. But the installation got blocked at the error message box mentioned above. 

I need help here.

---

### Post by logos34 on 2009-06-02
this way works:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by hcchen on 2009-06-04
Yeah thank you very much. [That page]("https://help.ubuntu.com/community/Installation/FromLinux") (I did the procedure 1 and procedure 2 for Alternate CD) helps a lot (tho' [still failed]("http://sites.google.com/site/guitardingdong/install-ubuntu-904-from-hdd") after all). I can really start installing from "ubuntu-8.04.2-alternate-i386.iso" on my hard disk, plus the installer ...
2008/10/26  14:03         6,348,557 initrd.gz
2008/10/26  14:03         2,244,272 vmlinuz
That I downloaded from [Ubuntu archive]("http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/").

As mentioned, next failure is at :[INDENT][!!] Load installer components from an installer ISO. 

Failed to load installer componet. 

Loading libc6-udeb failed for unknown reasons. Aborting.
[/INDENT]Exactly same problem happens on my old ThinkPAD and VirtualBox emulated virtual machine on another modern computer. Versions mismatch? According to the dates of above files I think they are match. Then why same problem happens on totally different machines?

---

### Post by hcchen on 2009-06-05
Now I have resolved the above problem. Download the correct vmlinuz and initrd.gz is the solution. Details are,

2008/06/20  05:48         6,222,092 initrd.gz
2008/06/20  05:48         1,920,472 vmlinuz

---

