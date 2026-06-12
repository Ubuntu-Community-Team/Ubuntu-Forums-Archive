---
title: "new to Linux installs, grub 17 after install, drive confusion"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by navboy on 2009-02-14
after a bit of Googling, i might have some idea why i get grub error 17 when booting after installing Ubuntu 8 from LiveCd after running it from Windows XP Home ...

my Pentium3 machine has one of those mobo's with the regular two IDE channels, and then two extra channels for doing RAID. I've always had optical drives on the two regular IDE (which i can boot using the LiveCD from), and then a single ATA drive on the first of the extra channels, it always ran fine in Windows, and in fact the Ubuntu partion editor worked with it fine. 

But i'm assuming that sda1 or hd0 or however it sees it in Grub should somehow be something else? Yet when i boot from LiveCD and use Gparted it shows the main Ext3 partition flagged as Boot as sda1. I already tried the sudo Grub commands where i tell it hd0,0 and send it and supposedly MBR reinstalls at reboot, but no joy.

I read some brief post where someone said they replaced Grub with something called LILA and then all their disk numbering confusions were solved. I have no idea how to do that from the LiveCd or if that would even apply in my case ...

i've already tried every possible combination in BIOS of SCSI, HDD0 through HDD4 and ATA in the boot sequence choices, always fails with Grub error 17 unless i put LiveCd in the cd-rom ...

less than spectacular start to my first Linux install experiene, but hey, i'm in it to basically learn by doing, so i guess i should be happy the install isn't working?  hehe

-steve

---

### Post by redroad55 on 2009-02-14
The live cd was intended to be booted into and not run from xp .. am I missing something ..explain Post back

---

### Post by caljohnsmith on 2009-02-14
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by navboy on 2009-02-14
Thanks ... Redroad, i'd read something on the download page saying you can run LiveCD from windows, so i did in order to see if it could interact with my hardware, and it seemed to do just fine, so i figured it'd be an easy install since it saw my HDD, etc. Once you actually do the install, you reboot with the cd in the cdrom and it installed fine from there, no complaints at all. Somewhere in the process, it used a GParted looking partition interface, which defaulted to prompting me to keep Windows on a partition and add Ubunt, but since i intend to just make this a Linux box, i chose the Autoguide full partition choice, though in the end it seems to have created 3 partitions, adding two small ones for extended and swap.

Here is the results.txt - i saw a lot of this last night, digging around in menu.lst, etc/fstab, grub ...  neat.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa98da98d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,292,229   153,292,167  83 Linux
/dev/sda2         153,292,230   156,296,384     3,004,155   5 Extended
/dev/sda5         153,292,293   156,296,384     3,004,092  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="43a976fa-f807-4b68-ba34-ce6f63a7b4e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="527e1b2c-06c5-4186-b051-58bcd3a71619" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=43a976fa-f807-4b68-ba34-ce6f63a7b4e1 ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=43a976fa-f807-4b68-ba34-ce6f63a7b4e1

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
uuid		43a976fa-f807-4b68-ba34-ce6f63a7b4e1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43a976fa-f807-4b68-ba34-ce6f63a7b4e1 ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		43a976fa-f807-4b68-ba34-ce6f63a7b4e1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43a976fa-f807-4b68-ba34-ce6f63a7b4e1 ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		43a976fa-f807-4b68-ba34-ce6f63a7b4e1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=43a976fa-f807-4b68-ba34-ce6f63a7b4e1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=527e1b2c-06c5-4186-b051-58bcd3a71619 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  55.0GB: boot/grub/menu.lst
  55.0GB: boot/grub/stage2
  55.0GB: boot/initrd.img-2.6.27-7-generic
  55.0GB: boot/vmlinuz-2.6.27-7-generic
  55.0GB: initrd.img
  55.0GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-14
So just to confirm, are you getting the Grub error 17 before seeing "Press ESC to enter the menu"? I would assume so, and if that is the case, getting a Grub error 17 before seeing the Grub menu can sometimes be due to how you have your HDD set up in BIOS, because according to the script Grub is installed correctly and should work. How about going into your BIOS and let me know what HDD-related settings you have, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, legacy IDE, native IDE, ACPI, DMA, etc. We can work from there.

---

### Post by redroad55 on 2009-02-14
So ultimately you want just a clean linux install correct ?.. To do this put in the live cd .. when you get to the partition part choose manual > delete all patitions this will make them free space > then choose free space and you can now choose new partition > make the first partition aprox.. 8 gb (8000) choosing primary and mount point of "/" this will become your root partition ... Now you again choose remaining free space and new partition and size it to 2.0 gb (2000) and choose primary and the choice called swap area  >  last with what is remaining in freespace  choose new partition  this time logical and mount point /home ... This partition layout will allow you to expand later if needed .. now you can go through the install process .. Post back with any results and or questions ..Best to you

---

### Post by navboy on 2009-02-14
> **caljohnsmith said:**
> So just to confirm, are you getting the Grub error 17 before seeing "Press ESC to enter the menu"? I would assume so, and if that is the case, getting a Grub error 17 before seeing the Grub menu can sometimes be due to how you have your HDD set up in BIOS, because according to the script Grub is installed correctly and should work. How about going into your BIOS and let me know what HDD-related settings you have, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, legacy IDE, native IDE, ACPI, DMA, etc. We can work from there.

thanks ... Nod, it POSTs, does memcheck, runs the Highpoint Raid controller (which lists my single disk as the Primary Master and blanks on the remaining three channels), enumerates all the devices/IRQ's etc, then "Checking DMI Pool", then (if the LiveCd isn't in the cd-rom) "booting from cdrom ... Failure", then something along the lines of Loading Grub, Please Wait .... Grub Error 17 and hangs. 

It sure does sound like it can see my HDD during install but not at boot. I'm wondering if whatever LILA is does a better job with Raid controllers? Also, i can't remember where in the process, but i'm positive that somewhere during the install process i saw it echoing lines that had SCS!I or similar in them, which made me think it saw my HDD as a SCSII drive, but i haven't seen any references to that in menu.lst etc or that report results.

In my Award Modular BIOS, all 4 IDE HDD (primary and secondary master and slave) settings are AUTO-Detection, Auto, None, Manual and i've run Auto-detect numerous times and those settings are all Auto.  Then, all choices in boot sequence ordering are floppy, LS120, HDD-0 thru HDD-3, SCSI, CDROM, ZIP100, LAN and ATA-100, but i've tried them all.

In Integrated Peripherals, there are settings relating to both of the Onboard IDE-1 and IDE-2 controllers, currently both enabled and all settings set to Auto (settings are Master and Slave Drv PIO Modes and Master and Slave driver Ultra DMA, and then Enable/Disable setting for the ATA100-RAID IDE Controller (where my hdd is) and it's set to enabled.

One thing i have not changed around at all since it was working fine in Windows was the HighPoint Raid controller setup (HPT370/372), which is showing my hdd WDC WD800JB-22JJA0 on Primary Master channel and no drives on the remaing 3 channels (correct) using mode UDMA, size 80GB, and status HDD0. In this interface, you can set the mode for the drive, and you get more options than in the Award BIOS interface - in addition to the PIO modes, you have 3 "MW DMA" modes at different speeds, and 6 UDMA modes at different speeds, mine currently set to the highest UDMA 5 at 100 MB/s ... No raid arrays defined, just the single disk.

I'm wondering if i'm going to have to just put the optical drives on one traditional IDE port and the HDD alone on the second IDE port and just not mess with the ATA100 port - but back when i used this machine a lot it seems like you get better performance out of the ATA100 port than the other two IDE ports, and also since Windows handled it fine i'd like to know how to achieve the same thing with a Linux setup, in case i do decide to run RAID again in the future ...

-steve

---

### Post by caljohnsmith on 2009-02-14
So since you have your HDD connected to the HighPoint Raid controller setup as the only drive, is there any setting for disabling RAID? None of your other BIOS settings for that drive particularly jump out at me as a problem, but with a Grub error 17 in your situation, you never know what might cause it in BIOS. You could try changing some of the settings you mentioned (such as those related to DMA for example), and see if it makes any difference; I would suggest making a note of the original settings you change so you can revert back if necessary. Also, how about booting your Live CD, and at the first main menu choose "boot from first HDD" and let me know if that works. If not, next I would download the [Super Grub Disk]("http://www.supergrubdisk.org") and use that to reinstall Grub, because on some rare occasions I've seen where using a slightly different version of Grub cures a Grub error 17 in a situation like yours. And if none of those ideas work, I think I would probably go with moving the HDD to your ATA port, because I imagine that has the best chance of success. Good luck and let me know how it goes.

---

### Post by navboy on 2009-02-14
Thanks, both.  Well, CJ, i'm into the reinstall suggested by redroad ... though i'm guessing i'll still have the same problem recognizing the drive on the raid array, and yes, i'd alread tried the "boot to first drive" ubuntu startup option and it couldn't find the drive.

Now that i'm leaving the partition editor during install, though, here is what i recall seeing, and i see now it looks like it was a SCSI name or label or something:

The following partitions are going to be formatted:

partition #1 of SCSI3 (0,0,0) (sda) as ext3
partition #2 of SCSI3 (0,0,0) (sda) as swap
partition #5 of SCSI3 (0,0,0) (sda) as ext3

So, i wonder why the partition editor can see it fine, but they kernel can't later when grub is trying to mount it, or is that not what happens ...  Anyway, once this completes (will take quite a while), i may try the supergrub disk you referred to before giving up and going with regular IDE. No, there's no way to turn off raid inside the Highpoint setup (you can disable the entire controller in Award BIOS, but then it couldn't read the disk at all), you either have a raid array defined or you don't, and i currently don't.

---

### Post by navboy on 2009-02-14
Ah!  this time, at the final screen b4 launching the install, i clicked on the Advanced button just for kicks, and there is an option "install boot loader" which is enabled by default, and below that a dropdown list to specify where the boot loader should look or something, and it was defaulting to hda (which i assume is for traditional IDE or something while all my stuff is coming up as sda, presumably for SCSI (which in reality it's not, it's ATA, so i don't understand that). 

Anyway i had two potential choices in the dropdown list that seemed better than the default hda, the first was just "sda" but it listed my hard drive name out to the right so i chose that one, and below it was "sda1", which would seem to indicate that first partition i set up as mountpoint "/". I'm not sure what the difference between the two is, if there is any. Would both of them evaluate out to the same location = the start of drive sda, since partition 1 should be the start of start of drive sda, or is mount point "/" not actually at the start? Also, i noticed during partitioning that i could have chosen a mountpoint of "/boot", but i decided to follow your suggestion RR and just go with "/". What would specifying "/boot" be used for compared to using "/" ?

Thanks

---

### Post by caljohnsmith on 2009-02-14
> **navboy said:**
> 
Anyway i had two potential choices in the dropdown list that seemed better than the default hda, the first was just "sda" but it listed my hard drive name out to the right so i chose that one, and below it was "sda1", which would seem to indicate that first partition i set up as mountpoint "/". I'm not sure what the difference between the two is, if there is any. Would both of them evaluate out to the same location = the start of drive sda, since partition 1 should be the start of start of drive sda, or is mount point "/" not actually at the start? Also, i noticed during partitioning that i could have chosen a mountpoint of "/boot", but i decided to follow your suggestion RR and just go with "/". What would specifying "/boot" be used for compared to using "/" ?

Thanks
Definitely use "/dev/sda" as the location to install Grub, because that will install Grub to the MBR where it needs to be in order to boot the HDD. Choosing "/dev/sda1" installs Grub to the boot sector of the sda1 partition, which will not help in your case. Also, at least in my experience, making a separate boot partition won't have any advantage in your case.

---

### Post by redroad55 on 2009-02-14
The "/" root partition includes boot when boot is not put in its own partition .. Some people like to have a separate boot partition but its not necessary...having the home partition separate allows you to upgrade later without loosing your files and settings ..

---

### Post by navboy on 2009-02-14
Hmm, well i'm confused. Really thought that by pointing grub to sda in the advanced install options would do the trick since that made sense and definitely wasn't something i did on the original install, but same error 17. Have tried various boot sequence settings again in BIOS but no joy. What's confusing me is Linux is referring to my drives as sda and a label of SCSI3, which implies SCSI, but the mobo doesn't really use SCSI - it's an ATA100 raid controller. So in the boot sequence i've tried all the numbered IDE drives, as well as SCSI and ATA100 but makes no difference.

I also notice in the Highpoint controller setup, i can elect to change the mode of the only drive listed there from "HDD0" to "BOOT", but the change doesn't seem to stick - still get error 17, then the next iteration through i go into set up and the drive shows status of "HDD0" again, not "BOOT" ...

hmm

---

### Post by caljohnsmith on 2009-02-14
> **navboy said:**
> Hmm, well i'm confused. Really thought that by pointing grub to sda in the advanced install options would do the trick since that made sense and definitely wasn't something i did on the original install, but same error 17. Have tried various boot sequence settings again in BIOS but no joy. What's confusing me is Linux is referring to my drives as sda and a label of SCSI3, which implies SCSI, but the mobo doesn't really use SCSI - it's an ATA100 raid controller. So in the boot sequence i've tried all the numbered IDE drives, as well as SCSI and ATA100 but makes no difference.

I know it's confusing, but Ubuntu refers to all drives now as sdX, whether they are PATA or SATA. I think you should try changing the HDD to use the ATA controller and see what happens, but let us know what you decide to do.

---

### Post by navboy on 2009-02-14
CJ, if you mean changing the BIOS to use ATA100 as boot device, i've done that several times. I also tried using grub root and setup commands from terminal window, but no joy.

I've just booted with Supergrub disk, but have no idea what to do with it ... ?

Also, if i decide to give up and move the HDD to one of the two normal IDE ports, do i have to go through a complete install again and partitioning, and would there be a quicker way to let it discover the new arrangement ... ?

thanks

-steve

---

### Post by caljohnsmith on 2009-02-14
> **navboy said:**
> CJ, if you mean changing the BIOS to use ATA100 as boot device, i've done that several times. I also tried using grub root and setup commands from terminal window, but no joy.

Actually I meant what you intend to try, namely moving your HDD to an IDE port.
> **navboy said:**
> 
Also, if i decide to give up and move the HDD to one of the two normal IDE ports, do i have to go through a complete install again and partitioning, and would there be a quicker way to let it discover the new arrangement ... ?

thanks

-steve
You shouldn't have to reinstall anything, Grub should be correctly installed to that HDD since you chose "/dev/sda" during the installation, which is the same drive Ubuntu is on. I would just move your HDD to one of the IDE ports, boot the computer, and see what happens. Let us know how that goes.

---

### Post by navboy on 2009-02-14
I'll try that move next ... 

i did notice in Supergrup i get error 6, corrupt or mismatched stage 1 ...

also, on the move to IDE port, i guess what confuses me is everything now is in terms of "sda" whereas if i move it to IDE port, wouldn't it then be "hda" ?  Or were you trying to tell me everything gets read as "sda" now?

---

### Post by navboy on 2009-02-14
Hmm, now i've got single HDD on IDE primary master, made sure HDD0 was in boot sequence after cdrom, still get grub error 17.

---

### Post by redroad55 on 2009-02-14
Just wondered about jumper on back of drive but you say it booted in xp .. this is quite curious ..this link looks promising :
 [http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")
post back with any results and or questions .. Best to you

---

### Post by navboy on 2009-02-14
> **redroad55 said:**
> Just wondered about jumper on back of drive but you say it booted in xp .. this is quite curious ..this link looks promising :
 [http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")
post back with any results and or questions .. Best to you

Nod, those BIOS settings already are my current settings, and at each point i've done the Auto Detect thing, although they always list properly after bootstrapping

Nod, worked fine in XP and in 2000 before that, since it's a single drive, jumper is in neutral position for that drive, just like they ship it.

---

### Post by redroad55 on 2009-02-14
here's another link[http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux]("http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux")
post back

---

### Post by navboy on 2009-02-14
hmm, ran the file system check on both parititons with ex3, found no errors, no bad blocks, nothing to fix, no resizing to do, etc, no problems.

tried re-installing grub to mbr via bash shell again, no joy

now that the drive isn't on the raid controllers, i'm really at a loss to explain why menu.lst and all the other boot files seems to agree on numbering (there's only one drive, so no real potential for confusion) and gpart and see the drive fine and read and set its partition info, but for whatever reasons grub always give error 17 and hangs

---

### Post by navboy on 2009-02-14
I'm at the partition editor again, on my 3rd install, and even with my hdd on the primary IDE port, i notice gpart in the "prepare disk space" dialog still refers to my drive as "SCSI3 (0,0,0) (sda)" ...

Could this be part of the problem? The hard drive is a Western Digital WD800JB (so called "Caviar") EIDE drive. Is the SCSI3 thing just some sort of leftover label from before, or is it seeing it as a SCSI drive rather than an IDE drive?

---

### Post by redroad55 on 2009-02-14
I'm afraid that's not it ..  I'm wondering if you change the bios to default settings but first record any changes that you've made prior to that .. I still think it's in bios or the first block of the hard drive that is steering you wrong ... You can try going to western digital's site and downloading their hard drive tools and wipe the drive clean .. Also the live cd when you boot it it gives you a choice to check the cd itself for integrity .. I know it seems like all this is a hassle but this sort of thing helps us learn ... For the most part all my ubuntu installs have gone well but it's that 1 or 2 that have a pain that I've learned the most from ..

---

### Post by caljohnsmith on 2009-02-14
> **redroad55 said:**
> I'm afraid that's not it ..  I'm wondering if you change the bios to default settings but first record any changes that you've made prior to that .. I still think it's in bios or the first block of the hard drive that is steering you wrong ... You can try going to western digital's site and downloading their hard drive tools and wipe the drive clean .. Also the live cd when you boot it it gives you a choice to check the cd itself for integrity .. I know it seems like all this is a hassle but this sort of thing helps us learn ... For the most part all my ubuntu installs have gone well but it's that 1 or 2 that have a pain that I've learned the most from ..
I just want to mention that at least in my experience helping in the forums for about a year now, I've never seen a case of solving the type of Grub error 17 as Navboy is experiencing by wiping the drive clean or reinstalling. That's why I didn't recommend it originally, but of course Navboy is free to try whatever he wants. If he can possibly get a BIOS upgrade for his computer, that might help, but otherwise I don't think doing more reinstalling will fix the problem (but I could be wrong).

---

### Post by navboy on 2009-02-14
Hey fellas, progress of sorts ...

I reinstalled, and this time i deleted all partitions PLUS the partition table (i did the first time i repartitioned, but not since i moved the hdd to std IDE port), reset them all (now that drive is on the std ide port) and this time i also chose to format everything i could (wouldn't let me format swap partition), which i hadn't reformated on prior attempts. 

After install/reboot, grub went fine this time and i have a desktop and all, but it's odd, now i under Computer i only see the optical drives and file system icons, nothing for the hdd, much less the partitions on it like i had in LiveCd.

Also, the Partition Editor is no longer listed under Administrative Tools. Where did it go?

---

### Post by caljohnsmith on 2009-02-14
> **caljohnsmith]I don't think doing more reinstalling will fix the problem (but I could be wrong).[/QUOTE]
Yes, it looks like I was totally wrong. I stand corrected, redroad55, and I'm really glad that navboy got Grub to work finally. My apologies if my previous reply seemed too brusque.
[QUOTE=navboy said:**
> 
After install/reboot, grub went fine this time and i have a desktop and all, but it's odd, now i under Computer i only see the optical drives and file system icons, nothing for the hdd, much less the partitions on it like i had in LiveCd.

If you only have your Ubuntu partition and swap partition, those partitions will not show under the Places menu. You can check all your HDDs and partitions by doing:
```
sudo fdisk -lu
```
> **navboy said:**
> 
Also, the Partition Editor is no longer listed under Administrative Tools. Where did it go?
You have to install it since it only comes by default with the Live CD. You can install the partition editor with:
```
sudo apt-get install gparted
```
Anyway, glad you have Ubuntu working.

---

### Post by redroad55 on 2009-02-14
It's great you stuck with it .. Ubuntu really is a great OS .. Best to you and you also caljohnsmith

---

### Post by navboy on 2009-02-14
well, thanks to both ... learned quite a bit in this bit of hassle ... if i had more time, i'd try the raid port again but that'll have to wait for another time ...

yep, all the disks are there in the fdisk listing, i guess i'm so used to seeing any hard drives drives listed in the GUI right alongside optical drives, it seems really weird to me to see those and not some sort of representation of any fixed disks. I'm sure there's probably a reason in the evolution of it all.

I could see all partitions listed from the LiveCD - is that just because i was in an instance that was not booted from a fixed disk so it showed them?

Anyway, thanks for the help ...

-steve

---

### Post by redroad55 on 2009-02-14
That is something you'll have to get used .. In a short while you'll have forgotten all about it ..Like was mentioned above you can add gparted or gnome partition editor ... Gnome partition editor can be added by going to applications > add/remove > system tools > scroll to gnome partition editor > check box and click apply changes in lower left corner .. Then look in applications > system > admin. for partition editor .. This will give you a clear breakdown of HD ..

---

### Post by navboy on 2009-02-15
cool, thanks ..

one final (possibly dumb) question to get me rolling:

At some point in my troubleshooting process, i followed instructions to run a command in the Gnome terminal that started with "sudo bash ..."  .  I'm confused - i thought i was already in a bash shell by opening up a Gnome terminal ... what is the point of using bash in a command line inside what is already a bash shell?

---

### Post by redroad55 on 2009-02-15
this link I find to be chucked full of great info. :
[http://ubuntuforums.org/showthread.php?t=898328]("http://ubuntuforums.org/showthread.php?t=898328")

then this one for command line questions :
[http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")

> Let's try another example. We will look at the bash program which is located in the /bin directory:

[me@linuxbox me]$ ls -l /bin/bash


-rwxr-xr-x 1 root root  316848 Feb 27  2000 /bin/bash

Here we can see:

    * The file "/bin/bash" is owned by user "root"
    * The superuser has the right to read, write, and execute this file
    * The file is owned by the group "root"
    * Members of the group "root" can also read and execute this file
    * Everybody else can read and execute this file

In the diagram below, we see how the first portion of the listing is interpreted. It consists of a character indicating the file type, followed by three sets of three characters that convey the reading, writing and execution permission for the owner, group, and everybody else.

permissions diagram



Although the diagram did not show up in the quote it can be found under " permissions "  in the link for script above..
Best to you

---

### Post by navboy on 2009-02-15
Very cool. Thanks RR ...

-steve

---

