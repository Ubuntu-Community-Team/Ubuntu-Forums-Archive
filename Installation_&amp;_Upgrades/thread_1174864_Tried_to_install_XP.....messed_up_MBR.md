---
title: "Tried to install XP.....messed up MBR"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2009-05-31
I searched under a number of different terms, I'm very surprised I couldn't find a solution to this.

I reinstalled my entire system on 9.04 EXT4 yesterday and everything worked perfectly. In the process I made a FAT32 partition for Windows XP and today I actually tried installing Windows. When I chose the FAT32 partition, it told me it needed to write to the MBR but there was no Windows compatible partition on it. I deleted the FAT32 partition, created a new partition and it still said the same thing, it can't write to the MBR because it's not a Windows compatible partition. So if you can fix this for me it'd be great but in the meantime, I have another issue....

When I try to reboot the machine into Ubuntu again, it says there's an error loading the operating system right after POST so I know that Windows must have messed up my managed boot record.

Any solution to either?

---

### Post by alastair on 2009-05-31
You can re-write the MBR again by booting with an Ubuntu CDROM and fixing the MBR.

Have a look here :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Maheriano on 2009-05-31
That looks easy enough, I'll try that. So what about installing Windows, is there a way to fix it so XP will install? Ever hear of it complaining about that and not installing?

---

### Post by presence1960 on 2009-05-31
> **Maheriano said:**
> That looks easy enough, I'll try that. So what about installing Windows, is there a way to fix it so XP will install? Ever hear of it complaining about that and not installing?

why are you using FAT32? Try NTFS.

---

### Post by Maheriano on 2009-06-01
> **presence1960 said:**
> why are you using FAT32? Try NTFS.

I thought the same thing but when I used the 9.04 LiveCD to create the partitions, it didn't give me an option for NTFS. The only Microsoft compatible partition type was FAT32.

---

### Post by presence1960 on 2009-06-01
something is not right there. Try downloading the iso for garted Live CD and burn it as an image to disk. You can then boot off of this and partition your drives. When finished reboot and try install. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by cmay on 2009-06-01
> **Maheriano said:**
> I searched under a number of different terms, I'm very surprised I couldn't find a solution to this.

I reinstalled my entire system on 9.04 EXT4 yesterday and everything worked perfectly. In the process I made a FAT32 partition for Windows XP and today I actually tried installing Windows. When I chose the FAT32 partition, it told me it needed to write to the MBR but there was no Windows compatible partition on it. I deleted the FAT32 partition, created a new partition and it still said the same thing, it can't write to the MBR because it's not a Windows compatible partition. So if you can fix this for me it'd be great but in the meantime, I have another issue....

When I try to reboot the machine into Ubuntu again, it says there's an error loading the operating system right after POST so I know that Windows must have messed up my managed boot record.

Any solution to either?

you have to install windows first. then ubuntu. 
you can not install windows after ubuntu or any other system.

---

### Post by presence1960 on 2009-06-01
> **cmay said:**
> you have to install windows first. then ubuntu. 
you can not install windows after ubuntu or any other system.

**Absolutely not true**

if you don't believe me see this : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

You can indeed install Linux first, then Windows. But since Windows will overwrite GRUB you need to Reinstall GRUB after installing Windows.

---

### Post by cmay on 2009-06-01
> **presence1960 said:**
> **Absolutely not true**

if you don't believe me see this : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

You can indeed install Linux first, then Windows. But since Windows will overwrite GRUB you need to Reinstall GRUB after installing Windows.

thanks for the correction. i did not use windows since ME and its a long time ago. it used to be that however. 

good link also. i bookmarked in case i run into this question again.

---

### Post by presence1960 on 2009-06-01
ME, that was a while ago. ME was a joke too! :p

---

### Post by Maheriano on 2009-06-02
Well, I put in the LiveCD and reinstalled Grub, I can now boot into Ubuntu! Thanks guys! Only problem is I didn't watch it boot to see if Windows was listed in Grub or not, I'll check it again when I get home.

---

