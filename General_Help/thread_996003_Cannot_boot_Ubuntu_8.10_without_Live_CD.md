---
title: "Cannot boot Ubuntu 8.10 without Live CD"
date: 2008-11-28
forum: General Help
---

### Post by stormdragonbc on 2008-11-28
Hi,

I apologize if this has already been asked and answered but I did not see anything that seemed to fit when searching the forums (my search-fu needs a bit of help so it might be me ;)).

I am having an issue over the last couple of days trying to get Ubuntu 8.10 booting without the live CD with an older laptop.

Laptop Specs:
Toshiba Satellite M45-S331 Laptop 15.4” Harman Kardon
80GB HD
1GB RAM
1.6GHz CPU

I originally put Windows XP on this machine without issues. I then decided to dual boot with Ubuntu 8.04. The installation went through without errors until the reboot. I removed the live CD, rebooted and then had only a black screen with "GRUB" in the top left.

I put in the live CD again, rebooted and then chose the option of 'Boot from first hard disk'. This worked and then I had my menu options. I checked my BIOS and the only boot option is the one disk.

I followed a lot of threads that I Googled based on how to restore GRUB (i.e. finding the hd designation, setting root (hd0,0) and setup (hd0)), and though they appeared to give back the correct information, it did not correct the issue. Note: the drive is /dev/sda and brings back hd0,0.

So I then went and restored the MBR using the 'ms-sys -m' option in an Ubuntu terminal but then could only boot Windows. I decided to scrap Windows (since I actually have 2 other desktops with them) and have the laptop be only Ubuntu.

I used the partition manager to go in and delete/merge the partitions back into 1 drive, installed Ubuntu again (using Guided - whole drive) but after a reboot, same issue. I then upgraded to Ubuntu 8.10 (thinking that maybe there was an updated GRUB) but again...same issues.

The strangest thing was that a few months back, I had installed Ubuntu to a desktop without having any of these issues but it was a newer system and I had not tried to dual boot that one. It does seem that something is mis-configured (i.e. where GRUB is looking for the boot area) since I can use my live CD to boot into it but in following all of the GRUB posts without errors, I am not sure what I might be missing.

So I suppose I am just looking for help in making Ubuntu boot normally without needing the live CD and wondering if anyone has any ideas off the top of their head.

I am currently at work so I am unable to post the outputs of the GRUB commands or the menu.lst file...but I will later when I get home. Also, I am currently trying to set up a Supergrub disk to see if that will help.

I appreciate any assistance :)

---

### Post by caljohnsmith on 2008-11-28
Some people in the past have had Grub hang on start up like that because of the way they have their HDD configured in BIOS, or it might even be an issue with your HDD's cabling. I would start with your BIOS, and look for HDD related settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Any of those setting that you find, try changing them one by one and see if it helps. I would recommend writing down any settings you change in case you need to revert back. 

But it would be good to also do some basic "sanity checks" first just to make sure Grub is properly installed, so if you can open a terminal (Applications > Accessories > Terminal), please post the output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And we can work from there if you want. :)

---

### Post by stormdragonbc on 2008-11-28
After running the requested commands, the results are as follows:

```
sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1fc42245

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150255944    75127941   83  Linux
/dev/sda2       150255945   156296384     3020220    5  Extended
/dev/sda5       150256008   156296384     3020188+  82  Linux swap / Solaris

```

```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

GRUB 

```

```
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

ff00

```

My results from running sudo grub

```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

After a reboot, I still have the same issue. When I opened the menu.lst file, the details were:

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5e0ddf78-3ba8-45d6-a256-3a1c91fc50e7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5e0ddf78-3ba8-45d6-a256-3a1c91fc50e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5e0ddf78-3ba8-45d6-a256-3a1c91fc50e7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5e0ddf78-3ba8-45d6-a256-3a1c91fc50e7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5e0ddf78-3ba8-45d6-a256-3a1c91fc50e7
kernel		/boot/memtest86+.bin
quiet

```

I did check my BIOS but there were very basic options and nothing too much to mess around with.

Please let me know if there is any other information I can gather in order to help :)

---

### Post by psusi on 2008-11-29
Your bios may not be able to see the whole disk if it is an older computer.  Try installing using the manual partitioning option and create a 100-150 mb partition at the start of the disk and mount it as /boot, then use the rest for / and swap.

---

### Post by stormdragonbc on 2008-11-29
I wiped the install and manually reorg'ed the partitions as:

/dev/sda1  ext3  /boot  148 MB
/dev/sda3  ext3  /      76.87 GB
/dev/sda2  swap         3 GB

I am not sure if the sda order matters but it was the order in which I did it through the GUI (i.e. boot, swap then the rest went to the root).

Unfortunately though, after the reboot I get the same GRUB message :(

---

### Post by logos34 on 2008-11-29
are you sure there are no Bios options to change hard disk detect settings?  That would have been my guess

you might check site manufacturer site--there's something about "[hard disk not recognized"]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=882862&rpn=PSM40U&modelFilter=M45-S331&selCategory=3&selFamily=1073768663&selModel=882862%7CPSM40U#"). 
> 
"Issue:                      
Occasionally, your computer may not recognize its hard disk drive.
         
     

If you experience this symptom, please [update your computer's BIOS]("http://javascript%3Cb%3E%3C/b%3E:goLink%28%27../su/su_sc_modItemList.jsp?ModelDLOS=null&ModelDLCat=BIOS%7C105502&ct=DL&moid=882862%27%29")  to version 1.20 or later."Not sure if that's the problem but worth a try.  

Or maybe it's this problem:

> GRUB_   
                                       
                                   Looks like this.
                                                                                                                                                                    [COLOR=#ffffff]grub>_[/COLOR]
                                          
                                         
                                                                                                                                                                                                                                                                                    (With a non-blinking underscore). 
                                   
                                   If you see this [COLOR=#000000]GRUB[/COLOR] error just after you installed Linux with Windows XP on a Toshiba laptop, and if it has an 'Express Media Player' partition, this is reported to conflict with GRUB, as it uses the first track of the hard disk which is normally reserved for boot loaders. 
[COLOR=#000000]GRUB[/COLOR] uses the first 15 sectors following the MBR for the optional stage1_5 of GRUB to be installed there.  
                              Deleting 'Express Media Player', has been reported to have successfully solved this problem.
                               
If you don't want to delete your 'Express Media Player' partition, you can instead try doing without the optional stage1_5 of GRUB in the first track of your hard disk. Super Grub Disk has the ability to install grub without the 1.5 stage files: [http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

source: [http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by stormdragonbc on 2008-11-29
I checked and my BIOS is v1.30. I know what you mean though...my desktops (which are newer) seem to have more robust BIOS settings...this laptop, not so much. It's an old work laptop that I got for free...so I really can't complain ;)

The interesting thing is that when I installed, I deleted and merged all partitions, so there is no sign of an Express Media Player partition.

I will try the supergrub approach and hopefully that will sort it all out.

Thanks again for all of the excellent suggestions and assistance :cool:

---

### Post by stormdragonbc on 2008-11-29
After a bit more time and using a supergrub CD, still no resolution. I tried several repair options as well as not using the stage1_5 files...nada :(

Unfortunately, as much as I am sad to do, I might have to re-install XP to the laptop as I didn't have any issues with it loading up for me. I think that it is a hardware issue at this point...though odd that I am able to boot via disk or through XP without issues.

If I decide to tackle Ubuntu on this rig again, I can always dual-boot it (which was my original intention).

Once again, thanks to everyone who tried to help. It was much appreciated :)

---

### Post by stormdragonbc on 2008-11-29
Hate to say it but I just couldn't leave well enough alone...I just like linux :)

I tackled this from another side...I installed Fedora 10 as a dual boot to see if it was a laptop issue or an Ubuntu loader issue. After the Fedora installation, I have no issues booting into either XP or Fedora :-? This of course has me thinking I am misconfiguring GRUB in Ubuntu somehow.

Played around a bit with Fedora (and read a lot of Fedora vs Ubuntu) and it seems to be a bit slower but I might give it a chance. However, I would like to eventually get back to Ubuntu so if anyone might have any other ideas, I am always open to try.

thanks :cool:

---

### Post by caljohnsmith on 2008-11-29
If you are feeling just a little adventurous, you could reinstall Ubuntu, copy the stage1, stage1.5, and stage2 files of Fedora's Grub to your new Ubuntu, reinstall Grub with those files, and then in theory you should be able to boot since you are using Fedora's version of Grub. I don't think it would take much effort to see if it would work. Let me know if you would like help giving that a try.

---

### Post by oilchangeguy on 2008-11-29
> **stormdragonbc said:**
> I wiped the install and manually reorg'ed the partitions as:

/dev/sda1  ext3  /boot  148 MB
/dev/sda3  ext3  /      76.87 GB
/dev/sda2  swap         3 GB

I am not sure if the sda order matters but it was the order in which I did it through the GUI (i.e. boot, swap then the rest went to the root).

Unfortunately though, after the reboot I get the same GRUB message :(

if nothing else you do NOT need 3gb of swap space. 512mb max.

---

### Post by psusi on 2008-11-30
Are you sure that you reinstalled grub without stage 1.5?  And using a /boot partition at the start of the disk?  It does sound like that is the problem.

---

### Post by stormdragonbc on 2008-12-14
Sorry for the late reply...work has kept me busy.

It's possible that I have done something wrong (I am proficient with linux/unix systems but not the granular stuff...yet :)).

When I tried using the Fedora stage files, I copied them to a separate machine, then replaced the Ubuntu ones in the /boot/grub directory. I then went through the steps of doing the grub install (i.e. using the root(hd0,0) and setup(hd0)). However, I seemed to get a blank screen after that.

So I went and cleaned it all up and used the Supergrub CD to restore everything.

Now my boot directory looks like:

/boot/grub$ ls -al
total 189
drwxr-xr-x 2 root root   1024 2008-12-13 00:40 .
drwxr-xr-x 4 root root   1024 2008-12-13 00:14 ..
-rw-r--r-- 1 root root    197 2008-12-12 21:20 default
-rw-r--r-- 1 root root     15 2008-12-12 21:20 device.map
-rw-r--r-- 1 root root   8108 2008-12-12 21:20 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-12 21:20 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-12 21:20 installed-version
-rw-r--r-- 1 root root   8712 2008-12-12 21:20 jfs_stage1_5
-rw-r--r-- 1 root root   4615 2008-12-13 00:40 menu.lst
-rw-r--r-- 1 root root   4616 2008-12-13 00:39 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-12 21:20 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-12 21:20 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-12 21:20 stage1
-rw-r--r-- 1 root root 121460 2008-12-12 21:20 stage2
-rw-r--r-- 1 root root   9556 2008-12-12 21:20 xfs_stage1_5

I believe that my boot is setup correctly. My disks are set up as follows:
/dev/sda1 ntfs
/dev/sda2 extended
/dev/sda5 ext3 /boot
/dev/sda6 ext3 /

(note: I took out the swap since I have read it is not necessary and since I am doing a lot of testing/rebuilding)

The boot flag is currently on sda1 (ntfs). I tried to change that to be on sda5 then sda6...each time I get an 'operating system cannot be found' error at that point.

I was thinking maybe it was a setting in my menu.lst file? I have attached it to the thread.

---

### Post by caljohnsmith on 2008-12-14
> **stormdragonbc said:**
> 
I believe that my boot is setup correctly. My disks are set up as follows:

/dev/sda1 ntfs
/dev/sda2 extended
/dev/sda5 ext3 /boot
/dev/sda6 ext3 /

From post #5 you show sda1 as the /boot partition; did you reinstall or something? Which drive is Fedora installed to? How about downloading the attached "boot_info6.sh.txt" script to your desktop, and run it with:
```
sudo sh ~/Desktop/boot_info6.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will help clarify your setup. Also what is your current boot status? Do you have to use Super Grub to boot Ubuntu?

---

### Post by stormdragonbc on 2008-12-14
In post #5 I meant that I had wiped the complete machine and was only trying to install Ubunutu without the dual boot...I apologize for the confusion.

After that I then installed Windows XP and Fedora just as a check. When I had Fedora I then copied all of it's Grub files elsewhere so that I could re-install Ubuntu and try them out (which didn't work too well). As of this moment I have Windows XP on the first partition and Ubuntu 8.10 on the second partition...both are on one hard drive and the original Grub files from Ubuntu are installed.

I still need the Ubuntu Live CD in order to 'boot from first hard drive' in order to get the standard Grub menu and get into my OS's (both of which work properly).

I ran the app and I have attached the results.

---

### Post by caljohnsmith on 2008-12-14
According to the output file that you posted, you have Grub properly installed to the MBR, so that's not the problem. I think if I were in your shoes, I would try using "Grub4DOS" in Windows, and then you can easily use your Ubuntu's menu.lst with Grub4DOS. How about booting into Windows and do the following:
[LIST=1]
[*]Download the [Grub4DOS-0.4.4]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip") package and also the the "[grubinst]("http://download.gna.org/grubutil/grubinst-1.1-bin-w32-2008-01-01.zip")" package.
[*]Move the "grldr" file from the Grub4DOS-0.4.4 package to your C:\ root directory
[*]Use the "grubinst_gui.exe" program to install the Grub4DOS MBR (Master Boot Record)
[*]Save the following menu.lst to your C:\ directory:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d182911d-762d-492d-9cbd-28d4ea39b783 ro

## default grub root device
## e.g. groot=(hd0,0)
## groot=85ad6b4f-1d0e-4857-b077-e94172e0b813
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d182911d-762d-492d-9cbd-28d4ea39b783 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,4)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=d182911d-762d-492d-9cbd-28d4ea39b783 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root            (hd0,4)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
chainloader	+1

```
[/LIST]
Then reboot, and let me know what happens. We can work from there.

---

### Post by stormdragonbc on 2008-12-14
I did what you outlined, moving the grldr file and adding the menu.lst to the C root directory. When running the installer, I used the File option and selected the grldr.mbr file (I also tried the grldr file in the root), I get the following error:

"grubinst: Unknown image type"

If I select that file and then select the option 'Save embedded GRLDR MBR', I then get the message:

"The MBR/BS has been successfully installed"

But when I reboot, I still get the GRUB message with no menu.

---

### Post by caljohnsmith on 2008-12-14
It sounds like the Grub4DOS MBR might not have been installed successfully. Just to make sure, how about booting your Live CD, download the [Grub4DOS-0.4.4]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip") package to your desktop and do:
```
cd ~/Desktop
unzip grub*.zip
cd grub*
sudo dd if=grldr.mbr of=/dev/sda bs=440 count=1
sudo dd if=grldr.mbr of=/dev/sda skip=1 seek=1
```
Then reboot, and let me know exactly what happens on start up, including any error messages you might get.

---

### Post by stormdragonbc on 2008-12-14
After rebooting, I see a quick (as in half a second) message that states "Trying (hd0..." and then it is caught in an infinite loop. The trouble is that it loops so quick, it almost becomes unreadible (and actually the part of the '...' there is something but I couldn't make it out before it disappears). If I hit pause, I have a black screen until I hit another button and it loops again.

---

### Post by caljohnsmith on 2008-12-14
I really think the most likely cause of your boot problems is how you have your HDD configured in your BIOS. Neither Legacy Grub (Ubuntu) nor Grub4DOS work on that HDD, both giving really strange results. In my experience, Grub seems to be more sensitive to problems with your HDD BIOS setup, so that's often why people in the forums find out they have a BIOS issue even though they could previously boot Windows OK. How about going through your BIOS and find out what HDD related settings you have, and try changing them one by one to see if it helps. Some of the settings to look for I mentioned back in post #2, but you most likely won't have that many choices in your BIOS to worry about. How about giving that a shot and let me know how it goes.

---

### Post by stormdragonbc on 2008-12-14
I will definitely give that a try and report back how it goes (I will try looking for some BIOS updates as well).

Thanks again for all the assistance :)

---

