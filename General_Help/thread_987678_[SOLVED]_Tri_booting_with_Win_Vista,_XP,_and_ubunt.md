---
title: "[SOLVED] Tri booting with Win Vista, XP, and ubuntu 8.10..."
date: 2008-11-19
forum: General Help
---

### Post by Jammanuser on 2008-11-19
Hi people! I've got a question to ask! i recently installed **Ubuntu 8.10** on top of my pre-installed **Vista**, on my Dell 1535 laptop, using **wubi-installer**, and now i want to add **XP** to the list, by shrinking my **Vista** partition to create more space, and then installing **XP** on the unalloted space! so my question is: can this be done without messing up my ubuntu installation?

Thanks to any and all honest answers!!!! 

-Jammanuser

P.S. oh, and one more thing! i couldn't get on the IRC #ubuntu channel for some reason!!!! i keep getting redirected to a channel called #ubuntu-proxy-users, when i'm not using a proxy, and i have no idea why it would think that i am!!! does anyone know what could be the problem??? Thanks!

---

### Post by caljohnsmith on 2008-11-19
Although you were probably all ready planning on doing it this way, I would highly recommend that you use Vista's Disk Management tool to shrink your Vista partition if you can. If you use any other type of partition editor, it can cause problems with Vista since Vista maintains its own partition table outside of the main partition table in the MBR (Master Boot Record). Also, shrinking the Vista partition shouldn't affect your Wubi install, so that should be fine.

But since you want to install XP after Vista and not the other way around (which is more ideal), I would recommend temporarily "hiding" the Vista partition before you install XP so that XP doesn't put its boot files in the Vista partition and mess up the booting process. After you install XP you can unhide the Vista partition, and then you can easily add XP as a boot option in your Vista's boot menu with a program called "[EasyBCD]("http://neosmart.net/dl.php?id=1")". 

If you would like me to help you hide/unhide your Vista partition, then first boot a Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal), and please post:
```
sudo fdisk -l
```
And we can work from there if you want. :)

---

### Post by Jammanuser on 2008-11-20
ok...thanks! actually i was planning to use the DISKPART app that's built into Vista to shrink the partition! i'm using the tutorial on dual booting Vista with XP (with Vista installed first) if that helps any! here's the link to that: [http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm](http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm)

according to the tutorial, the Win XP bootloader gets installed to the MBR, and Vista can no longer boot...and then i'm supposed to fix the corrupt bootloader with the System Recovery tool called 'Startup repair' on my Vista DVD that came with my computer. and **then** i'm supposed to use the EasyBCD app to setup my Vista bootloader to dual boot with XP! as for hiding my Vista partition...sounds nice, and might work better than what the person who wrote the tutorial is suggesting, but unfortunately i don't have a Ubuntu Live CD! i downloaded and installed ubuntu, using wubi-installer, from this link: [http://wubi-installer.org](http://wubi-installer.org)

Hope this info helps, and thanks for replying!

Looking forward to next comment...

---

### Post by caljohnsmith on 2008-11-29
Can you just burn a Ubuntu Live CD? The Wubi application downloads the Live CD ISO file into Windows if I remember correctly, so you may all ready have the ISO file still. Just remember when you burn the ISO file to disk, you burn it as an "image" to the CD, not as a data CD. You can always go to [www.ubuntu.com](www.ubuntu.com) to download a new Live CD ISO file if you need to. You'll need the Live CD if you want to do the hide/unhide partition trick, or at least that's probably the easiest way at this point.

---

### Post by Jammanuser on 2008-11-30
> **caljohnsmith said:**
> Can you just burn a Ubuntu Live CD? The Wubi application downloads the Live CD ISO file into Windows if I remember correctly, so you may all ready have the ISO file still. Just remember when you burn the ISO file to disk, you burn it as an "image" to the CD, not as a data CD. You can always go to [www.ubuntu.com](www.ubuntu.com) to download a new Live CD ISO file if you need to. You'll need the Live CD if you want to do the hide/unhide partition trick, or at least that's probably the easiest way at this point.

ok...thanks! i'm actually in the process of downloading the Ubuntu CD right now (sorry for not giving the info before)...didn't occur to me that i might already have the ISO! any chance u know **exactly** where to find it? i looked in my ubuntu folder on my C:/ drive, but didn't find anything that looked like the ISO! i would **much** prefer to burn the ISO that i have already (IF i have it!), than spend so much time downloading it from ubuntu site! i've already had a failed download twice, and had to start it all over again...from square 1, as it didn't pick up from where it left off, as i was hoping it would, but instead started from the beginning again! BOTH times! :( 

Thanks in advance! :guitar:

EDIT: oh! i forgot to mention two things! (1) i've already installed a program called 'InfraRecorder' to burn the ISO image to a CD, and (2) i've also downloaded and installed EasyBCD! just wanted to get those two things out of the way!

---

### Post by caljohnsmith on 2008-11-30
I think Wubi downloads the Ubuntu ISO to this directory:
```
C:\ubuntu\install\
```
Or you can look in your Wubi log file to find where Wubi downloaded the ISO to, and if you were using Windows XP it would be located at:
```
C:\Documents and Settings\<username>\Local Settings\Temp
```
So I'm guessing in Vista you would find yours at:
```
C:\Users\<username>\Local Settings\Temp
```
Good luck and let me know how it goes.

---

### Post by Jammanuser on 2008-11-30
> **caljohnsmith said:**
> I think Wubi downloads the Ubuntu ISO to this directory:
```
C:\ubuntu\install\
```
Or you can look in your Wubi log file to find where Wubi downloaded the ISO to, and if you were using Windows XP it would be located at:
```
C:\Documents and Settings\<username>\Local Settings\Temp
```
So I'm guessing in Vista you would find yours at:
```
C:\Users\<username>\Local Settings\Temp
```
Good luck and let me know how it goes.

thanks...i went to C:/ubuntu/install folder, but the only file in the there is named ".fuse_hidden0000000400000001"...? :confused: is that the ISO file, just with a different file name? it **is** the correct size, i.e. 699 MBs...could that be it? 

as for the Wubi log file, i tried looking for it in the dir u specified, but it turns out there's no such folder called "Local Settings' in Vista! :popcorn: 
there, however, **is** a Temp folder, only in a different location, i.e. instead of in C:/Users/<username>/Local Settings/Temp, its just in the main C: folder...right above the Ubuntu folder! i looked in there, but the only files in it were two irrelevant 'SrtTrail' documents, that appear to be some kind of system log...in one of them was recorded the disk scan that i recently ran...which i mentioned in my other forum topic about the booting problem i encountered trying to boot into Ubuntu again: [http://ubuntuforums.org/showthread.php?t=994123&highlight=CRC+error](http://ubuntuforums.org/showthread.php?t=994123&highlight=CRC+error)

Looking forward to ur reply... :lolflag:

---

### Post by caljohnsmith on 2008-11-30
You could download and install "[Virtual CloneDrive]("http://www.slysoft.com/en/virtual-clonedrive.html")", rename that .fuse_hidden0000000400000001 file to "maybe_Ubuntu.ISO", and try to mount it with Virtual CloneDrive. If it works and Virtual CloneDrive shows the Ubuntu CD files, then you could burn that to CD and it just might work fine. Have you searched Vista for any other ~700 MB files? You might find the ISO file that way too.

---

### Post by Jammanuser on 2008-11-30
> **caljohnsmith said:**
> You could download and install "[Virtual CloneDrive]("http://www.slysoft.com/en/virtual-clonedrive.html")", rename that .fuse_hidden0000000400000001 file to "maybe_Ubuntu.ISO", and try to mount it with Virtual CloneDrive. If it works and Virtual CloneDrive shows the Ubuntu CD files, then you could burn that to CD and it just might work fine. Have you searched Vista for any other ~700 MB files? You might find the ISO file that way too.

Thanks, and MUCH appreciation!!! :) i mounted that file with Virtual CloneDrive like u said, and it **was** the ISO! now i don't have to download it...i can just burn it right away to a CD, and i'll have my Ubuntu LiveCD!!! yay! :) 

as soon as i have done that, and hopefully fixed my Ubuntu boot problem first using the same CD, i'll then run that 'sudo fdisk -l' command like u said, and then post the output of the terminal **here** in this thread, and we can work from there, like u said, hopefully sucessfully hiding the Vista partition when i dual (i mean TRIPLE!) boot my computer with XP!

Thanks a lot!

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-01
> **caljohnsmith said:**
> 

If you would like me to help you hide/unhide your Vista partition, then first boot a Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal), and please post:
```
sudo fdisk -l
```
And we can work from there if you want. :)

ok...so i ran that "sudo fdisk -l" command like u said, and this is the output that i obtained:

```
ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x3c5a8d58


Device Boot Start End Blocks Id System

/dev/sda1 1 5 40131 de Dell Utility

/dev/sda2 6 1280 10240000 7 HPFS/NTFS

/dev/sda3 * 1280 38914 302290037+ 7 HPFS/NTFS

ubuntu@ubuntu:~$
```

Looking forward to ur reply...

:popcorn:

Jammanuser

---

### Post by caljohnsmith on 2008-12-01
It looks like you still need to shrink Vista and create a partition for XP, true? If so, then if you boot into Vista, open Windows Explorer, right-click "my computer", and select "management" (I think that's right), then you can try to use Vista's Disk Management to shrink the Vista partition. If for some reason Vista won't let you shrink its partition, then you could use Ubuntu's partition editor to shrink Vista, but then you would need a Vista Install or Recovery CD to repair Vista's partition table afterwards. Do you have a Vista Install/Recovery CD? See if you can use Vista's disk management first to shrink Vista, and let me know how that goes.

---

### Post by Jammanuser on 2008-12-01
> **caljohnsmith said:**
> It looks like you still need to shrink Vista and create a partition for XP, true? If so, then if you boot into Vista, open Windows Explorer, right-click "my computer", and select "management" (I think that's right), then you can try to use Vista's Disk Management to shrink the Vista partition. If for some reason Vista won't let you shrink its partition, then you could use Ubuntu's partition editor to shrink Vista, but then you would need a Vista Install or Recovery CD to repair Vista's partition table afterwards. Do you have a Vista Install/Recovery CD? See if you can use Vista's disk management first to shrink Vista, and let me know how that goes.

yes! i still need to shrink Vista, and create a partition for XP! :) i also have a Vista Install CD...i'll let u know if what u suggested works!

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-01
ok...so there's 3 partitions listed in the Computer Management app! so which one do I shrink?

Looking forward to ur reply... :)

---

### Post by Jammanuser on 2008-12-01
here's a screenshot of it, so u can see for urself and figure it out! :)

---

### Post by caljohnsmith on 2008-12-02
You would want to shrink the 288 GB Vista "C:" partition, or the second partition listed in that screenshot. Let me know how that goes.

---

### Post by Jammanuser on 2008-12-02
> **caljohnsmith said:**
> You would want to shrink the 288 GB Vista "C:" partition, or the second partition listed in that screenshot. Let me know how that goes.

ok...thanks!!! that's what i figured...i just wanted to make sure! 

Cheers! :guitar:

-jammanuser

P.S. once i've shrunk it (which might be a while from now, i might add!), and installed XP as an additional OS, i'll come back here and let u know if it works! hope it does! ):P

EDIT: WAIT!!! i just realized i was forgetting something when i wrote that...u mentioned hiding/unhiding the Vista partition...how can that be done? looking forward to ur reply...

---

### Post by caljohnsmith on 2008-12-02
Once you get Vista shrunk and have created a new NTFS partition for XP with the freed space, go ahead and post again:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by Jammanuser on 2008-12-02
> **caljohnsmith said:**
> Once you get Vista shrunk and have created a new NTFS partition for XP with the freed space, go ahead and post again:
```
sudo fdisk -lu
```
And we can work from there.

ok...cool! :D

Thanks!

EDIT: i **assume** that that is with the Ubuntu CD, as well, correct? or can i run the command in my Windows Command Prompt? Looking forward to ur reply...

---

### Post by Jammanuser on 2008-12-05
Actually...since my last post, caljohnsmith, i've changed my mind about how to triple boot my computer! ;) since then, i have found and decided to use a partitioning program called [BootIt NG]("http://www.terabyteunlimited.com/downloads/bootitng.pdf") to first partition my hard drive, and then install Windows XP, and also now Ubuntu 8.10 (since i've been having problems with my wubi install, i have decided to uninstall wubi, and instead install Ubuntu 8.10 on a **separate** partition!)...the program, i just learned, can also hide/unhide partitions as well...so i no longer need to use either Vista's Computer Management tool to shrink the partition, **nor** use the Ubuntu Desktop CD to hide/unhide that partition...if i understood right, that is, about how u planned to help me hide the Vista partition, using the Ubuntu CD! ;) 

So bottom line: I no longer need ur help (i THINK...don't take me TOO seriously on that!;)) in hiding the Vista partition...however you're welcome to help if u want...since i'm new to BootIt NG, i **could** use some helpful pointers from someone who's used it, and managed to successfully setup dual boots, triple boots, etc.

Cheers! ;)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
Ok...so i'm reading the BootIt NG manual right now...and i just got to a place, where it mentioned all the different filesystems it works on...and NOWHERE in the manual do i see whether or not it supports ext3 format or not! so i'm wondering if creating a partition for Ubuntu will work with this program...? ;)

So far, its only mentioned these filesystems: FAT, FAT32, NTFS, Ext2fs, and ReiserFS

Does anyone have any idea whether or not the program supports ext3 filesystem or not? ;)

Thanks in advance! :)

-jammanuser

:D

---

### Post by caljohnsmith on 2008-12-06
Just curious, but why do you especially want to use BootIt NG to partition your drive? I'm not saying it wouldn't work, but it is a commercial program when there is Ubuntu's gparted partition editor that will do the same thing for free. You can use gparted to hide partitions too, and of course it can make an ext3 partition. It's up to you though.

---

### Post by Jammanuser on 2008-12-06
> **caljohnsmith said:**
> Just curious, but why do you especially want to use BootIt NG to partition your drive? I'm not saying it wouldn't work, but it is a commercial program when there is Ubuntu's gparted partition editor that will do the same thing for free. You can use gparted to hide partitions too, and of course it can make an ext3 partition. It's up to you though.

Well...because I think BootIt NG has more options to create partitions! and just fyi...i'm using the 30-day **free** trial right now, and once i've got my computer successfully setup, I'll probably remove the program, **without** purchasing it! ;)

as for Gparted...i may use that for creating the ext3 partition for Ubuntu 8.10, if I find out that BootIt NG does **indeed** not support that filesystem! But as for XP, I would rather use something that's made mainly for Windows (such as BootIT NG) to create a partition for it, then to use Gparted for that! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
Is Gparted already on my Ubuntu Desktop CD, or do I have to download it first, and install it?

Looking forward to ur reply... ;)

-jammanuser

:D

---

### Post by caljohnsmith on 2008-12-06
After booting your Live CD just go to System > Admin > Partition Editor. Gparted shouldn't overwrite your Windows boot loader as long as you don't format the Windows partition; also, to my knowledge gparted doesn't change any of the boot code in the MBR either for what you are doing. And to answer your latest question, "e2fsprogs" is installed by default I think so you shouldn't have any problems. :)

---

### Post by Jammanuser on 2008-12-06
And **also**, if I use Gparted, doesn't it overwrite my Windows bootloader?

Looking forward to ur reply... ;)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
> **caljohnsmith said:**
> After booting your Live CD just go to System > Admin > Partition Editor. :)

ahh...ok! Thanks! my above question still stands... ^ 

Cheers! ;)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
> **caljohnsmith said:**
> After booting your Live CD just go to System > Admin > Partition Editor. Gparted shouldn't overwrite your Windows boot loader as long as you don't format the Windows partition; also, to my knowledge gparted doesn't change any of the boot code in the MBR either for what you are doing. :)

ok...cool! Thanks! :) one more question: If i use Gparted to create the ext3 partition...will i also need to have "e2fsprogs"? I'm looking at the Gparted website right now, and it says that the required software for that is "e2fsprogs"!

Looking forward to ur reply... :guitar:

-jammanuser

:D

EDIT: or is the software already included on the Ubuntu Desktop CD???

---

### Post by Jammanuser on 2008-12-06
> **caljohnsmith said:**
> After booting your Live CD just go to System > Admin > Partition Editor. Gparted shouldn't overwrite your Windows boot loader as long as you don't format the Windows partition; also, to my knowledge gparted doesn't change any of the boot code in the MBR either for what you are doing. And to answer your latest question, "e2fsprogs" is installed by default I think so you shouldn't have any problems. :)

ok...cool! Thanks for all ur help! :D

Cheers! ;)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-08
hmm...it says on the sticky thread about upgrading the Wubi install to a dedicated partition:

> also make sure you have a swap partition of greater size than your RAM memory, in addition to the partition you will install Linux to ([COLOR="Red"]the filesystem type for the main partition doesn't matter, it'll be made ext3 anyhow[/COLOR], just make sure the swap partition is formatted as swap or it won't be used). If you do, just move on to the next section.

So it sounds like I **could** use BootIt NG to create the partition for Ubuntu...since it'll be made ext3 anyway, by LVPM, when it transfers the Wubi install to a dedicated partition, according to the thread poster!

i may not have to use Gparted at all...which is good, because i think i remember reading in the BootIt NG manual, that if at install of BootIT NG, u choose to allow more than 4 primary partitions (which i did!), than ur supposed to use only BootIT NG to create partitions, as long as it is installed, or it will somehow mess up boot setup, and make ur computer unable to boot into Windows!

So i'm glad then that i can use BootIT NG, after all, to create the partition for Ubuntu, not just the one for XP! :guitar:

Cheers! :D

-jammanuser

):P

---

### Post by Jammanuser on 2009-01-04
Tri-boot successful. :guitar: I got it working some days ago...but forgot to post here until just now. :) I now have Vista, XP, and Ubuntu 8.10 all working and booting from both BootIT NG itself, and the Vista bootloader itself. :D Thanks for all your help, caljohnsmith! 

Cheers! :popcorn:

-Jam man

:guitar:

---

