---
title: "GRUB issue when attempting to boot XP from (hd0,4)"
date: 2008-08-16
forum: General Help
---

### Post by quixotic-cynic on 2008-08-16
Hello,

I am attempting to boot XP from (hd0,4) using GRUB and am experiencing difficulties.

(hd0,4) is most likely the correct partition because it is the only NTFS partition I have and GRUB identifies it as partition type 0x7 (i.e. NTFS).

It is possible that issues are arising due to it being in a logical partition. I have set the partition as active in qtparted to avoid the issue of GRUB being unable to set logical partitions as active.

Initially (hd0,0) [my 200m boot partition] was formatted by windows xp during it's installation. It has since been formatted to ext2 and GRUB is now installed on it. I have used my XP cd to copy ntldr, NTDETECT.COM, and boot.ini to (hd0,4) and run *fixboot* from the XP recovery console to ensure that the boot sector on the NTFS partition is as required.

My menu.lst entry for XP is (currently) as shown below, though I have tried several combinations.

```
title Windows XP
	map (hd0,0) (hd0,4)
	map (hd0,4) (hd0,0)
	rootnoverify (hd0,4)
	chainloader +1
	boot
```

When the "Windows XP" option is selected on boot, the commands in the code section above are displayed on screen and then the system stops responding, leaving a blinking cursor on the line below boot. E.g.:

```
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
rootnoverify (hd0,4)
chainloader +1
boot
<blink>_</blink>
```

I would be grateful for any suggestions people can give.

---

### Post by ajgreeny on 2008-08-16
I don't think windows can boot from a logical partition, it needs a primary partition and there will be no way I'm aware of to make it boot, though others may tell you of workarounds to get it to do so.

Let's see the output of ```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.lst 
```and that may help.

---

### Post by quixotic-cynic on 2008-08-16
Thanks for the reply. From what I have read I have been given the impression that others have got it to work (though it is probably inadvisable). I'm mainly trying to avoid a reformat - which I would dread at this point.

My fdisk output is:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      208813+  83  Linux
/dev/sda2            1812        9729    63601335    f  W95 Ext'd (LBA)
/dev/sda3              27        1046     8193150   a6  OpenBSD
/dev/sda4            1047        1811     6144862+  a5  FreeBSD
/dev/sda5   *        2832        4361    12289693+   7  HPFS/NTFS
/dev/sda6            1812        1875      514017   83  Linux
/dev/sda7            1876        2576     5630751   83  Linux
/dev/sda8            2577        2601      200781   83  Linux
/dev/sda9            2602        2728     1020096   83  Linux
/dev/sda10           2729        2747      152586   83  Linux
/dev/sda11           2748        2766      152586   82  Linux swap / Solaris
/dev/sda12           2767        2831      522081   83  Linux
/dev/sda13           4362        5126     6144831    b  W95 FAT32
/dev/sda14           5127        9624    36130153+  83  Linux
/dev/sda15           9625        9729      843381   83  Linux

Partition table entries are not in disk order

```

My menu.lst is:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda6 ro

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.26-1-686
root		(hd0,0)
kernel		/vmlinuz-2.6.26-1-686 root=/dev/sda6 ro 
initrd		/initrd.img-2.6.26-1-686

title		Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.26-1-686 root=/dev/sda6 ro single
initrd		/initrd.img-2.6.26-1-686

title		Debian GNU/Linux, kernel 2.6.18-6-686
root		(hd0,0)
kernel		/vmlinuz-2.6.18-6-686 root=/dev/sda6 ro 
initrd		/initrd.img-2.6.18-6-686

title		Debian GNU/Linux, kernel 2.6.18-6-686 (single-user mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.18-6-686 root=/dev/sda6 ro single
initrd		/initrd.img-2.6.18-6-686

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,0)
kernel		/vmlinuz-2.6.18-5-686 root=/dev/sda6 ro 
initrd		/initrd.img-2.6.18-5-686

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.18-5-686 root=/dev/sda6 ro single
initrd		/initrd.img-2.6.18-5-686

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
	map (hd0,0) (hd0,4)
	map (hd0,4) (hd0,0)
	rootnoverify (hd0,4)
	chainloader +1
	boot

title		OpenBSD
	root		(hd0,2)
	#makeactive
	chainloader +1

title		FreeBSD
	root		(hd0,3)
	#makeactive
	chainloader +1

```

Thanks.

---

### Post by caljohnsmith on 2008-08-16
As a general rule, I've always read that you can't boot Windows from a logical partition, but I did come across this web page that talks about [booting Windows from a logical partition]("http://www.goodells.net/multiboot/index.htm"). It's not really a how-to guide though, but it might shed some light on the issues you are facing.

I'm quite curious though, why did you put Windows on a logical partition? Were you unaware at the time of the implications that would mean for booting? I've never tried, but I think that the Windows installer would complain about being installed to a logical partition.

---

### Post by quixotic-cynic on 2008-08-16
From all I have now read, you *would* think that the XP installer would complain, right? But, er, no... it didn't unfortunately - and I did not realise that there would be problems putting XP on a logical partition (this is really the first time I have experimented with GRUB etc).

I have already read the link that you mention - it was useful in somewhat improving my understanding of the situation. Nevertheless, thank you for the suggestion.

---

### Post by logos34 on 2008-08-16
> **quixotic-cynic said:**
> 
Initially (hd0,0) [my 200m boot partition] was formatted by windows xp during it's installation. It has since been formatted to ext2 and GRUB is now installed on it. 

There's your answer right there.  

XP will install and run on a logical partition if there is either a prexisiting windows installation or a primary boot partition available, which is where it will locate the boot files.  Apparently it put them on sda1.  

So free up sda3 or 4 for a ntfs boot partition, or just install windows on one of them.

Note: you only need map lines to boot windows on a [different disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by caljohnsmith on 2008-08-16
> **logos34 said:**
> XP will install and run on a logical partition if there is either a prexisiting windows installation or a primary boot partition available, which is where it will locate the boot files.  Apparently it put them on sda1.  

So free up sda3 or 4 for a ntfs boot partition, or just install windows on one of them.

Note: you only need map lines to boot windows on a [different disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").
I'm wondering, if quixotic-cynic were to make sda1 a FAT32 partition, wouldn't it be possible to put his Windows boot files back on that partition *and* put his Grub config files there too, and let them share the partition? It seems like it would be possible since both Windows and Grub natively support the FAT32 file system. The Windows boot files would exist in the root directory and Grub's files would exist in /boot or /boot/grub, so they certainly wouldn't interfere with each other. Seems like it would work--what do you think logos34?

---

### Post by quixotic-cynic on 2008-08-16
Ok, thanks for that. 

I may move /boot and turn sda1 back into a fat32 partition... or try fixmbr and see if it works by pointing ntldr at grub (though I really don't want to try it that way round).

Incidentally, it looks as if at least 1 crazy person out there has managed what I am trying: [http://linux.derkeiler.com/Newsgroups/comp.os.linux/2004-03/0348.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux/2004-03/0348.html)

The drive mapping was a desperate experiment to get it to work - I wasn't really sure that it would do anything. ;)

Edit: The person above did it by using partition magic to edit their partition table. I'm really not sure I want to try that one...  ~.~   [see [http://www.goodells.net/multiboot/ptedit.htm](http://www.goodells.net/multiboot/ptedit.htm) if anyone is interested on this one].

Edit2: > **caljohnsmith said:**
> I'm wondering, if quixotic-cynic were to make sda1 a FAT32 partition, wouldn't it be possible to put his Windows boot files back on that partition *and* put his Grub config files there too, and let them share the partition? It seems like it would be possible since both Windows and Grub natively support the FAT32 file system.

While I know less, I was actually considering this option too -- I think I can see vaguely how to go about it.

---

### Post by logos34 on 2008-08-16
> **caljohnsmith said:**
> I'm wondering, if quixotic-cynic were to make sda1 a FAT32 partition, wouldn't it be possible to put his Windows boot files back on that partition *and* put his Grub config files there too, and let them share the partition? It seems like it would be possible since both Windows and Grub natively support the FAT32 file system. The Windows boot files would exist in the root directory and Grub's files would exist in /boot or /boot/grub, so they certainly wouldn't interfere with each other. Seems like it would work--what do you think logos34?

interesting idea..never tried it but I don't see why it wouldn't work.

---

### Post by caljohnsmith on 2008-08-16
> **quixotic-cynic said:**
> Ok, thanks for that. 

I may move /boot and turn sda1 back into a fat32 partition... or try fixmbr and see if it works by pointing ntldr at grub (though I really don't want to try it that way round).
I definitely wouldn't use fixmbr as that will replace Grub in the MBR completely with the window's MBR, and I don't think it will boot Windows anyway since you have it on a logical partition.

My point is if you make sda1 FAT32, you can keep Grub there along with your Windows boot files, and it seems like it should work in theory if I haven't missed something.

---

### Post by quixotic-cynic on 2008-08-16
Ok, thanks for everyone's input. I am going for changing /boot to fat32. Let's see if it goes boom. >:D

I have a GParted live disc (or super grub) to fix things if they go pear shaped.

//

Edit: Ok, here's what happened:
1) tried to tar /boot, format /boot to fat32 and then untar back to boot, then restart  ----> result = very bad  ^_^
Perhaps that was to be expected
2) Since boot was trashed anyway took opportunity to reinstall xp
3) XP install trashed my partition table
4) Reinstalled stuff in sane partitions - pretty much works now.

---

### Post by logos34 on 2008-08-16
> **quixotic-cynic said:**
> 
While I know less, I was actually considering this option too -- I think I can see vaguely how to go about it.

As far as /boot goes, you know you really don't need one for linux OSs--you can just use [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") or [chainloader]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader") entries in your master (ubuntu?) menu.lst.  That would simplify your dual boot with windows

---

### Post by DDurcsak on 2008-08-18
> **logos34 said:**
> There's your answer right there.  

XP will install and run on a logical partition if there is either a prexisiting windows installation or a primary boot partition available, which is where it will locate the boot files.  Apparently it put them on sda1.  

So free up sda3 or 4 for a ntfs boot partition, or just install windows on one of them.

Note: you only need map lines to boot windows on a [different disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").


Excuse me for breaking into this discussion but it seems that you (all) may have the answer that I need.

I'm trying to dual boot a machine that originally had (still has) WIN XP, but I keep getting a Fatal Error during the last part of the install process.

"Executing 'grub-install(hd0)' failed."

Should I be looking to install 'grub" at another point...there was a drop down list of locations??

Here is what I have from the list:

/dev/sda (primary HD with partitioned for both WIN and Ubuntu)
/dev/sda1 MS WIN XP
/dev/sda2
/dev/sdb (Secondary drive partitioned for WIN data and Ubuntu Swap)
/dev/sdb5


Thank you

---

