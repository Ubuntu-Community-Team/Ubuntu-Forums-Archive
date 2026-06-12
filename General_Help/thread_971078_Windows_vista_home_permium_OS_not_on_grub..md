---
title: "Windows vista home permium OS not on grub."
date: 2008-11-04
forum: General Help
---

### Post by robofighter on 2008-11-04
When I first installed the ubuntu operating system from the live cd to my aspre 5610z laptop. On the partition table it hung at 0% for a long time and would not advance. Do I had to quit from it and then I restarted my computer.

Then after I booted up nothing came on the screen but a blinking text that would only beep if I types anything. I rebooted it again and went through the bios to set it to boot from cd first and then selected install ubuntu. Then I installed ubuntu with no problems that time but was able to figure out the partition and set it to 15% of my hard drive.

Now when I restated it again I find out that my windows vista os is missing from the Grub (or what ever it is called) and I find a windows XP os that when I went to it. It showed the acer recovery management and I tried to activate but it required the password and I forgot what is was (even tried the default of 000000) However ubuntu is still working fine.

Can anyone help me figure out how to get the vista operating system back. Any important data I had was backup before installing ubuntu, But I don't have a system recovery disk

---

### Post by alberto ferreira on 2008-11-04
In the terminal what's the output of :
```
sudo fdisk -l
```

Also, do:
```
sudo grub
```
From here type:
```
root (
```
then press TAB twice and post the results also.

---

### Post by robofighter on 2008-11-04
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x407c676d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12035    96671106   12  Compaq diagnostics
/dev/sda2   *       12036       14593    20547135    5  Extended
/dev/sda5           14221       14593     2996091   82  Linux swap / Solaris
/dev/sda6           12036       14123    16771797   83  Linux
/dev/sda7           14124       14220      779121   82  Linux swap / Solaris

Partition table entries are not in disk order






grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x12
   Partition num: 4,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type unknown, partition type 0x82

---

### Post by robofighter on 2008-11-04
Beat
up
mary
poppins

---

### Post by Monotoko on 2008-11-04
Hmm, it appears /dev/sda3 and /dev/sda4 are missing
as well as XP and Ubuntu, leads me to believe those two were on those partitions.

From the looks of that fdisk output, it appears Windows no longer exists, either you have accidently deleted the partition, or something went very wrong, it might still be there hidden away, im not sure as it is not an area im very confident in.

---

### Post by robofighter on 2008-11-04
Ok then Is there a way to recovery the password for acer recovery. So I can atleast reset it back to factory defaults.

---

### Post by Sef on 2008-11-04
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk_Download").  It might be able to help you.

---

### Post by robofighter on 2008-11-05
I download the linux version of  Test Disk and I have no idea how to even activate the program.


Also what should I do in test disk to get back windows or get the lost password for acer recovery.

---

### Post by robofighter on 2008-11-06
bring
up
my
post

---

### Post by TeXtonyx on 2008-11-06
I doubt that there is a way to recover the password. But if you 
call Acer support they could tell you for sure. If the laptop is
registered to you maybe you can get them to send you a recovery cd.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

That is the online documentation for TestDisk. There is no certainty
that any recovery program will recover your lost partitions. Your User Guide,

[http://www.acerpanam.com/synapse/data/7117/documents/](http://www.acerpanam.com/synapse/data/7117/documents/) [put in one line]
AS5680_5650_5630_5610_5610Z_3690-ENG-OLM_0227.pdf     [<--------------]
when you paste into your browser.

---

### Post by robofighter on 2008-11-07
hmm I called acer but I do not what to pay 125 bucks AND ship my laptop halfway across the nation.

I heard from another forum that acer has their password stored on a hiden parition. Do you know if I can access it. I think it might be on one of those paritions that linux picked up. However the system is only picking up filesystem. Is there a way I can manually access that parition look for the text file that would have the password stored on it.

---

### Post by TeXtonyx on 2008-11-07
Here is a link with some instructions about using Testdisk
[http://georgia.ubuntuforums.org/showpost.php?p=6107798&postcount=3](http://georgia.ubuntuforums.org/showpost.php?p=6107798&postcount=3)

I've never accessed a hidden partition from any manufacturer, though
I've only tried a couple of times. The other problem is that the
password is likely to be stored in encrypted format on the hidden partition, 
not what you would type in. 
Did you ask Acer about a recovery cd? For HP, they contain the same
files as are found in the hidden partition. The recovery cd won't
have a password. Also these recovery installs use the whole drive. 
Read below to see why I think a recovery cd is the option.

[http://ask.metafilter.com/43147/Help-Me-See-Whats-In-The-Hidden-Partition](http://ask.metafilter.com/43147/Help-Me-See-Whats-In-The-Hidden-Partition)
posted by Gerard Sorme at 7:27 PM on July 27, 2006

"I went through this exercise on a friend's Packard Bell iMedia desktop machine. It was a pain in the ****.

The first thing I did was stick a spare hard disk drive on the same IDE cable, and use the Trinity Rescue Kit to make a block-for-block backup of the existing disk; because I knew that without one, I'd stuff things up totally. In fact I had to restore from that backup twice.

What I found on the recovery partition (which was marked with partition type 0x1C, "Hidden FAT32 (LBA)", which stops Windows from mounting the partition but doesn't stop Linux) was a DOS-based automated reformat and recovery system. The Windows image, the pre-installed apps and drivers were not easily accessible; they were all compressed and archived into bizarrely numbered files in some password-protected format (I forget which one, but I didn't have either a decompressor or any reasonable way to find the password in any case)."

---

### Post by robofighter on 2008-11-07
ok I was able to use testdisk to get the password for erecovery. I was able to use the restore factory settings on the computer.

The drive ACER has now appeared on places on my ubuntu places. BUT now when ever grub loads there is a error 17 that appear so I will have to put it up through the live ubuntu cd. Any help?

---

### Post by TeXtonyx on 2008-11-08
> **robofighter said:**
> ok I was able to use testdisk to get the password for erecovery. I was able to use the restore factory settings on the computer.

The drive ACER has now appeared on places on my ubuntu places. BUT now when ever grub loads there is a error 17 that appear so I will have to put it up through the live ubuntu cd. Any help?

TeX: I certainly am amazed! I did not think you could obtain the
password for the hidden partition. I guess I have to retract this
previous remark:

"I doubt that there is a way to recover the password. 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
That is the online documentation for TestDisk. There is no certainty 
that any recovery program will recover your lost partitions." 

And then in post #11 of this thread I spent 99% of it explaining
why you couldn't recover the password. Then I made another error,
I said that if you did reinstall from the hidden partition, that
it would reinstall over the whole drive, erasing the Ubuntu
partitions. But you report that you got a grub error 17 and I
didn't think grub would be around. I thought Vista, which was on
the hidden partition would have overwritten the MBR and booted
directly to Vista without ever a grub error being possible.

Obviously, I'm not qualified to help you. I'm 60, and you know
the saying, you can't teach an old dog new tricks. I'm still stuck
in the delusion that any password you recovered was for Cmos.

---

### Post by robofighter on 2008-11-08
I saw on another forum where acer hides the password in the in the hidden partions. Then I used test disk to search for the partition that list the files. Then I used it to copy the file that stored the password to the home folder. Then of course read the file.

But I am stilling getting that error 17. I would also like to mention that the DATA partition did not appear on the places, which was the other partition that the computer before installing ubuntu. However only windows is in the acer drive (C:)

update:

I just installed ubuntu back on by machine and now windows vista has appeared on grub. But is said (loader) on the end and showed an error message. error 12 if I remember right.

---

### Post by TeXtonyx on 2008-11-08
[http://ubuntuforums.org/archive/index.php/t-464695.html](http://ubuntuforums.org/archive/index.php/t-464695.html)

This thread covered your problem. So my comments assume you've
read the thread, which I'll summarize.

You didn't answer my question about booting into Vista after you
restored it from the hidden partition, _and_ before reinstalling
grub. One just can't assume these things work without testing.

So when you restore Vista it writes to the MBR and it doesn't
know about Ubuntu. Vista has a free program called Easybcd that
you can download and it will add Ubuntu (easy directions) to the
Vista bootloader, it will add Ubuntu to your Vista boot options.

Now, since you've installed Ubuntu again, Ubuntu is lodged in the
MBR and Vista can't boot by default. One approach is to use the
fixmbr and fixboot mentioned in the thread above. I think both 
are on the Testdisk choices. They are also on Super Grub Disk
which is an excellent little program to have. 

So you can use fixmbr and fixboot to fix Vista and then use 
Easybcd to add Ubuntu. In that case you should reinstall grub
to the /boot partition of Ubuntu. Now you can boot either Vista
or Ubuntu if one OS fails, they don't depend on each other. 
One way to do this is at step 7, Advanced, to choose to install
grub to /boot partition, not to the MBR. You can also do this
with a grub reinstall using the Ubuntu 83 ext3 partition that
you know from running sudo fdisk -l.

Another way is to read the thread and figure out how to fix the
menu.lst file so that grub correctly points to the Vista partition.
If you get a Windows error message, then you know that grub has
properly chained to the Vista bootloader, but there is something
wrong with the Windows install or partition. Some people would
prefer this approach.

Besides the fixmbr and fixboot method, you could, reinstall from
the hidden partition again. Make sure Vista is working by booting
from it. Download Easybcd. Reinstall Ubuntu and put grub in the
/boot partition in Step 7 Advanced. Boot Vista, you won't be
able to boot Ubuntu yet. Add Ubuntu to the Vista bootloader with
Easybcd. Now you can boot either OS. If either OS fails, you can
still boot the other OS (Ubuntu from Super Grub is useful). 

You will probably learn more by going through the process that
is reported in the thread url provided at the top of this post.
Good luck. In menu.lst you can change the title XP to Vista. 
The important part is to get the other info right.

---

