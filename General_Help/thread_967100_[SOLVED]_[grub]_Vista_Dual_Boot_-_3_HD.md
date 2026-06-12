---
title: "[SOLVED] [grub] Vista Dual Boot - 3 HD"
date: 2008-11-01
forum: General Help
---

### Post by pofigster on 2008-11-01
I'm not sure if this really is the best place to put this...
I'm a devoted user of Ubuntu, but, I bought a iPod Touch, so I really wanted to have iTunes to make the process of getting music and stuff onto it as seamless as possible.  So, I bought Vista (for $15, much against my own sense).  I installed Vista onto the SATA drive connected to the second SATA port (hdb).  I have /boot, /, and swap installed on hda (partitions are in that order) and /home on hdc - all drives are SATA.  My motherboard (ASUS M2A-MVP) has a RAID chip in it and hdb (Vista) and hdc (/home) are both set up as individual RAID 1+0 (the result of a failed attempt to get get a RAID 1 set up with both drives).

When I installed 8.10 it detected Vista and added an entry to GRUB - but it doesn't work.  It says "Starting Up..." (or whatever it says when you make a selection) and just sits there.  For minutes.  Nothing happens.  Below is the original GRUB entry:
```

title        Windows Vista
savedefault
root(hd1)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```
So, I changed a couple of things and tried:
```
title        Windows Vista
savedefault
map        (hd0,0) (hd1,0)
map        (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader    +1
boot
```
As well as:
```
title        Windows Vista
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader    +1
boot
```
And a couple of other variations.  Still the same result.  Any idea on why GRUB won't boot into Vista?
I know that I can just change the HD boot order in the BIOS, but my wife uses the computer too and while she could learn to do that, it's easier to stick with teaching her CLI in Ubuntu and not worrying about BIOS stuff yet.

---

### Post by caljohnsmith on 2008-11-01
First, have you confirmed you can still boot Vista OK by changing your BIOS to boot it first on start up? Also, please post the following:
```
sudo fdisk -lu
```
Also, when you reboot and get the Grub menu, press "c" to get the grub command line, and then enter:
```
grub> geometry (hd
```
And press TAB for tab-completion, and you should see a list of all your drives like (hd0), (hd1), etc. For each of your drives, do:
```
grub> geometry (hd0)
```
And also replace (hd0) with (hd1) and however many other drives you have. That will show you the partition structure and size of each HDD, so from that try to figure out which (hdX) is Vista's HDD. Let me know and we can work from there. :)

---

### Post by pofigster on 2008-11-01
Yes, by changing the first HD in BIOS I can still boot into Vista (done it several times already).

sudo fdisk -lu returns the following:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00063492

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      481949      240943+  83  Linux
/dev/sda2       144585000   156296384     5855692+  82  Linux swap / Solaris
/dev/sda3          481950   144584999    72051525   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000de189

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   310520384   155260161    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006687b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   312576704   156288321   83  Linux

```

I'll get back to you on the geometry thing.

---

### Post by pofigster on 2008-11-02
Ok, so,
grub> geometry (hdX)
confirms that hd1 is the Vista drive.  The output it gave said that it was an unknown file system type even though everything else seems to detect that it's NTFS.

---

### Post by meierfra. on 2008-11-02
> grub> geometry (hdX)
confirms that hd1 is the Vista drive. 

Just to make sure:  You did this after pressing "c" at the grub menu at boot up?  (And not after "sudo grub" in an Ubuntu terminal)



Try these (you can put them all on menu.lst at the same time and later deleted the once which did not work)


title        Windows Vista
rootnoverify (hd1)
chainloader    +1


title        Windows Vista
rootnoverify (hd1)
map (hd1) (hd0)
chainloader    +1

title        Windows Vista
rootnoverify (hd1)
map (hd0) (hd1)
chainloader    +1


title        Windows Vista
rootnoverify (hd1,0)
chainloader    +1


title        Windows Vista
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

---

### Post by pofigster on 2008-11-02
Yes, you are correct - I obtained the information from the actual GRUB bootloader after pressing 'c' - not from the CLI in Ubuntu.

I'll try the whole list and see if any of them provide any new insight.  Thanks!

---

### Post by pofigster on 2008-11-04
Ok, I tired all 5 of those and none of them worked :(

It may be worth noting, that attempting to set up dual boot from Vista's end doesn't work either.  When I try and access Linux it complains that there is no systemdisk found and wants  me to insert one.

---

### Post by caljohnsmith on 2008-11-04
That's strange you can't boot Vista from Grub, but as far as booting Ubuntu from Vista, have you given EasyBCD a try? Here are two links that I think will help with that:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Also, you could try changing the BIOS settings related to your HDDs and see if that makes it possible to boot Vista from Grub. Look for settings in your BIOS like "auto-detect", LBA, CHS, RAID, AHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. You could change them one at a time, and see if it makes any difference to boot Vista from Grub. I would recommend writing down any settings you change though so you can revert back to the original settings if necessary. You might also want to check the manufacturer's website of your motherboard to see if there is a newer BIOS version available. 

Good luck and let us know how it goes.

---

### Post by TeXtonyx on 2008-11-04
pofigster wrote: "It may be worth noting, that attempting to set 
up dual boot from Vista's end doesn't work either. When I try and
access Linux it complains that there is no systemdisk found and 
wants me to insert one."

TeX: I agree with caljohnsmith's suggestion to try Easybcd.

[http://neosmart.net/blog/2006/easybc...-mac-os-x-bsd/](http://neosmart.net/blog/2006/easybc...-mac-os-x-bsd/)
"You can&#8217;t get much simpler than this. With our new release of EasyBCD 1.5, booting into Linux, Mac OS X, or BSD straight from the Vista bootloader without ever having to add a single line of code reconfigure a thing is but a touch away!

-------------------------

I would bet, 10 to 1, that the method described below will work.

[http://port25.technet.com/archive/20...M-Support.aspx](http://port25.technet.com/archive/20...M-Support.aspx)

Step 1 &#8211; Install GRUB on the Linux partition (outside of MBR)

As Windows Vista will replace the Master Boot Record (MBR) with its own, we need to relocate GRUB elsewhere by running grub-install with the Linux partition as a parameter.

&#8226;        On Linux, launch a Terminal with root privileges

&#8226;    Find the name of the partition Linux is installed on by running fdisk &#8211;l (the partition you&#8217;re looking for is the one whose system is Linux, can be  something like /dev/sda1 or /dev/hda1. For the rest of this post, I&#8217;ll use /dev/sda1)

&#8226;    Install GRUB on the Linux partition by running : grub-install /dev/sda1

"Step 2 &#8211; Get a copy of Linux boot sector

We will need to instruct Windows Boot Manager how to boot correctly Linux using Linux boot sector, which we will extract using dd.

&#8226; On Linux, launch a Terminal with root privileges

&#8226; Take a copy of Linux boot sector : dd if=/dev/sda1 of=/tmp/linux.bin bs=512 count=1

&#8226; Copy linux.bin on a FAT formatted USB key or any storage accessible from Windows Vista"

"Step 4 &#8211; Configure dual booting in Windows Vista
&#8226; Copy Linux boot sector on the root of the Windows boot (active) partition, namely the one containing bootmgr. If you don&#8217;t know for sure you can use diskpart or diskmgmt.msc to find out which one it is.

&#8226; Create an entry for GRUB :

o bcdedit /create /d &#8220;GRUB&#8221; /application BOOTSECTOR

o Note: bcdedit will return an ID for this entry that we will call {LinuxID} below. You will need to replace {LinuxID} by the returned identifier in this step. An example of {LinuxID} is {81ed7925-47ee-11db-bd26-cbb4e160eb27}

&#8226; Specify which device hosts a copy of the Linux boot sector

o bcdedit /set {LinuxID} device boot

&#8226; Specify the path to a copy of the Linux boot sector

o bcdedit /set {LinuxID} PATH \linux.bin

&#8226; Add Linux entry to the displayed menu at boot time

o bcdedit /displayorder {LinuxID} /addlast

&#8226; Let the menu be displayed 10 seconds to allow for OS selection

o bcdedit /timeout 10

--------------------------------------

TeX: LinuxReader is a free program that conveniently saves files
like linux.bin, from Ubuntu /boot to the Vista root partition C:\

After Step 1, installing grub to sda, (outside of MBR) I would
use Super Grub disk to boot that partition, (hd0,0) I think, to
check that the settings and linux.bin are correctly used before
having Vista rely on them. 

The command prompt in Vista has a little icon at the left-top.
Clicking on this drops down a menu where you mark text to later
paste. If you already have content in the buffer, then under Edit
one can choose paste to put that content into the command line.
That gadget doesn't look too helpful for pasting the bcdedit 
commands in this case. Also in Vista one can assume Administrative
command line rights in case there is any problem editing the bcd file 
with bcdedit. I've also seen other instructions for reinstalling grub.

---

### Post by caljohnsmith on 2008-11-04
> **TeXtonyx said:**
> 
I would bet, 10 to 1, that the method described below will work.

I'm willing to take that bet, but I would bet that the method you describe will unfortunately not work as you've written it: :)
> **TeXtonyx said:**
> 
•    Install GRUB on the Linux partition by running : [COLOR="Red"]grub-install /dev/sda1[/COLOR]

"Step 2 – Get a copy of Linux boot sector

We will need to instruct Windows Boot Manager how to boot correctly Linux using Linux boot sector, which we will extract using dd.

• On Linux, launch a Terminal with root privileges

• Take a copy of Linux boot sector : [COLOR="Red"]dd if=/dev/sda1 of=/tmp/linux.bin bs=512 count=1[/COLOR]

The method you describe above will only work if the Linux boot sector that you copy is on the same HDD as Windows; if Linux is on a different HDD, you have to install Grub to the boot sector in a special way so that when you move the boot sector to the Windows drive, the boot sector will correctly point to the external drive. If you use the method above, Grub will point to the same drive it is on, so moving the boot sector to the Windows drive won't work. 

I unfortunately learned all of that the hard way myself, but if you don't believe me, feel free to try. :)

---

### Post by TeXtonyx on 2008-11-04
caljohnsmith wrote: The method you describe above will only work if the Linux boot sector that you copy is on the same HDD as Windows; if Linux is on a different HDD, you have to install Grub to the boot sector in a special way so that when you move the boot sector to the Windows drive, the boot sector will correctly point to the external drive. If you use the method above, Grub will point to the same drive it is on, so moving the boot sector to the Windows drive won't work.

I unfortunately learned all of that the hard way myself, but if you don't believe me, feel free to try."
------------------------------------------------

You wrote that before and I responded that it worked on two of my
computer systems each of which has two drives, and I've seen a web
reference. But I can't remember if I used dd with two drives 
installed, perhaps I just tested dd for dual booting on just one drive.
That is because I switched to Bootpart, which is much easier. 
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Although it doesn't say Vista, it works for Vista to create a 
512 byte segment which boots from a second drive. The method for
XP, writing to boot.ini doesn't apply. I used to think Bootpart
was the same thing as the dd method, but in a discussion with
meierfra, I learned they are not the same thing. 
I'm using the 512 bytes created by Bootpart to boot my second
drive which has Ubuntu installed on this computer I'm typing from.

Well, ok, I will try it now, shouldn't take too long, and I will
report the result back to this thread promptly.

EDIT: I just realized I'm downloading a large file so I'll find 
out after the download completes. Also I used sda in this example
because that is where the OP has Linux installed. I have Ubuntu
installed on the second drive, sdb, so will use that for dd.

---

### Post by meierfra. on 2008-11-04
Just a few more options:

title Windows Vista
rootnoverify (hd0)
map (hd0) (hd1)
chainloader +1


title Windows Vista
rootnoverify (hd0)
map (hd1) (hd0)
chainloader +1


title Windows Vista
rootnoverify (hd0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Sorry, for giving you this many options, but in my experience, if raid is involved, it is pretty much impossible to predict what  the correct parameters are.

If none of this works, I agree with caljohnsmith and tex: give eascybcd a try.

---

### Post by TeXtonyx on 2008-11-04
Well, the dd method did not work I just got a GRUB screen.
The first time I posted those bcdedit instructions, I added
the following remark in Re: Moving GRUB location? #25

"TeX: This was the same method I used earlier, only with XP
and boot.ini, before I discovered Bootpart." 

So I switched back to the Bootpart created Ubuntu.bin and it works to
access the second hard drive still. I had tried to install Mandriva on hdb
in a fat32 partition, I supposedly formatted the fat32 partion with ext 3.
The install failed and checking later the fat32 partition was still fat32.

But Bootpart didn't work now and reported: Loading New Partition
Cannot load from hard disk. Similar to the error reported by the OP.

So you are correct, the dd method does not work. But the Bootpart method
does work. I'm using it now in Ubuntu on my second drive. Bootpart 
presents a list of drives and partition with their types which makes it
easy to choose the right partition to create the linux.bin. Real evidence
that dd and Bootpart don't work the same way.

I hope that one of those last three menu.lst entries suggested works.

I got a free coffee from Starbuck's for voting. Ain't America great.

---

### Post by TeXtonyx on 2008-11-05
I wondered why I was suffering from such a wrong impression about
the equivalence of dd and Bootpart.

--------------------------------------------

[http://www.linux.com/feature/113945](http://www.linux.com/feature/113945)
Convert a Windows system to dual-boot Linux on a second drive ...

Boot sector transplant

"The next step in the process is to save a copy of the Linux boot 
partition. *This can be done either with dd in Linux or with the 
free Bootpart utility under Windows. Either program simply takes 
the first 512 bytes on the disk and puts them into a file.* The 
dd command to do this is dd if=/dev/hdb1 of=bootsect.lnx size=512 
count=1. Once you have this file, copy it to a diskette or some 
other removable media so you can then copy it to the Windows 
drive for NTLDR. 

I happened to use Bootpart because I forgot to use dd before I 
booted the system back to Windows. If you use Bootpart you don't 
have to copy the boot sector to a diskette, as you are already in
Windows. To complete the transplant, place the file you created 
*with dd or Bootpart on the Windows drive as C:\bootsect.lnx.*" 

----------------------------------------------

[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)

Configuring A Dual-Boot Windows2000/XP & Linux System

cd \bootpart
bootpart

When you run it, you get a report similar to the one below:

Physical number of disk 0: ffff6a32
0 : C:* type=42 , size=22659651 KB, Lba Pos=63
1 : C: type=42 , size=17358232 KB, Lba Pos=45319365
Physical number of Disk 1 : ca1dca1d
2 : D: type=83 <Linux native>, size=6184993 KB, Lba Pos=63
3 : D: type=82 <Linux swap>, size=522112 KB, LBA Pos=12370050
4 : D: type=83 <Linux Native>, Size=1542240 KB, LBA Pos=13414275

---------------------------------------------

In this example whose purpose was to demonstrate how Bootpart
worked, there is a disk 0, and a Disk 1, two hard drives. It does
not say that dd and bootpart are equivalent. However, the first
webpage is rather emphatic about saying dd and bootpart are the
same, "Either program simply takes the first 512 bytes on the 
disk and puts them into a file."

One would think linux.com would be a reliable source of information.
And if majorgeeks.com wanted to feature the advantages of Bootpart,
it should have pointed out that the dd command was ineffective
in the context of two hard drives which its example displayed,
but that Bootpart bypassed this limitation of dd.

It just goes to show you, never trust authority. Anyway, I figure
that ten to one on a dime is a dollar, the price of a cup of coffee 
at Starbuck's which I mentioned was free yesterday.

---

### Post by TeXtonyx on 2008-11-06
Well, I got dd to work.

Drive 0 = WinXP + Ubuntu

Drive 1 = Vista + Ubuntu

I used dd to copy the 512 bytes of the Ubuntu boot sector to ubiwan.bin
That gives me the option to boot Vista. In Vista I repeated dd to get the 
512 bytes of Drive 1 Ubuntu /boot (linux.bin). I followed the instructions 
to manually (bcdedit) add Ubuntu on hd1 to the Vista bootloader options:

There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 10 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  GRUB
BCD ID:  {7b1c2e71-ab94-11dd-869f-000c7613bf91}
Drive: Active Boot Partition
Bootloader Path:  \linux.bin

That works if I change the  bios to boot Vista first.

Since I have WinXP booting 1st normally, I choose Ubiwan to boot Vista
on the grub menu.lst. Then selecting Vista lets me choose to boot Vista
or Grub which is the name for Ubuntu on the second drive. Easybcd only
made a working entry for NeoSmart Linux when I booted directly to Vista.
The GRUB title and the NeoSmart Linux title point to the same Ubuntu hdb5
so I don't know why Ubuntu only worked for both methods using linux.bin,
which is the dd created entry for Ubuntu on hd1, grub installed to /boot.
Maybe because dd works when it is invoked from the active boot drive.

EDIT: But, booting Vista (hd1) and picking the Ubu.bin
created by dd, for Ubuntu located on drive 0, doesn't work.

---

### Post by pofigster on 2008-11-09
Wow, this thread exploded while I was gone - I thought I was supposed to get email notifications...

Ok, first off, I had already used EasyBCD (or whatever it was called - it was using this method that got me the error I reported)

I got GRUB to boot into Vista properly.  All I had to do was change my settings so that instead of RAID the BIOS set up the hard drives as AHCI.  I dunno...it was kinda weird.

Thanks for all the help everybody!

---

