---
title: "BusyBox error as well as a question on RAID"
date: 2008-07-12
forum: General Help
---

### Post by McTwist724 on 2008-07-12
Hola! I recently built a new pc and have since been having problems installing Ubuntu 8.04. First off, I hate to make a new thread about BusyBox as there are quite a few already here and it seems that a lot of people are having problems with it.

With that being said, I can get Ubuntu to run/install if I go into my BIOS and change my drives from IDE to RAID. However, my drives are not set up as a RAID device and Ubuntu will not run/install if my drives are configured as IDE. Now to my question, even though my drives are SATA, why was the default BIOS setting IDE (even though my HDDs work perfectly)? What exactly is RAID? Is it wise to be running under RAID? If so, why and how?

Possible need to know info:

ASUS P5Q-E motherboard
Intel E8400 CPU
Radeon HD4870 video card
Hitachi and Seagate HDDs
Windows Vista Ultimate (trying to dualboot with Ubuntu)

I thought maybe my .ISO was corrupted, so I downloaded another. I burned a couple disks at 2x and the same problem. I can't even run the checksum to see if my .ISO is 100% because it takes me to BusyBox.

I will do anything I can to fix this because I do not want to run in Windows. The only reason I have Windows is for games.

What should I do? Wipe the drive and try again?

thanks

peace

---

### Post by Aearenda on 2008-07-12
The 'RAID' setting is usually a misnomer - it means that the SATA drives are using the native AHCI BIOS (which is slightly faster). When set to IDE mode they pretend to be IDE drives.

You can generally get Ubuntu to install using IDE mode with the all_generic_ide kernel parameter as detailed here: [http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15)

EDIT: I realised I haven't answered all your questions. RAID stands for 'Redundant Array of Inexpensive Disks' and it is designed to let you use ordinary disk drives in various fault-tolerant ways. This is useful for businesses but rarely so for home users. The BIOS setting marked 'RAID' probably offers to set up the drives this way, but does not REQUIRE the drives to be fault tolerant. It should really be named 'SATA native mode', and it IS wise to use it with Ubuntu (slightly faster) but not if you are dual booting with an existing Windows installation that uses IDE mode.

The default setting is IDE because Windows XP does not know how to use SATA at installation time. I expect Vista does. XP needs an extra driver disk to be able to install in SATA mode.

---

### Post by McTwist724 on 2008-07-12
Ok I see. I also have an option of AHCI. Which should I choose?

---

### Post by Aearenda on 2008-07-12
AHCI is the native SATA mode, but without the RAID option. Many BIOSes don't have a separate AHCI mode, they just have RAID or IDE.

I would use AHCI for single-booting Ubuntu, and IDE if you are dual-booting.

Also, note I added more details to my post while you were replying. Sorry about that!

---

### Post by McTwist724 on 2008-07-12
Ok, well I can't use IDE for dualbooting because Ubuntu seems to not like it and takes me to BusyBox. The only way I found to get around this is to simply change my settings to RAID and then continue the installation, but this just doesn't seem right. What do you think I should do? I'm kinda stuck and I am getting sick of Vista. I mean it's not bad and all, but it's just not Ubuntu.

---

### Post by Aearenda on 2008-07-13
That's what the all_generic_ide flag is for at boot time with Ubuntu - the link I gave you earlier on - it should make Ubuntu start without the busybox error, after the installation is done, if you add it to /boot/grub/menu.lst.

---

### Post by McTwist724 on 2008-07-13
Thank you very much. All is well. =)

---

### Post by shom on 2008-07-13
It's a miracle, I have just failed to install ubuntu and this fresh thread helped me to solve my problem by using all_generic_ide flag.
Nevertheless, I can't figure out why can't I use the sata mode and I have to use the IDE mode in a pure linux installation.   
Mother board Gygabyte GA-73PVM-S2H.

---

### Post by Aearenda on 2008-07-13
It's most likely because the BIOS reports the drives to the operating system in a different order depending on whether you are booting from the CD or the hard disk, or indeed which hard disk you are booting from. Busybox appears when the initial system can't find the root filesystem.

That said, there are many possible reasons for this, and as I don't know your motherboard I'll leave others to comment.

---

