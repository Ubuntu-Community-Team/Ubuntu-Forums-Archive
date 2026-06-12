---
title: "NTFS partitions corrupt after installing grub"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by chopsuwe on 2009-07-27
I was trying to add Ubuntu (actually Mint linux - it's the same process) to Vista's boot manager in my triple boot system (Vista - main os, Windows7 and Mint Linux). Now Vista and it's partition shows up as RAW instead of NTFS. I would like to fix this without reinstalling Vista as my DVD only has the option to erase the entire hard drive during the install, killing off my all files partition in the process.

Booting from the Mint live cd gparted shows all the partitions as they should be and sudo fdisk -l gives me this:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1276        4471    25671870    7  HPFS/NTFS
/dev/sda3            4472       19521   120884212    7  HPFS/NTFS
/dev/sda4           27014       30401    27214110    f  W95 Ext'd (LBA) 
/dev/sda5           27146       29185    16386300    7  HPFS/NTFS
/dev/sda6           29186       30401     9767488+  83  Linux

```
sda1 = recovery
sda2 = Vista
sda3 = Data, files, stuff.
sda4 = Extended partition for 7 and Mint to live in
sda5 = Windows 7
sda6 = Mint Linux

Booting off the hard drive, Vista's boot manager comes up showing Vista and Win7. Vista blue screens giving a corrupt partition error. Win7 works with no problem however it shows the Vista drive as RAW format instead of NTFS. Win7 also shows an additional unformatted partition on the drive (there should only be one - the hidden recovery partition).

To get to this position I followed the instructions here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
in the Preserving Windows Bootloader section. Searching through the ntfs-3g forums suggests a "RAW file system often means partition table, boot sector corruption or device driver problems". Win7 detects errors on the Vista partition and runs chkdsk at startup but this makes no difference. 

Is there any way to change the Vista partition back to RAW without formatting it, and why has the extra partition shown up?

---

### Post by chopsuwe on 2009-07-28
Hmm, no replies. I guess the next thing to ask is if it is safe for me to delete the unknown partitions and reinstall windows?

---

### Post by merlinus on 2009-07-28
I suggest you ask for assistance in a windows forum.

---

### Post by coffeecat on 2009-07-28
Since you've already found the ntfs-3g forums you've probably found a load of threads about "RAW" problems in Vista after Linux has written to the partition. I get the sense that this happens only with 64-bit Vista - I haven't had this problem (yet :( ) with my 32-bit Vista. Is yours 64-bit? Not that that helps you much.

Since it sounds as though you have an OEM Vista DVD, rather than the standard Microsoft one with the "recovery center", the only other thing I can suggest is to download the Vista recovery disc from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Although, if W7's chkdsk doesn't help, this might not either.

Rather than a Windows forum as merlinus suggests, where only a minority may have any experience at all with Linux, have you thought about posting on the ntfs-3g forum?

By the way - which do you mean by the "extra partition showing up"? I don't see which you mean.

---

### Post by chopsuwe on 2009-07-29
As you say there are a lot of people having this problem, I've got 60 browser tabs open trying to find a soltion, but no answers. 

I'm running Vista32 bit Premium but the problem came up after trying to install Grub which makes me think that Grub may have over written the MBR or partition table or something. I've already run chkdsk, fixmbr and fixboot with no success. 

The extra partition seems to be the Linux partition. See the screen shots below. The red labels on the disk manager screenshot are what I think the partitions relate to. Is it normal for Windows7 to be able to see there is a Linux partition like mine can?

---

### Post by coffeecat on 2009-07-29
> **chopsuwe said:**
> I'm running Vista32 bit Premium but the problem came up after trying to install Grub which makes me think that Grub may have over written the MBR or partition table or something.

Well - strictly speaking, the term mbr refers to the first 512 bytes of the Hard Disk, which does include the partition table. The first 446 bytes (which is what a lot of people loosely mean when they refer to the mbr) hold the code invoked during bootup to pass control to the Windows ntldr, or bootmgr in the case of Windows7. Yes, grub certainly does overwrite the Windows mbr on the first 446 bytes by writing grub stage 1 to that area. But it doesn't touch the 64 byte partition table that comes immediately after. I've never, ever had a partition table corruption by installing (or re-installing) grub.

I thought the RAW problem with Vista was to do with filesystem corruption, and not a problem with the partition table.

> **chopsuwe said:**
> The extra partition seems to be the Linux partition. See the screen shots below. The red labels on the disk manager screenshot are what I think the partitions relate to. Is it normal for Windows7 to be able to see there is a Linux partition like mine can?

I see what you mean by your "why has the extra partition shown up?" question now. Yes it is quite normal for a Linux partition to be shown in the Windows computer management utility. It happens in Vista and XP as well. I think Windows is simply reading the partition table, but when it gets to the filesystem it doesn't understand it and that's why it's not identified as ext3 or whatever.

---

### Post by W4l0ck on 2009-07-29
Try converting to FAT.

---

### Post by chopsuwe on 2009-07-29
> **coffeecat said:**
> I thought the RAW problem with Vista was to do with filesystem corruption, and not a problem with the partition table.

All I know is it changed to RAW after trying to install GRUB. Would attempting to uninstall Grub help? I'm only concerned with getting Vista going again and not ruining my data partition in the process. 

> **coffeecat said:**
> Yes it is quite normal for a Linux partition to be shown in the Windows computer management utility.

That's a relief, I was worried Windows was doing that because all the partitions had been messed up

Would it be safe for me to just delete the Vista partition and use Vista to create a new partition and reinstall in the empty space?


**> **W4l0ck said:**
> Try converting to FAT.**
Why? The partition was NTFS and Linux still recognises it as NTFS. I don't see how this will help?

---

### Post by coffeecat on 2009-07-30
> **chopsuwe said:**
> All I know is it changed to RAW after trying to install GRUB. Would attempting to uninstall Grub help?

Almost certainly not. If you uninstall grub from the Mint system by using Synaptic, that will merely remove all of grub from the system folders of your root partition - which will just make things worse from the Linux point of view. Grub stage 1 will still be on the mbr. Even if you replaced grub stage 1 with the Windows fixmbr command, that won't touch the partition table. And I still don't understand how installing grub could have caused this problem. Like fixmbr, the grub installer simply shouldn't touch the partition table. It must have been one of those random stray events that sometimes affect electronic equipment.

> **chopsuwe said:**
> Would it be safe for me to just delete the Vista partition and use Vista to create a new partition and reinstall in the empty space?

It depends whether you have a Microsoft Vista install DVD, or one of these OEM restore DVDs (or if you're using the hidden restore partition). If the former, you certainly won't have to delete the partition, just tell the Vista installer to install to the RAW partition. It will format it and then install, **hopefully** not touching anything else. Usual caveat: back everything up from the other partitions. Or if the Vista installer doesn't like that, simply use a Ubuntu or Mint live CD to format the RAW partition to NTFS. The Vista installer will be happy with an empty NTFS partition. It will detect all the partitions you have on the HD and ask you which one you want to use.

However, it's a very different matter if that's a manufacturer's OEM disc, which it almost certainly is. I'm sorry, but I don't know. Different manufacturers' discs do different things. Some simply wipe the whole drive, reformat it the way they think best and restore Vista to its factory condition, together with any hidden/restore partitions. More thoughtful manufacturers give you more control. My Sony discs allowed me to restore the original Vista image to a partition that I had set up. It was still sda2 as originally, but I had made it smaller so that I could multiboot. I'm afraid you'll have to check the documentation or start the DVD up and see what happens. It *should* warn you what it's about to do and let you cancel if necessary. "*Should*". :(


> **chopsuwe said:**
> [quote=W4l0ck;7700409]Try converting to FAT.Why? The partition was NTFS and Linux still recognises it as NTFS. I don't see how this will help?[/quote]

I don't follow W410ck's logic either. FAT is going to be of no use to you. For one thing, Vista won't run in a FAT partition.

---

