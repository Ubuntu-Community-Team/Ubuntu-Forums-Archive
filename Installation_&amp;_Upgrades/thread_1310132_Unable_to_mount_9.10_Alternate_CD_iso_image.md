---
title: "Unable to mount 9.10 Alternate CD iso image"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by eskay_karthik on 2009-11-01
I am trying to upgrade from 9.04 to 9.10 using the Alternate CD.
The command:

```
sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom0
```

gives the error:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Moreover, dmesg | tail gives:

```
[ 4072.109146] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 4447.722400] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4447.722465] ISOFS: changing to secondary root
[ 4447.722496] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 4483.972717] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4483.972785] ISOFS: changing to secondary root
[ 4483.972828] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 4707.393616] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4707.393681] ISOFS: changing to secondary root
[ 4707.393710] isofs_fill_super: root inode is not a directory. Corrupted media?

```

I have no clue what to do.

Please help.

eskay

---

### Post by wilee-nilee on 2009-11-01
I believe you have to boot the disc and somewhere in that install process is upgrade rather then overwrite option. I assume your aware of this method will not get you grub2 and ext4 installed which can be done later but it shouldn't be done without backing up your important stuff so maybe just doing a backup and a clean install might be a better option if you want the new grub and extension. Your description is you can't mount sounds like your trying to run it in a running environment.

---

### Post by DustofDust on 2009-11-01
are you sure the path is correct and is it cdrom or cdrom0

i used at recovery boot
[http://ubuntuforums.org/showpost.php?p=8201026&postcount=23](http://ubuntuforums.org/showpost.php?p=8201026&postcount=23)
> alt f2 for another bash, because it dont let you escape.
sudo mount -o loop ~/path/ubuntu-9.10-alternate-i386.iso /mnt/cdrom

and it worked for me. you need the correct path where it is from the root directory!

---

### Post by wilee-nilee on 2009-11-01
> **DustofDust said:**
> are you sure the path is correct and is it cdrom or cdrom0

i used at recovery boot
[http://ubuntuforums.org/showpost.php?p=8201026&postcount=23](http://ubuntuforums.org/showpost.php?p=8201026&postcount=23)


and it worked for me. you need the correct path where it is from the root directory!

 So is the use of the alternative done on a running system or a boot from cd.

---

### Post by DustofDust on 2009-11-01
> **wilee-nilee said:**
> So is the use of the alternative done on a running system or a boot from cd.

on a running system. i had the problem with x and graphics driver. i had the live cd in the cdrom but it was not recognized and complained about a media change. so i had to mount the iso on the hd to install the drivers.

the reason why i used the alternate iso was, because i didnt want to download all the packages through the slow downloads and used the quicker torrent download. i used the simple way not to burn it and just mount the iso and this i needed todo also when i had the other problems. 1st with the gui and later at crapped x with commandline.

---

### Post by wilee-nilee on 2009-11-01
> **DustofDust said:**
> on a running system. i had the problem with x and graphics driver. i had the live cd in the cdrom but it was not recognized and complained about a media change. so i had to mount the iso on the hd to install the drivers.

the reason why i used the alternate iso was, because i didnt want to download all the packages through the slow downloads and used the quicker torrent download. i used the simple way not to burn it and just mount the iso and this i needed todo also when i had the other problems. 1st with the gui and later at crapped x with commandline.

 Thanks for the information I know a person can install with a iso by mounting it I guess it makes sense that this could be done with a upgrade via the alternative. Thank goodness you and the people who have to side step compatibilities to get it to work know how to do it.

---

### Post by DustofDust on 2009-11-01
> **wilee-nilee said:**
> Thanks for the information I know a person can install with a iso by mounting it I guess it makes sense that this could be done with a upgrade via the alternative. Thank goodness you and the people who have to side step compatibilities to get it to work know how to do it.

i didnt know it, i had to boot with the live cd and look after the informations. i learned it also the hard way when i needed it... ;)

---

### Post by wilee-nilee on 2009-11-01
> **DustofDust said:**
> i didnt know it, i had to boot with the live cd and look after the informations. i learned it also the hard way when i needed it... ;)

 One good thing about the hard way is your brain saves that information in the long term memory, rather then short term.

---

### Post by DustofDust on 2009-11-01
> **wilee-nilee said:**
> One good thing about the hard way is your brain saves that information in the long term memory, rather then short term.

it saves where to look at and "there was something" but not the details if you are not a professional it person. you get an overview how it works in general but if you have a problem once a year and you dont know if it is the same problem or libs and so on are changed, you need to look after the solution.

what is really essential:

always have an approved working livecd, to get into the internet to search for help, or another working pc.

have your account for help forum also not on the pc in case the pc does not work. the save function of the browser is nice for everyday but not if you boot with a livecd and without that stored account infos.

;)

---

### Post by chimiasanchi on 2009-11-06
[http://help.ubuntu.com/community/IntrepidUpgrades#AlternateUpgrade]("http://help.ubuntu.com/community/IntrepidUpgrades#AlternateUpgrade")

---

