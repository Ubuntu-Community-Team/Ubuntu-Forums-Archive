---
title: "Problem installing XP in a dual-boot"
date: 2008-08-18
forum: General Help
---

### Post by Rixii on 2008-08-18
I'm attempting to install XP so that I can dual-boot. I have my most important files backed up but I can't back up everything, and even if the other files aren't important, I'd rather not have to get them back. It would  take quite a while. So until I have a large enough disk to back everything up, installing XP first is out of the question.

This guide:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4)
is the only one I can find on dual-booting with Ubuntu already installed. I can create space and everything up to this point, but the page I link to is the problem. XP won't even recognize the two partitions of Linux.

It says I have 131000+ MB in unpartitioned space - this makes no sense. My hard drive is 750 GB (only half of he Ubuntu partition is filled). The unpartitioned space I've set aside for XP is only 20 GB. What's going wrong?

---

### Post by Rixii on 2008-08-18
Anyone have any ideas?

---

### Post by PGScooter on 2008-08-18
Hi Rixii, this sounds like a job for supergrub:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It is normal that xp doesn't recognize the linux partitions.. there are tools that you can use to read ext* partitions, but I don't think that would help XP to recognize them at boot. But don't worry, your data is still there.

I have actually seen quite a few guides on this as it is a pretty common manoeuver.

In any case, I think that supergrub should be able to fix everything.

good luck!

---

### Post by Rixii on 2008-08-18
> **PGScooter said:**
> Hi Rixii, this sounds like a job for supergrub:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It is normal that xp doesn't recognize the linux partitions.. there are tools that you can use to read ext* partitions, but I don't think that would help XP to recognize them at boot. But don't worry, your data is still there.

I have actually seen quite a few guides on this as it is a pretty common manoeuver.

In any case, I think that supergrub should be able to fix everything.

good luck!

To be clear, will supergrub help me install XP? I haven't installed XP and still have just ubuntu with the small unpartitioned space set aside. Or should I just install XP and then use supergrub to restore the normal booting.

---

### Post by caljohnsmith on 2008-08-18
Super Grub Disk won't help you install Win XP. If your Win XP doesn't correctly recognize the space you set aside for it, I would try using gparted to go ahead and format the Win XP partition to NTFS format, and make sure it is a primary partition by the way. Then see if the Win XP installer likes that better. You should use gparted from your Live CD as you need to have your HDD completely unmounted. You can find gparted under the System > admin > Partition Editor I think, or just run it from a terminal with:
```
gksudo gparted
```
Also, when you install Win XP it overwrites your HDD's master boot record, and there is nothing you can do about it. Thus you will need to go through a few simple steps to reinstall Grub. We can help you do that.

---

### Post by Rixii on 2008-08-18
> **caljohnsmith said:**
> Super Grub Disk won't help you install Win XP. If your Win XP doesn't correctly recognize the space you set aside for it, I would try using gparted to go ahead and format the Win XP partition to NTFS format, and make sure it is a primary partition by the way. Then see if the Win XP installer likes that better. You should use gparted from your Live CD as you need to have your HDD completely unmounted. You can find gparted under the System > admin > Partition Editor I think, or just run it from a terminal with:
```
gksudo gparted
```
Also, when you install Win XP it overwrites your HDD's master boot record, and there is nothing you can do about it. Thus you will need to go through a few simple steps to reinstall Grub. We can help you do that.

Yes, that was my problem. Originally, I had tried that. It was formatted to NTFS but the same thing was happening. So I went back in the guide and tried leaving it unformatted, and it still doesn't work. That's why I'm confused, because I've used gparted before and from what I can tell I'm following the directions correctly..

---

### Post by caljohnsmith on 2008-08-18
Would you mind posting a screen shot of your gparted window? I just want to see what it actually shows. Also, when you boot the live CD, run the following command in a terminal and post the results:
```
sudo fdisk -lu
```

---

### Post by Rixii on 2008-08-18
```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       87032   699076507+  83  Linux
/dev/sda2           89724       91201    11872035    5  Extended
/dev/sda5           89724       91201    11872003+  82  Linux swap / Solaris

```

[IMG]http://img.photobucket.com/albums/v366/ShisouIkari/Screenshot-1.png[/IMG]

The attached image should be the screenshot, and that's my fdisk output

---

### Post by caljohnsmith on 2008-08-18
I don't understand what you meant earlier, because according to gparted you have 20 GB of unallocated space after sda1. In gparted, can you select it, set it up as a primary partition, and format it as NTFS?

---

### Post by Rixii on 2008-08-18
> **caljohnsmith said:**
> I don't understand what you meant earlier, because according to gparted you have 20 GB of unallocated space after sda1. In gparted, can you select it, set it up as a primary partition, and format it as NTFS?

Yes I can. Like I said, I tried that the first time. Should I try once more in case something went wrong?

On another note..my XP CD is not my original one which seemingly was lost a year or two ago. The one I'm using is a copy from a friend in the industry. It has only SP1 on it, though I have another CD with SP2 that I would always use right away.. Could it have something to do with a difference between SP1 and SP2?

EDIT: I know what windows was doing when I got to the install screen, it doesn't detect more than 120 GBs of a drive, so it was detecting my entire drive..I forgot about that. Is that it then? It can't read farther than that so it can't see my open space? Should I move the space in front of my ubuntu patition?

---

### Post by caljohnsmith on 2008-08-18
If you can set it up as a primary partition, format it to NTFS in gparted, and it doesn't work, what kind of errors is it giving you? Or does gparted show that it successfully formats the partition to NTFS, but when you close and reopen gparted it is shown as unallocated space?

---

### Post by Rixii on 2008-08-18
> **caljohnsmith said:**
> If you can set it up as a primary partition, format it to NTFS in gparted, and it doesn't work, what kind of errors is it giving you? Or does gparted show that it successfully formats the partition to NTFS, but when you close and reopen gparted it is shown as unallocated space?

It successfully formats it and shows that it is formatted when reopened, albeit with the traditional 7.81 MB left unpartitioned. (unallocated I should say)

In case you didn't see my edit to my last post, I've always had to use Norton Partition Magic to get windows to see more than 120GBs of my drive after I installed Windows. Do you think that's the problem?

---

### Post by caljohnsmith on 2008-08-18
> **Rixii said:**
> It successfully formats it and shows that it is formatted when reopened, albeit with the traditional 7.81 MB left unpartitioned. (unallocated I should say)

So if gparted shows that unallocated space as successfully partitioned and formatted to NTFS, what about that screen shot from your post #8? In that screen shot, gparted shows 20 GB of unallocated space. So am I misunderstanding something?
> 
In case you didn't see my edit to my last post, I've always had to use Norton Partition Magic to get windows to see more than 120GBs of my drive after I installed Windows. Do you think that's the problem?
If Windows only detects approximately the first 120 GB of your drive, I would try moving the Windows partition in front of the Ubuntu partition like you mentioned before--put it at the very beginning of the HDD. I'll bet that will solve the problem.

---

### Post by Rixii on 2008-08-18
> **caljohnsmith said:**
> So if gparted shows that unallocated space as successfully partitioned and formatted to NTFS, what about that screen shot from your post #8? In that screen shot, gparted shows 20 GB of unallocated space. So am I misunderstanding something?

If Windows only detects approximately the first 120 GB of your drive, I would try moving the Windows partition in front of the Ubuntu partition like you mentioned before--put it at the very beginning of the HDD. I'll bet that will solve the problem.

Ahh, I had previously deleted the partition to start over. I reformatted it after I showed you the screen shot and it is working fine. Sorry, it's normal for me to confuse people :P

I am moving the partition to the beginning of my drive now. I'll let you know either if I get Windows installed or if it doesn't work.

---

### Post by Rixii on 2008-08-19
Well, it still doesn't work, so I guess I'll wait until I can back everything up and install Windows first; unless anyone else has suggestions? Thanks for your help.

---

### Post by TeXtonyx on 2008-12-13
> **Rixii said:**
> Well, it still doesn't work, so I guess I'll wait until I can back everything up and install Windows first; unless anyone else has suggestions? Thanks for your help.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4)

Page 4 - Install Windows XP
Please see first screenshot below on the left.

--------------------------------------------------

"Unfortunately XP isn't so adaptive at handling existing 
partitions during installation. It detects the two Ubuntu 
partitions and marks then C: and E: accordingly. The remaining 
unpartitioned space which is available for XP will be marked as F: 

For the operating system and the vast majority of Windows 
applications which have properly-coded installation scripts, 
this is not a problem. Some older applications will assume that 
C: is the system partition and may bring up errors. There are 
ways of changing the drive letter assignation of the system 
partition, but in this scenario it's strongly discouraged." 

---------------------------------------------------------

Please see second screenshot below on the right, under it says
"To insult to injury, XP detects the Linux partition as an 
active system partition and won't install unless it marks this 
partition as inactive." 

--------------------------------------------

This is the same page that you linked to on the first page of 
this thread. Did you get something like the predicted displays
during your installation?

------------------------------------

"Windows XP manufactured prior to August 2002 has a native 
limitation of 137GB"...

"Windows XP SP1 includes 48-bit LBA support for ATAPI disk 
drives. With this support, you can use hard disks that are 
larger than the current 137 GB limit. By default, support is 
enabled in SP1."

"To determine if you have the latest ATAPI driver, verify that 
you have version 5.1.2600.1135 or later of the Atapi.sys file 
in your %systemroot%\system32\drivers folder."

--------------------------------------

The install guide you are using is updated to SP3 and 8.04. But
I think that if your XP cd is slipstreamed with SP1, that is 
supposed to be good enough. Nonetheless, I would borrow your
friends XP with SP2 and check your result, does it repeat what
you now see or is it like the XP install guide page 4? If the XP 
SP2 install duplicates what you've already seen, I think it is 
another problem. You don't have to complete the install if the 
XP SP2 install cd works; I'm trying to simplify troubleshooting.
According to the guide, that 20.62GB unallocated space should be F:

---

