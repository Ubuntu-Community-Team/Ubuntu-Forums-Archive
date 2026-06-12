---
title: "Nothing but a black screen Gnu Grub... (Wubi)"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by SBloke on 2009-11-09
Hi all,

In an attempt to start learning more about Ubuntu I installed 9.10 using Wubi I'm having a slight problem:

If I select the Ubuntu option in the boot menu I get a black screen (Console-like) with header "Gnu Grub 1.97 beta" 

[Minimal BASH-like....... 

...]

sh:grub>


And nothing more than that. I can't seem to get Ubuntu to boot normally. Seeing as I'm a total nobb, what am I doing wrong here?

ps: CPU is  AMD phenom 2 x3 720 in case that might matter. (And yes, installing the 64 bit version)

---

### Post by Panizzi on 2009-11-09
try this:

```
grub>ls
grub>ls (hdX,Y)             #find ubuntu partition 
grub>insmod ntfs           #load ntfs module
grub>set root=(hdX,Y) 
grub>ls $Boot                   #find BOOT partition's UUID
grub>search --no-floppy --fs-uuid --set UUID  
grub>loopback loop0 /ubuntu/disks/root.disk  
grub>set root=(loop0)       #reset loop to loop0
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel
grub>initrd /boot/initrd.imgxxxxxxxxxxxx
```

use tab to complete xxxxxxxx, of course U can use "ls /boot" to select which kernel to be loaded

after login run "update-grub2" in terminal


more detail here:
[https://help.ubuntu.com/community/Grub2#Rescue Mode](https://help.ubuntu.com/community/Grub2#Rescue Mode)

---

### Post by replikanxxl on 2009-12-07
> **Panizzi said:**
> try this:

```
grub>ls
grub>ls (hdX,Y)             #find ubuntu partition 
grub>insmod ntfs           #load ntfs module
grub>set root=(hdX,Y) 
grub>ls $Boot                   #find BOOT partition's UUID
grub>search --no-floppy --fs-uuid --set UUID  
grub>loopback loop0 /ubuntu/disks/root.disk  
grub>set root=(loop0)       #reset loop to loop0
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel
grub>initrd /boot/initrd.imgxxxxxxxxxxxx
```

use tab to complete xxxxxxxx, of course U can use "ls /boot" to select which kernel to be loaded

after login run "update-grub2" in terminal


more detail here:
[https://help.ubuntu.com/community/Grub2#Rescue Mode](https://help.ubuntu.com/community/Grub2#Rescue Mode)

hey man . all u say is working . Right . but after i type boot and hit enter , the system reboots so i again choose ubuntu when my pc asks me to choose between windows or ubuntu. But so then im on the same screen again . What is wrong ?
i wanna ask something else also .  i have kernels 14,15 and 16 . but i can only find the  initrd.imgxxxxx for 16 . 15 and 14 are not showing up when i try to load kernel 14 or 15

---

### Post by gwatsmiles on 2009-12-08
> **replikanxxl said:**
> hey man . all u say is working . Right . but after i type boot and hit enter , the system reboots so i again choose ubuntu when my pc asks me to choose between windows or ubuntu. But so then im on the same screen again . What is wrong ?
i wanna ask something else also .  i have kernels 14,15 and 16 . but i can only find the  initrd.imgxxxxx for 16 . 15 and 14 are not showing up when i try to load kernel 14 or 15

how do you load the kernel? i tried the code given above by Panizzi and it works well until the loading the kernel part. what should i do? thank you very much and any help will be greatly appreciated.

---

### Post by gwatsmiles on 2009-12-08
hey it worked!


simply use the code below:
grub>ls
grub>ls (hdX,Y)             #find ubuntu partition 
grub>insmod ntfs           #load ntfs module
grub>set root=(hdX,Y) 
grub>ls $Boot                   #find BOOT partition's UUID
grub>search --no-floppy --fs-uuid --set UUID  
grub>loopback loop0 /ubuntu/disks/root.disk  
grub>set root=(loop0)       #reset loop to loop0
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel
grub>initrd /boot/initrd.imgxxxxxxxxxxxx
my system had kernel 2.6.31-14-generic.
after everything, just type "boot" in the sh:grub> and press ENTER.

:)

---

### Post by replikanxxl on 2009-12-08
> **gwatsmiles said:**
> hey it worked!


simply use the code below:
grub>ls
grub>ls (hdX,Y)             #find ubuntu partition 
grub>insmod ntfs           #load ntfs module
grub>set root=(hdX,Y) 
grub>ls $Boot                   #find BOOT partition's UUID
grub>search --no-floppy --fs-uuid --set UUID  
grub>loopback loop0 /ubuntu/disks/root.disk  
grub>set root=(loop0)       #reset loop to loop0
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel
grub>initrd /boot/initrd.imgxxxxxxxxxxxx
my system had kernel 2.6.31-14-generic.
after everything, just type "boot" in the sh:grub> and press ENTER.

:)

well i do the same stuff with my terms yes. but when i type boot and enter , then im back to the same place after the reboot . anyway im glad it worked for you ! i had to install another ubuntu from Cd this time

---

### Post by felixcorrales on 2009-12-09
> **replikanxxl said:**
> well i do the same stuff with my terms yes. but when i type boot and enter , then im back to the same place after the reboot . anyway im glad it worked for you ! i had to install another ubuntu from Cd this time


Type the next script in order to find the "Y":
grub>ls (hdX,Y)

You have to replace the script line:
...root=/dev/sda5

with the next one:
...root=/dev/sdaY

where Y=1 in most of Wubi cases, hence>
...root=/dev/sda1
-------------------------------------------
 grub>ls 
grub>ls (hdX,Y)             #find ubuntu partition  
grub>insmod ntfs           #load ntfs module 
grub>set root=(hdX,Y)  
grub>ls $Boot                   #find BOOT partition's UUID 
grub>search --no-floppy --fs-uuid --set UUID   
grub>loopback loop0 /ubuntu/disks/root.disk   
grub>set root=(loop0)       #reset loop to loop0 
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel 
grub>initrd /boot/initrd.imgxxxxxxxxxxxx 
grub>boot 

after login, run “update-grub2” in terminal

---

### Post by JasonSilver on 2009-12-10
Same things happens with me-- black screen after trying this stuff in grub. I see the little white ubuntu logo momentarily, then it hangs on black.

I was getting into a ram disk session for a while, but that wasn't getting me anywhere.

I don't have a CD drive, so have to install from Windows (I HATE VISTA!). If I uninstall Ubuntu from within Windows, I suppose I will lose everything, right?

Ugh. And this was starting out to be such a nice day.

---

### Post by aeronutt on 2009-12-10
I have the same problem, but 'most' of the time it boots (4 out of5?). Oddly, it seems to hang on the black screen when on battery more than when on AC. Luckily, I have a partition with 9.04 still. Unfortunate, the one thing an OS load should do is boot.

---

### Post by JasonSilver on 2009-12-10
I got back to that prompt I was referring to.

It says:

ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

Then it goes into a shell called BusyBox v1.13.3

It shows a few lines of messages, concerning sdb, "attached SCSI disk" and then stops with a blinking cursor.

What should I do?

---

### Post by Yith on 2009-12-13
Hi everyone! I instaled kubuntu 9.10 a couple of days ago; everything went well until I tried to run starcraft using wine, when I closed it, my screen went totally white, I thought it had crashed so I manually turned off my pc. When I turned it on I had the same problem as the original poster of this thread, I tried to follow the instructions given here and got error messages after these two steps:

grub>search --no-floppy --fs-uuid --set UUID 
grub>loopback loop0 /ubuntu/disks/root.disk 

So I went on and tried the final steps chosing both kernels I have (14 and 16), just to see the "Kubuntu" loading screen last for some seconds and then go completely black (happened with both kernels)

I also tried to use my installation cd to boot in "rescue mode", but it said that it had no full built-in "rescue-mode" :? , what shall I do guys? I must be doing something wrong coz' I'm a total noob and feel lost as hell at this point,I wouldn't want to reinstall it and lose all the progress I've been making :(

---

### Post by cbob on 2009-12-26
Try
```
ls
set root=(hd0,2) #As mentioned load your linux partition, mine being hd0,2
insmod ntfs 
loopback loop0 /ubuntu/disks/root.disk
linux (loop0)/boot/vmlxxxxxx root=/dev/sda2 loop=/ubuntu/disks/root.disk ro nosplash
initrd (loop0)/boot/inixxxxx
boot
```

---

### Post by Hiro_hiei on 2010-01-07
> Originally Posted by Panizzi  
try this:

Code:
grub>ls
grub>ls (hdX,Y)             #find ubuntu partition 
grub>insmod ntfs           #load ntfs module
grub>set root=(hdX,Y) 
grub>ls $Boot                   #find BOOT partition's UUID
grub>search --no-floppy --fs-uuid --set UUID  
grub>loopback loop0 /ubuntu/disks/root.disk  
grub>set root=(loop0)       #reset loop to loop0
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel
grub>initrd /boot/initrd.imgxxxxxxxxxxxx
use tab to complete xxxxxxxx, of course U can use "ls /boot" to select which kernel to be loaded

after login run "update-grub2" in terminal


more detail here:
[https://help.ubuntu.com/community/Grub2#Rescue](https://help.ubuntu.com/community/Grub2#Rescue) Mode
hey man . all u say is working . Right . but after i type boot and hit enter , the system reboots so i again choose ubuntu when my pc asks me to choose between windows or ubuntu. But so then im on the same screen again . What is wrong ?
i wanna ask something else also . i have kernels 14,15 and 16 . but i can only find the initrd.imgxxxxx for 16 . 15 and 14 are not showing up when i try to load kernel 14 or 15


I am having that same problem and that last step that was posted did me no good it don't work for me....

---

### Post by stevenjoes on 2010-01-08
I cant get past search --no-floppy --fs-uuid --set UUID

i get: no such device: UUID

any ideas?? i may have to ditch ubuntu!! it too kme hours to get my NDAS working as well.

---

### Post by justinweathersby on 2010-01-08
Yea same thing happens when i search too

---

### Post by stevenjoes on 2010-01-10
Hi, is there anything that can be done or do i have to uninstall and reinstall through wubi??

---

### Post by meierfra. on 2010-01-10
This is the solution by the author of Wubi:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by Bigj350 on 2010-01-13
> **JasonSilver said:**
> I got back to that prompt I was referring to.

It says:

ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

Then it goes into a shell called BusyBox v1.13.3

It shows a few lines of messages, concerning sdb, "attached SCSI disk" and then stops with a blinking cursor.

What should I do?

Ive been working on the same problem and once I ended up the same screen. Busybox v1.13.3. I fixed that by rebooting and changing the sda2 to sda3 in command line. If that doesnt work I think you can try sda4 or sda5 as well.

Sorry I just noticed that you posted that 4 weeks ago.

---

### Post by kigalirunner on 2010-01-14
This may not be very helpful, but I think I have a similar problem.  Some time ago I could no longer boot from kernel 17.  It would just return to the dual boot screen (Windows XP and Ubuntu).  By the way, I am a real novice and cannot follow anything very complex.  I found that if I moved to kernel 16 it would boot again.
 
Then this week another problem developed, which I think fits with this discussion thread.  When selecting Ubuntu in the dual boot, it went to a screen headed GNU GRUM version 1.97~beta 4, under which was [Minimal BASH-like editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible devise/file completion.]  Below this is an sh:grub> prompt.  
 
There is something very similar to this on the Grub 2 page on Community Documentation but slightly different, so I am not sure it is the same thing.
 
Does anybody know the problem here, why I am encountering it and what I can do to get back to Ubuntu, which has some crucial documents and photos that I should have backed up more recently than I have!  Is one of the solutions in this thread the one I should try?

---

### Post by meierfra. on 2010-01-14
> Does anybody know the problem here, why I am encountering it a

It's a bug in Grub 2. Grub 2 is only able to read the first 4GB (or so) of an NTFS partition. Anytime you have  a kernel update or run  "update-grub", one of your boot files might end up outside the 4GB.  Depending on which boot files it is , you will have different symptoms: kernel can not be found, grub menu does not appear,  kernel panic, splash screen disappears ...

> what I can do to get back to Ubuntu, 
You just need to download one file  to your C: drive. That will replace the faulty code and you should be all set. Click on the link in post 17.

---

### Post by bizkaz on 2010-02-03
> **gwatsmiles said:**
> hey it worked!


simply use the code below:
grub>ls
grub>ls (hdX,Y)             #find ubuntu partition 
grub>insmod ntfs           #load ntfs module
grub>set root=(hdX,Y) 
grub>ls $Boot                   #find BOOT partition's UUID
grub>search --no-floppy --fs-uuid --set UUID  
grub>loopback loop0 /ubuntu/disks/root.disk  
grub>set root=(loop0)       #reset loop to loop0
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel
grub>initrd /boot/initrd.imgxxxxxxxxxxxx
my system had kernel 2.6.31-14-generic.
after everything, just type "boot" in the sh:grub> and press ENTER.

:)

Hey all,

I'm getting really frustrated now!

I did the wubi thing - worked a treat for several weeks. Then this boot problem, resolved by following advice on these boards......

However (you saw this coming, right?) now similar problem again (several weeks on - i didnt think i had allowed any grub2 updates??). So I returned here, following the advice but I keep getting "file not found" errors mid way through my inputting of commands. For example after the "search......." line, as above i get-

error: no such device: uuid

and after the loopback command line i get-

error: file not found



help!!

ps I have found the faulty file/patch to download and copy over, but haven't been able to progress that far from boot..

Thanks,
Biz

---

### Post by darkod on 2010-02-03
> **bizkaz said:**
> Hey all,

I'm getting really frustrated now!

I did the wubi thing - worked a treat for several weeks. Then this boot problem, resolved by following advice on these boards......

However (you saw this coming, right?) now similar problem again (several weeks on - i didnt think i had allowed any grub2 updates??). So I returned here, following the advice but I keep getting "file not found" errors mid way through my inputting of commands. For example after the "search......." line, as above i get-

error: no such device: uuid

and after the loopback command line i get-

error: file not found



help!!

ps I have found the faulty file/patch to download and copy over, but haven't been able to progress that far from boot..

Thanks,
Biz

After the new wubildr file was released, don't bother with the commands above. They were just temporary solution. Just go here and download the new wubildr and replace the one in C: (or depending where you told wubi to install it might be D:, E:, etc):
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

You can do this from windows too. Don't keep trying to fix wubi, boot your windows, download that file and replace the current one.

---

### Post by bizkaz on 2010-02-03
> **darkod said:**
> After the new wubildr file was released, don't bother with the commands above. They were just temporary solution. Just go here and download the new wubildr and replace the one in C: (or depending where you told wubi to install it might be D:, E:, etc):
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

You can do this from windows too. Don't keep trying to fix wubi, boot your windows, download that file and replace the current one.
Thanks for quick response - never fails to amaze how keen folk are to spread the knowledge etc......

Unfortunately I've done the wubildr thing - I even did it again just a moment ago, and i still end up at the sh grub prompt as before....

its really frusrating as a non expert (im not even competent enough to be classed as highly as a"non expert" to be honest..

Any ideas anyone?

thanks again
biz

---

### Post by darkod on 2010-02-03
> **bizkaz said:**
> Thanks for quick response - never fails to amaze how keen folk are to spread the knowledge etc......

Unfortunately I've done the wubildr thing - I even did it again just a moment ago, and i still end up at the sh grub prompt as before....

its really frusrating as a non expert (im not even competent enough to be classed as highly as a"non expert" to be honest..

Any ideas anyone?

thanks again
biz

Sorry, I never use wubi myself. I just have that bookmarked in case someone asks about the wubi grub thing. If that doesn't solve it, I really don't know much about wubi.

---

### Post by meierfra. on 2010-02-03
Sounds like  the Wubi file system got corrupted. But before we jump to conclusion, let's have  a look at your system. Follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt.

---

### Post by bizkaz on 2010-02-03
ok - thanks, i'll try and do that....

as i use a netbook, and have no cd could i follow the instruction using a memory stick, if pop the livecd onto it?


like everyone else I have some stuff i'd like to save - fingers crossed..

also, if i succeed i promise to stop using wubi(useful tho it is) and move to dual boot!!

thanks
biz
;)

---

### Post by meierfra. on 2010-02-03
Yes, you can use a LiveUSB.  Pendrive Linux has instruction on creating a LiveUSB from Windows

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows).

---

### Post by bizkaz on 2010-02-04
I'm doing that stuff up there  /\  but i wondered, if i boot from the usb drive will i be able to find all  the bits a wanted to recover? 
 If so I'll save them, and just follow the instructions for a proper dual boot (non wubi) arrangement....


biz

---

### Post by meierfra. on 2010-02-04
> if i boot from the usb drive will i be able to find all the bits a wanted to recover?
You might have  to run the  filesystem checks before you will be able  recover any of the files.   If your  run the boot info script and post  the RESULTS.txt, I should be able to give you a better answer.

---

### Post by bizkaz on 2010-02-04
Well, i think i got there with only mild frustration - not bad.....
lets see if this makes any sense - it is worse than gobbledygook to me...
i suppose i should say when i ran the results program/script thing i still have a memory card and the usb that i'm booting off, both plugged in...

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk 
                       /IO.SYS /MSDOS.SYS

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdc1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd91ac89e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     4,014,079     4,006,016   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2 MB, 2097152 bytes
2 heads, 32 sectors/track, 64 cylinders, total 4096 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32         4,095         4,064   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       028dc347-9e7a-8d44-8282-c9c561f46199   ext2       casper-rw                     
/dev/mmcblk0p1   78AD-5A9E                              vfat                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        FAB408B5B4087683                       ntfs                                     
/dev/sdb1        A892-EBE3                              vfat                                     
/dev/sdc1        A842-8FC9                              vfat       DONT USE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/mmcblk0p1   /media/78AD-5A9E         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1        /media/DONT USE          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/FAB408B5B4087683  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[Boot Loader] 
timeout=5 
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[Operating Systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="USB Repair NOT to Start Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu"

---

### Post by meierfra. on 2010-02-05
> 
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr
/ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk 

Bad news: /ubuntu/disks/root.disk is missing. 

That is the file containing  the Wubi file system.  Just to  confirm: Boot into XP and look at C:\ubuntu\disks.  Does it contain any files other than "swap.disk"

Did you have any hard shutdowns lately?  Did your run "chkdsk"?  Do you  have  a folder "C:\FOUND.0000" or "C:\FOUND.0001",...

Did you do anything which might have caused "root.disk" to disappear?

I suggest to run a file system check on your XP partition. Boot into XP, go to Start->Run. Type "cmd".  This opens the XP command line. Type

```
chkdsk /r C:
```
and agree for "chkdsk" to run after rebooting.

Maybe "chkdsk" can recover "root.disk".  You might have to look in "C:\FOUND.0000", ..

If chkdsk does not  find "root.dsk" and you had value data in Wubi, you might have to look into data recovery. But since Wubi was on  virtual file system, I'm not sure how successful that will be.

---

### Post by bizkaz on 2010-02-05
> **meierfra. said:**
> Bad news: /ubuntu/disks/root.disk is missing. 
 
That is the file containing the Wubi file system. Just to confirm: Boot into XP and look at C:\ubuntu\disks. Does it contain any files other than "swap.disk"
 
[COLOR=blue]Yeah, it contains swap.dsk and  the folder boot, which contains the folder grub, which seems empty....[/COLOR]
 
Did you have any hard shutdowns lately? Did your run "chkdsk"? Do you have a folder "C:\FOUND.0000" or "C:\FOUND.0001",...
 
Did you do anything which might have caused "root.disk" to disappear?
 
[COLOR=blue]The machine was left on, running out of battery, therefore shutting down 'instantly' rather than shutting down properly. On restart in xp it did go through some checks (a blue screen of text cycling through some checking process?), so this sounds like the culprit?[/COLOR]
 
I suggest to run a file system check on your XP partition. Boot into XP, go to Start->Run. Type "cmd". This opens the XP command line. Type
 
```
chkdsk /r C:
```
and agree for "chkdsk" to run after rebooting.
 
Maybe "chkdsk" can recover "root.disk". You might have to look in "C:\FOUND.0000", ..
 
If chkdsk does not find "root.dsk" and you had value data in Wubi, you might have to look into data recovery. But since Wubi was on virtual file system, I'm not sure how successful that will be.
 
[COLOR=blue]I'll give that a go with fingers crossed, I appreciate your help - you owed me nothing but have been very patient - thanks..[/COLOR]
[COLOR=blue][/COLOR] 
[COLOR=blue]biz[/COLOR]

---

### Post by bizkaz on 2010-02-07
As i think you expected, there doesn't appear to be any improvement or "/found" files...
Yet another tech experience to put down to experience.....


windows is frustrating by comparison though so off to research partitions, dual boots etc.... scary!

note to self - back up, back up, back up...

---

### Post by meierfra. on 2010-02-07
> As i think you expected, there doesn't appear to be any improvement or "/found" files...
Sorry to hear.  

> so off to research partitions, dual boots etc.... scary!
It's not all that difficult. But

> note to self - back up, back up, back up... 

is the most important step, whenever you partition  a hard drive.

---

### Post by TriadHonor on 2010-02-07
The solution is simple: log in Windows and find the "wubildr" file, it usually be in the drive where wubi is.

Then you need a backupped one ( or you can find some here, on sourceforge or by internet, writing "wubilrd download" ) and replace the broken one you have.

Restart the system and log in Ubuntu like always.

Done :popcorn:


!= This is a knowed solution, found by most then one person, and documented in some place over the net

---

### Post by bizkaz on 2010-02-08
Thanks, but I've had a go at that already - my problem seems more terminal, with a key bit corrupted/removed, as described above...

thanks anyway,

biz

---

### Post by TriadHonor on 2010-02-08
So the disk is gone, try to recover it from Windows with something like Recuva ( [http://www.piriform.com/recuva](http://www.piriform.com/recuva) ).

Maybe you can recover, maybe not, but a try is necessary.

---

### Post by baseem on 2010-05-26
Guys I'm having this problem and it's urgent since I started working on a project and ubuntu stopped booting in the middle.. so I saw the code you posted and tried it but something is wrong:

```
grub>ls #DISPLAYS (hd0) (hd0,1) ...
grub>ls (hdX,Y)             # I choose (hd0,3) - which I found some files in
grub>insmod ntfs           #Displays nothing
grub>set root=(hdX,Y) #Displays nothing
grub>ls $Boot                   #Says (NULL) NO DEVICE .... UUID
grub>search --no-floppy --fs-uuid --set UUID  #I put that UUID - command displays nothing
grub>loopback loop0 /ubuntu/disks/root.disk  #SAYS error: NO FILE LABEL
grub>set root=(loop0)       #reset loop to loop0 #displays nothing
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda5  loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel #Tab completes nothing - ls doesn't show any files named vmlinuz..
grub>initrd /boot/initrd.imgxxxxxxxxxxxx
use tab to complete xxxxxxxx, of course U can use "ls /boot" to select  which kernel to be loaded
```"ls /boot" shows alot of files - how can I know my kernel version ?! 
NOTE: the wubi/ubuntu is installed at D:\ NOT C:\
C:\ has the windows

Please help me if you can..

Thanks alot!!!

---

### Post by thanhquanky on 2010-09-03
I had tried this 
```
grub>loopback loop0 /ubuntu/disks/root.disk
```

and it responded File not found while it's still there.

Any idea?

---

