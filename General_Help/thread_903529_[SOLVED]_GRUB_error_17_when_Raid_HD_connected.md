---
title: "[SOLVED] GRUB error 17 when Raid HD connected"
date: 2008-08-28
forum: General Help
---

### Post by azTom on 2008-08-28
I'm running XP Pro. (desktop), XP on one HD Ubuntu on another. Grub loads OK with just the XP & Ubuntu HDs connected.
BUT then I connect a Raid HD I either receive an Error #17 or just hangsup saying Grub loading when I strap the Raid drive as Slave. The HD I'm using is a 200MB Seagate.

Note: In windows Device Manager Raid works great!

Any and ALL help/suggestions greatly appreciated.

azTom

---

### Post by fjgaude on 2008-08-28
Could you show us the output of your /etc/fstab file?

I think what is happening is the drive letters are changing when you add the raid drive... so you will need to change the drives in the fstab file to UUIDs. Then drive letter changes will not affect the boot.

Let us know how you are doing.

---

### Post by azTom on 2008-08-28
I'm a newbe to Linux so please have patience with me. In Ubuntu I opened the Synaptic Package Manager and entered /etc/fstab/ and it came up with latest version packages pmount ver 0.9.16-4 and xvmount 3.7-18 which evidently are not installed/mounted or whatever.  What should I do with them?

---

### Post by fjgaude on 2008-08-28
Nothing!

Do this:

```
gksu gedit /etc/fstab
```

Therein you should see the contents of the fstab file. Copy and paste it here so we can take a look.

---

### Post by azTom on 2008-08-28
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=bd45135d-6e9a-4021-8b87-a198c1542ecd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=0150669b-80e1-4d43-a302-af84345cef5c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by azTom on 2008-08-28
REMEMBER this does NOT include the Raid HD!  I cannot run Ubuntu with the Raid HD connected.

Sorry it took so long to get back to you, I had to attend a meeting.

Thanks for your advice.

---

### Post by fjgaude on 2008-08-29
Okay, it's not the drive letter changing.

Now what about the tail-end of the **menu.lst** file that shows the **grub** listing of what you can boot. We wish to see that it has the same UUID, i.e., the UUID=bd45135d-6e9a-4021-8b87-a198c1542ecd, for the boot drive that the fstab shows.

```
gksu gedit /boot/grub/menu.lst
```

Look for the line that says: ## End Default Options ## then you should see at a root= line the UUID= we are looking for.

I can't say if we can get to where you wish to go but this is one way to try.

---

### Post by azTom on 2008-08-30
Remember I'm new to Linux and their command lines.
 Are you suggesting I go to the terminal window and type in ##End Deault Options##?

What root= am I looking for?

What's a UUID? and what should I be looking for?

---

### Post by fjgaude on 2008-08-30
> **azTom said:**
> Remember I'm new to Linux and their command lines.
 Are you suggesting I go to the terminal window and type in ##End Deault Options##?

Enter in a terminal the command given as code.

What root= am I looking for?

That's a line in the file you will be seeing in gedit. As stated near the bottom of the file

What's a UUID? and what should I be looking for?

A UUID is the label for a drive letter.

---

### Post by caljohnsmith on 2008-08-31
[quote=azTom]BUT then I connect a Raid HD I either receive an Error #17 or just hangsup saying Grub loading when I strap the Raid drive as Slave.[/quote]azTom, please clarify: when you connect your RAID array, do you get the Grub error 17 before you get the Grub start up menu, or do you see the Grub menu, try and select an OS, and then get the error 17? I assume from what you say above you are getting the error 17 before getting a Grub menu, but correct me if I'm wrong.

Fjguade, if azTom gets the Grub error before seeing a menu, then changing his menu.lst will not help load Grub on start up. I agree with what you pointed out earlier: the device names of the HDDs are probably changing. But when you install Grub to the MBR of a drive, it hard-codes into the MBR the HDD location as (hdX,Y) where it looks for its system files, including menu.lst. So if the HDDs get moved around, like when he connects his RAID HDD, then Grub still points to (hdX,Y) even though that is probably an entirely different HDD now. Therefore, changing his menu.lst will unfortunately not fix that. :)

azTom, there are a number of solutions for your problem, but probably the best would be to install Grub to the MBR of the Ubuntu HDD and set the BIOS to always boot from that HDD. Which HDD are you booting from now? Based on the symptoms of your problem I might guess you are booting the Windows HDD first (but it has Grub installed to its MBR). Let me know and we can go from there.

---

### Post by azTom on 2008-09-01
> **caljohnsmith said:**
> azTom, please clarify: when you connect your RAID array, do you get the Grub error 17 before you get the Grub start up menu, or do you see the Grub menu, try and select an OS, and then get the error 17? I assume from what you say above you are getting the error 17 before getting a Grub menu, but correct me if I'm wrong.

Fjguade, if azTom gets the Grub error before seeing a menu, then changing his menu.lst will not help load Grub on start up. I agree with what you pointed out earlier: the device names of the HDDs are probably changing. But when you install Grub to the MBR of a drive, it hard-codes into the MBR the HDD location as (hdX,Y) where it looks for its system files, including menu.lst. So if the HDDs get moved around, like when he connects his RAID HDD, then Grub still points to (hdX,Y) even though that is probably an entirely different HDD now. Therefore, changing his menu.lst will unfortunately not fix that. :)

azTom, there are a number of solutions for your problem, but probably the best would be to install Grub to the MBR of the Ubuntu HDD and set the BIOS to always boot from that HDD. Which HDD are you booting from now? Based on the symptoms of your problem I might guess you are booting the Windows HDD first (but it has Grub installed to its MBR). Let me know and we can go from there.

I've been trying just about everything for over a week now.  I've tried Unbuntu in the primary drive position and the secondary position, each time as a NEW installation. GHrub never got to the menu window, just the error message. The latest is installing Grub in Ubuntu's primary partition.  Boots great but does not give any other OS choice.

How do I install Grub in Ubuntu's MBR, or do I install an MBR from XP's installation CD?

---

### Post by caljohnsmith on 2008-09-01
> **azTom said:**
> I've been trying just about everything for over a week now.  I've tried Unbuntu in the primary drive position and the secondary position, each time as a NEW installation. GHrub never got to the menu window, just the error message. The latest is installing Grub in Ubuntu's primary partition.  Boots great but does not give any other OS choice.

How do I install Grub in Ubuntu's MBR, or do I install an MBR from XP's installation CD?
It would be really helpful if you could post the output of the following while your RAID drive is connected (from your Ubuntu partition or Live CD, doesn't matter):
```
sudo fdisk -lu
```
Now, to install Grub to the MBR of the Ubuntu HDD:
```
sudo grub
grub> find /boot/grub/stage2
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

```
If you can set BIOS to boot the Ubuntu HDD first, you should at least get a Grub menu now; we may have to modify the entries to make them work, but see if you get this far first. 

And I would recommend not reinstalling Ubuntu any more, or we would have to start from scratch troubleshooting. If you leave it as it is, I think there's a good chance we can get everything working.

---

### Post by azTom on 2008-09-01
I'm not doing to good with this forum format, not ever sure my replies are going anywhere?

Just how do you suggest I install Grub to the MBR of the Ubuntu HDD? Or do I install a windows MBR from the XP installation CD using the Repair function?

---

### Post by caljohnsmith on 2008-09-01
> **azTom said:**
> I'm not doing to good with this forum format, not ever sure my replies are going anywhere?

Just how do you suggest I install Grub to the MBR of the Ubuntu HDD? Or do I install a windows MBR from the XP installation CD using the Repair function?
First, I don't think you want to install the Windows MBR or you'll never be able to boot Ubuntu. Grub can boot either Windows or Ubuntu, so I would think that's what you want in your HDD's MBR. The commands I gave in my last post will install Grub to the Ubuntu HDD's MBR. Just open a terminal (Applications > Accessories > Terminal), and type them in as directed. Also, post the output of that "sudo fdisk -lu" command.

---

### Post by azTom on 2008-09-01
OK So I'll be starting with a clean slate I am wipping my Ubuntu HDD clean and for the umpteenth time will do a clean install. Then reset my bios so it starts on the Primary  (Ubuntu) HDD.

Thanks for your patience with me.

---

### Post by azTom on 2008-09-01
Wipped the Ubuntu HDD secure clean and did a new install.  Another problem, when I select XP Pro, it comes up with Error #12 Invalid Device Requested.  This has happened in the past and I've tried many fixes all to no avail.  

The GOOD NEWS at least I no longer have the Raid error and does go to the Grub menu.  Now if I could only open my XP!

---

### Post by caljohnsmith on 2008-09-01
Well, if you want to get Win XP booting OK, how about posting the following first:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by azTom on 2008-09-01
Now Grub gives me 4 listings for Ubuntu, still one for XP Pro but still get the error #12 no XP

---

### Post by azTom on 2008-09-01
Hold it a minute, let me delete the 50MB partition I created for BootMagic

---

### Post by azTom on 2008-09-01
It'll take me awhile, in other words don't hold your breath.As always I screwed things up.
:confused:  See you tomorrow.

Tom

---

### Post by azTom on 2008-09-03
I'm back, had a few projects that had to be taken care of.  At bootup when I select XP Pro I still get Error #12: Invalid device requested.  At least the Raid problem has been fixed thanks to you.

---

### Post by azTom on 2008-09-03
Well, if you want to get Win XP booting OK, how about posting the following first:

Code:
sudo fdisk -lu
cat /boot/grub/menu.lst

I did enter the above in the terminal window. Still receive the Error #12 Invalid device requested.

Should I start a NEW thread as the original problem is taken care of??

---

### Post by caljohnsmith on 2008-09-03
You need to type those commands in a terminal (Applications > Accessories > Terminal) from the Ubuntu on your HDD or from a Ubuntu Live CD. They should give you a much different output than the Grub error 12 you are getting.

---

### Post by azTom on 2008-09-03
That's exactly what I did, but just in case I missed something I reentered same. I'll try to copy and paste the terminal results.
tom@Ubuntu:~$ sudo fdisk -lu
[sudo] password for tom: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001407e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   390716864   195350400    f  W95 Ext'd (LBA)
/dev/sda5           16128   390716864   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8e528e52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    74862899    37431418+  83  Linux
/dev/sdb2        74862900    78156224     1646662+   5  Extended
/dev/sdb5        74862963    78156224     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb982b982

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   126977759    63488848+   7  HPFS/NTFS
/dev/sdc2       126977760   133130654     3076447+   7  HPFS/NTFS
/dev/sdc3       133130655   312576704    89723025    f  W95 Ext'd (LBA)
/dev/sdc5       133130718   139283549     3076416    7  HPFS/NTFS
/dev/sdc6       139283613   145436444     3076416    7  HPFS/NTFS
/dev/sdc7       145436508   149645474     2104483+   7  HPFS/NTFS
/dev/sdc8       149645538   214274969    32314716    7  HPFS/NTFS
/dev/sdc9       214275033   312576704    49150836    7  HPFS/NTFS
tom@Ubuntu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=39942ff2-5a18-4134-aa1a-8d8e9d08bc32 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=39942ff2-5a18-4134-aa1a-8d8e9d08bc32 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=39942ff2-5a18-4134-aa1a-8d8e9d08bc32 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=39942ff2-5a18-4134-aa1a-8d8e9d08bc32 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=39942ff2-5a18-4134-aa1a-8d8e9d08bc32 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

tom@Ubuntu:~$

---

### Post by caljohnsmith on 2008-09-03
It looks like your Windows XP is on sdc1, is that true? Grub sometimes doesn't see the order of HDDs the same as BIOS, so your Windows entry in menu.lst that uses (hd1) may not be correct. So first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst &
```
And in at the bottom of the file where it has your Windows entry, replace it with:
```
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```
That should work unless maybe there is some issue with your RAID array.

---

### Post by azTom on 2008-09-04
THANK YOU, THANK YOU!  You have no idea how many weeks I've spent trying to resolve this on my own in addition to suggestions from the local Linux users group.  No one even mentioned the help available in ubuntuforums.org, you can be sure I'll recommend your site at the next meeting I attend.  They meet weekly.

Once again THANK YOU and God Bless You'all.

---

