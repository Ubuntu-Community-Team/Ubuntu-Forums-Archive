---
title: "Lenovo (Y580) Partition Issue"
date: 2012-07-18
forum: Hardware
---

### Post by Degraan on 2012-07-18
So I just received a Lenovo Y580 for work that I was intending to dual boot Ubuntu on. I unfortunately have to keep the W7 OS installed for work but I can install another OS for my personal use. Apparently, Lenovo systems ship with 4 partitions which the Lenovo forums say "not to touch".

SYSTEM_DRV  200MB    NTFS
LENOVO      25.27GB  NTFS
Windows7_OS 420.56GB NTFS
(No Name)   19.53GB  (No FS) - noted as (OEM Partition)


I figured I could just shrink the Windows7_OS partition down 150GB and install on that. When I shrink it though, I can't set it up as an NTFS with Windows7 and when I boot into the 12.04 Live CD, it tells me that the "free space" is unusable. I wanted to see if anyone had any suggestions on: 

a.) Why is the free space unusable and is there a way to access it?

b.) Is there a way to merge Lenovo's partitions without screwing up the Windows OS?

I realize this is a fairly specialized question, but I figured I'd get more help here than the Lenovo forums.

Thanks

---

### Post by oldfred on 2012-07-18
Welcome to the forums.

Since it is a work computer, I am not sure you should be modifying it. You have run into the ancient MBR(msdos) four partition limit. Microsoft uses 2, boot & main install and the vendor uses 2, one is an image of drive as purchased for restore & the other usually system utilities. 

You can purchase another hard drive or even a larger flash drive and install to that. USB port is a bit slower and flash is slow writing but either will give a functional system without modifying your hard drive.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

Whatever you decide make recovery DVDs, full backup & repairCD:

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

While older install versions, the installer has not changed much at all.
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by Degraan on 2012-07-19
First off thank you, a majority of this was extremely helpful. I've got the go ahead from my boss for modifying the machine so that isn't a worry, I just need to be able to get my work done on it as well (which is why I need windows intact).

So I cleaned the hard drive down to:

> 
/dev/sda
    /dev/sda1 SYSTEM_DRV   200 MB NTFS
    /dev/sda2 WINDOWS7_OS  374 GB NTFS
    /dev/sda3 UBUNTU       126 GB Extended
        /dev/sda5 BOOT     300 MB Ext2  /boot
        /dev/sda6 ROOT     15 GB  Ext4  /
        /dev/sda7 HOME     104 GB Ext4  /home
        /dev/sda8 SWAP     8 GB   linux-swap 
 

I installed Ubuntu Desktop 12.04 64 bit and the installer finished clean, but I can't access grub. I've tried modifying the BCD to load sda5 on boot but it just sits with a blank screen and blinking cursor. I've tried to reinstall multiple times with no success. I'm not sure what I'm missing.

The machine is definitely configured MBR and not GPT. The first 200 MB partition on the drive is Lenovo's custom bootloader that is bootstrapping windows so I'm pretty sure I don't want to tamper with that.

---

### Post by oldfred on 2012-07-19
The Windows boot loader will not boot Ubuntu, not sure if Lenovo's is the standard Windows boot loader or a modified Windows. But all that boot loader does is look for the partition with the boot flag and jump to the PBR - partition boot sector to find more code to boot. With Windows a NTFS PBR has either reference to ntldr for XP or bootmgr for Vista/7.

If you install grub to the PBR of the Linux boot partition you cannot get to it. The Windows boot loader only looks for primary partitions not logical.

You can either backup MBR and replace it with grub2's boot loader or install grub2's boot loader to an external device like a CD or USB flash drive. Then when you boot from flash it can load the install on the hard drive.

Supergrub works like the external boot in that it finds an install and boots it.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

But any of the repair tools will write a Windows like or grub2 boot loader to the MBR. Even any Windows repairs that runs fixBoot will write a standard Windows boot loader.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1

the full MBR is 512, but that includes the partition table. If your backup includes that, then you modify partitions, the backup will damage partition table.

Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

---

### Post by Degraan on 2012-07-19
Played around with that for a bit and I seem to have everything running properly through Grub now, thanks so much for all the help.

One more quick question, my trackpad and function keys were working on the live CD but seem to no longer be functional on the actual install. Can I just use the drivers provided by Lenovo that I have backed up or will I need to find a linux equivelent?

Thanks again.

---

### Post by oldfred on 2012-07-19
If it worked on liveCD you should have or be able to get drivers. But I do not know details on those. 

Under system settings, drivers does it automatically suggest some additional drivers. 

There are other threads on similar issues, you can search forum or start a new thread with those issues in the title so someone that know may respond.

---

### Post by vincom2 on 2012-07-27
Hi,
sorry for butting into your thread, but I have a Y580 on its way to me and am thinking of installing either ubuntu or linux mint on it. A couple of questions, if you wouldn't mind:
1) once you copy the drivers and make the recovery DVDs, it's perfectly fine to remove the OEM and recovery partitions, right? did you do this using windows 7's Disk Management?
2) Does the Y580 come from the factory with its HDD formatted as GPT or MBR? i.e. did you have to convert it to MBR for your install?
3) did you try using easyBCD to configure the bootloader instead of using grub2?
4) have you tried bumblebee with it? I've seen reports around that say the ideapad Y570 was configured weirdly by lenovo such that bumblebee wouldn't work with it. Is this also the case for the Y580?
5) Have you managed to fix the trackpad and function keys?

Thank you in advance.

---

### Post by Degraan on 2012-07-27
> **vincom2 said:**
> Hi,
sorry for butting into your thread, but I have a Y580 on its way to me and am thinking of installing either ubuntu or linux mint on it. A couple of questions, if you wouldn't mind:
1) once you copy the drivers and make the recovery DVDs, it's perfectly fine to remove the OEM and recovery partitions, right? did you do this using windows 7's Disk Management?
  Yep, if you're sure you have both the D:/ drive (Drivers/Apps) and used the Lenovo backup utility to make DVDs. Use dskmgmt to remove the two partitions. Don't touch the SYSTEM or Windows7_OS partitions obviously.  > **vincom2 said:**
>  2) Does the Y580 come from the factory with its HDD formatted as GPT or MBR? i.e. did you have to convert it to MBR for your install?
  Half the internet insisted it was shipped GPT, and I was initially working on that assumption. However after running the command "list disk", I found out it's MBR. So unless they've changed something in the last 2 weeks, you'll be good to go with MBR. (Probably check just to confirm though)   > **vincom2 said:**
>  3) did you try using easyBCD to configure the bootloader instead of using  grub2?
  I tried using easyBCD repeatedly and ended up completely losing bootability at one point which I had to fix with a windows boot disk (make one of those too). As far as I can tell, no matter how I configured my linux install, the easyBCD entry couldn't get grub or linux going when I selected the boot partition. I finally had to use the grub boot disk listed in the post above and it automatically make grub my default bootloader. It works fine with Windows so that's what I'd suggest. It's a lot less of a headache.  Steps:  Install with whatever partitions you want in the extended partitions and install the bootloader to sda. It'll still only load windows, so use the grub boot disk to load in and find the bootloader. It then just set that up as default and I was good to go.  > **vincom2 said:**
>  4) have you tried bumblebee with it? I've seen reports around that say the ideapad Y570 was configured weirdly by lenovo such that bumblebee wouldn't work with it. Is this also the case for the Y580?
 I haven't tried bumblebee but I think that both models are near identical.  > **vincom2 said:**
>  5) Have you managed to fix the trackpad and function keys?

Thank you in advance.

 Function keys always worked, I had a minor issue with right clicking but I used this patch to fix it and everything is working great now.  [http://ubuntuforums.org/showpost.php?p=11918367&postcount=18](http://ubuntuforums.org/showpost.php?p=11918367&postcount=18)  Hope this helps.

---

### Post by vincom2 on 2012-07-31
Thanks for the help! I'm typing this from my new Y580 running LM13 :) the disk did indeed come formatted MBR, not GPT.
Also, easyBCD worked fine for me (decided to go with that because it'll be less troublesome if I play around with linux installs). I can't seem to get bumblebee to work. I *think* the power-saving nvidia card-disabling feature is working properly, but optirun definitely doesn't work for me. If anyone managed to get it to work, maybe you could share! That'd be great.
My right-click didn't work either, but after installing that patch you linked to, it works fine. Thanks! (although the touchpad behaviour is not very satisfactory compared to when in windows...)
Also, ethernet didn't work out of the box. I followed [this]("http://askubuntu.com/questions/165192/how-to-install-drivers-for-the-atheros-ar8161-ethernet-controller") and it's fine now.

---

### Post by alfchung on 2012-08-10
Hi I have the same issue with Y580. Lenovo comes with 4 primary partitions and I get rid of one and resized one. Therefore, I have 3 primary for Windows and empty space (220 GB)

Then in Ubutun live USB, I partitioned the empty space into 210G Ext4 and mounted as / (sda4 logical) and 2G as Linux swap. 

For where to install grub, I tried both sda( I guess the whole disk), and sda4 ( the 210 Ext4 as mentioned before)

The installation went through. However, it boots to Windows 7 every time!!!

I tried on BIOS, both enable and disable UEFI. No luck. 

I read a little bit about MBR, GPT, UEFI and got some concept. However, I have no idea how to make my Linux partition GPT and bootable. 

I don't even know what kind of partition the pre-installed Windows is. 

Would you mind telling me how exact should I set up dual boot on Y580. Maybe we can create a Wiki page for Lenovo Ideapad Y580. 

Here is one for Arch Linux
[https://wiki.archlinux.org/index.php/Lenovo_IdeaPad_Y580](https://wiki.archlinux.org/index.php/Lenovo_IdeaPad_Y580)

I think it is way too complicated to follow. 

And this is the post for Fedora
[http://forums.fedoraforum.org/showthread.php?t=282998](http://forums.fedoraforum.org/showthread.php?t=282998)


I still don't know the answer. 

Thanks a lot!

---

### Post by oldfred on 2012-08-10
@alfchung
You need to know if your drive is gpt or MBR(msdos). Windows only boots from gpt partitioned drives with UEFI, so do not convert if you already are MBR. 

Degraan's post above shows exactly how he repartitioned his MBR drive.

Post this from the liveCD terminal:

sudo fdisk -lu

If it comes back with gpt then post this:
sudo parted /dev/sda unit s print

---

### Post by alfchung on 2012-08-10
@oldfred, thanks a lot for replying!

Here is what "sudo fdisk -lu" shows, and I don't know how to see if it is MBR or GPT... I ran it on Ubuntu Live USB. Sorry about the dump question again! 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb6934443

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   468111359   233849856    7  HPFS/NTFS/exFAT
/dev/sda3       935811072   976773167    20481048   12  Compaq diagnostics
/dev/sda4       468113406   935809023   233847809    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       468113408   896747519   214317056   83  Linux
/dev/sda6       896749568   935809023    19529728   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7935999     3963968    c  W95 FAT32 (LBA)

---

### Post by oldfred on 2012-08-10
@alfchung
fdisk in effect errors out and says it does not work with gpt. gpt has a protective MBR that just has one entry saying it is gpt, so the older tools do not think a gpt drive  is not a partitioned drive. You have MBR.

Partitions look ok.

I would try Boot_repair. If that does not work, run the BootInfo report and post link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by AlexInBlack on 2012-08-16
I'd just like to say that I just got a Y580 as well and ran into the same boot loader troubles, using the same partition scheme as Degraan. I tried using Rescatux to repair grub, getting a successful message, but still failing to find a boot device. Super Grub2 Disk could find a grub configuration file, but not a grub install. I was able to boot into either Windows 7 or Xubuntu using the grub configuration file. Running "sudo grub-install /dev/sda" or "sudo grub-install /dev/sda5" in Xubuntu both failed, despite giving me a successful install message.

Boot-repair finally got grub working for me.

Thanks, oldfred.

---

### Post by VansEF on 2012-12-06
Hi,

I reply to this thread since I have a new Lenovo IdeaPad Y580, too and it seems I have a similar problem trying to install ubuntu alongside 
the pre-installed Windows 7 as a dual boot.

I also have the model with the 32G SSD and the 4 occupied primary partitions. So I found this thread and tried to follow the steps...

- created recovery disks 
- deleted the lenovo-driver partition (but still kept the recovery partion)
- downsized the windows partion, created an additional ntfs partition for data exchange 
- then I started ubuntu installation from usb stick and created the necessary root-, swap- and home-partitions in the free drive space
- the notebook is booting in EFI mode so I also created an EFI partition
- ubuntu installad successfully and after reboot still Windows booted as expected from this thread
- but Windows reported some problems during boot, so I ended up  using the one key recovery feature
- Windows recovered successfully, but completely on the SSD, now what as I remember was different in the original configuration (??)
- so, anyway I installed ubuntu again and after installation I rebooted from ubuntu live stick and started boot-repair to get a grub boot menu
- boot-repair reported success, but after another reboot still there is no boot menu and Windows is booting
- using F12 shows an ubuntu entry, but choosing this one boots Windows, too :(

When I ran boot-repair last time this is what it created as 
information link:
[B]
[http://paste.ubuntu.com/1415501/]("http://paste.ubuntu.com/1415501/")[/B]

I also tried EasyBCD on Windows side but that didn't work, too.

What do I miss here??

As I am not that familiar with partition issues I would be very thankful for any suggestions!!

regards, VansEF

---

### Post by YannBuntu on 2012-12-06
Welcome among us

> **VansEF said:**
> [http://paste.ubuntu.com/1415501/]("http://paste.ubuntu.com/1415501/")

This looks like this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1085908](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1085908)

---

### Post by oldfred on 2012-12-06
Welcome    	VansEF

Even if your system can boot in UEFI mode, your Windows is in BIOS/MBR mode, so you need to install Ubuntu in BIOS/MBR mode. 
You then do not need an efi partition as that is only with gpt partitioning and UEFI boot.

Some others with Intel SRT. Even if different vendors the way Intel SRT is done is the same.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by VansEF on 2012-12-07
Hi again,
thank you for the quick reply!

So, I removed the EFI partion and just re-installed ubuntu again...also used boot-repair
again after installation and this time it worked, i.e. I finally have a grub boot menu and
both systems are booting.  :smile:

I don't really know, what really was the problem before, but one obvious difference 
during boot-repair run was that boot-repair advised me to install some additional packages to continue.

Ok, everything seems to be fine now, thanks again.

regards, VansEF

---

