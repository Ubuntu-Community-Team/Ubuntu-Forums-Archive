---
title: "Fresh Install of Ubuntu Error 21 on Main Harddrive"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by tresanus on 2008-12-03
Okay I am brand new to linux.  I bought an Asus EEE 701sd a couple days ago and installed Ubuntu EEE from a flash card onto the hard drive.  Everything was working magically.

I always knew I was going to install XP on the machine as soon as I bought a USB cd rom but wanted to test out linux to see what it was all about.

I decided to install Ubuntu to a SD card incase I wanted to boot up linux and mess around with it once I had XP on the main drive.  This is where the madness starts.

When I removed the SD card and tried to boot back onto the hard drive I got the Error 21.  So me, not knowing much about computers, decided to format and fresh install ubuntu on the hard drive.  Through google searched I am learning that the error relates to my GRUB and that upon boot my system cannot find the grub loader or something??

Any help would be appreciated, hopefully this is an easy problem to fix!

Tres

---

### Post by tresanus on 2008-12-03
Just to let everyone know there is nothing on this machine I need to save.  I want to wipe the hard drive and start fresh, I guess I just need to fix the grub or boot loader or something.

Thank in advance for whatever help you guys might provide!

Tres

---

### Post by caljohnsmith on 2008-12-03
What happened is that when you installed Ubuntu to your SD card, Grub by default is installed to the MBR (Master Boot Record) of your internal HDD so that when you reboot, you should get the Grub menu and can boot Ubuntu. The big disadvantage of this though is that your two drives are dependent on each other for booting, so if you remove the SD card, you will get a Grub error like you got. 

Usually the most ideal solution for this situation is if you can change your BIOS to boot directly from the SD card, and then you can also install Grub to the MBR of the SD card to make it bootable. And if you reinstall a Windows MBR to your internal Windows drive, you should be able to boot directly into Windows if you boot the Windows drive instead of the SD card if the SD card is unplugged. Also, you can add an entry to boot Windows in your Grub menu if you want so you don't have to chnage your BIOS just to boot the Windows drive. If that sounds good to you, then you can first restore your Windows MBR from the Ubuntu Live CD by opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
Next, to install Grub to the MBR of your SD card:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Also, please post the output of all the above commands. Then reboot, set your BIOS to boot the SD card, and you should get the Grub menu on startup. See if you can get that far or let me know if you run into problems. :)

---

### Post by tresanus on 2008-12-03
John thank you for your reply! My fingers have been itching to get this working again!

What I would like to do is forget all about the sd card and just restore ubuntu to my main hard drive!

I am going to look through the information you have posted and see if I can figure out what has gone wrong!

Thanks,

Tres

---

### Post by tresanus on 2008-12-03
i tried the sudo apt-get install syslinux

and it said 
Reading package lists... Done
Building dependency tree
Reading state information...Done
E:  Couldn't find package syslinux

Does the E mean it is reading off my flash card?  I am using a 4gb flash usb drive to run live cd

Thanks again

---

### Post by caljohnsmith on 2008-12-03
That error you are getting with the "syslinux" package I think is because you either don't have internet access from the Live CD you are running, or maybe because you don't yet have all the repositories enabled in System > Admin > Software Sources. But if you just want to wipe your HDD and start clean anyway, don't worry about those steps I gave in my previous post; just pull up Ubuntu's partition editor (System > Admin > Partition Editor), and use that to delete the current partitions and set up all your new partitions. If you are going to also install Windows, you should do that before installing Ubuntu, because Windows will wipe out Grub in the MBR. How about trying that and let me know how it goes.

---

### Post by tresanus on 2008-12-03
john i deleted the first partition
and now i see this partition

dev/sbd (7.51 gb)

dev/sbd1           ext3                   7.15 gb
dev/sbd2           extended               376.52 mib
    dev/sbd5       linux-swap             376.49 mib

and it wont let me delete these partitions

is there a work around this? or maybe i dont know what i am doing!!

haha i think the latter

thanks again john

---

### Post by tresanus on 2008-12-03
also my asus only has an 8gb hard drive so I believe all that is my main drive.

the delete option is grayed out.

---

### Post by caljohnsmith on 2008-12-03
Try selecting the swap partition, right-click, and choose "swapoff". Then I think you should be able to delete it.

---

### Post by tresanus on 2008-12-03
partition has been deleted,
it is now installing ubuntu on my hard drive,

i will update when the install is done

lets cross our fingers for about 30 mins!

thanks either way John you have been a great help!

---

### Post by tresanus on 2008-12-03
okay reinstalled and reboot and same issue

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21

:-(

---

### Post by tresanus on 2008-12-03
And when I hit escape at the splash screen to switch to usb
it now boots ubuntu like it would normally but on the usb

it appears to me that ubuntu has installed the the usb?
even though I choose to install to the main hard drive?

oooohh boooyy

---

### Post by tresanus on 2008-12-03
now when i go to partition editor i see that 1.93 gib of something has installed on my main hard drive

i also see dev/sda is my usb flash drive
and dev/sdb is my main hard drive

maybe this means something to you? i dont know!

---

### Post by caljohnsmith on 2008-12-03
How about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd  -l  2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
Note that "-l" is a lowercase L, not a one. That will give me a clearer idea of your setup right as it currently stands.

---

### Post by tresanus on 2008-12-03
sudo fdisk -lu
Disk /dev/sda: 4025 MB, 4025810432 bytes 
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x000e5164 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          38     7839719     3919841    b  W95 FAT32 
 
Disk /dev/sdb: 8069 MB, 8069677056 bytes 
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x4d305939 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              63    14988644     7494291   83  Linux 
/dev/sdb2        14988645    15759764      385560    5  Extended 
/dev/sdb5        14988708    15759764      385528+  82  Linux swap / Solaris 
 
Disk /dev/sdc: 130 MB, 130023424 bytes 
1 heads, 32 sectors/track, 7936 cylinders, total 253952 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xd0c8e305 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *          32      253951      126960    b  W95 FAT32

---

### Post by tresanus on 2008-12-03
i recognize that sda1 is my usb pen drive
and sdc1 is another pen drive i just used to copy that information off my eeepc to my other laptop to post here.

my hard drive is sdb1

also when i search for my grub it locates it on (hd1,0)

---

### Post by tresanus on 2008-12-03
i think i need to move my grub from my pendrive to my hard drive

this is what i come across from forums and what kind of makes sense to me..  keep in mind before today grub meant bug of some sort!

---

