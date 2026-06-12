---
title: "Cross platform memory stick"
date: 2014-08-07
forum: Hardware
---

### Post by UncleMonty on 2014-08-07
Is it possible to format a memory stick so that it will work on both Ubuntu 14.04 and a Mac Mini that runs Snow Leopard?

---

### Post by slooksterpsv on 2014-08-08
You'd want to use FAT32 or NTFS. I believe Macs can write to NTFS, if not FAT32. You can install modules to mount ext2 or ext3  on Mac - which I'd prefer over, but I use Windows still so I use NTFS.

---

### Post by oldfred on 2014-08-08
This was not for a Mac, but shows installing in both UEFI & BIOS boot mode.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

You may also be able to install rEFInd?
      
 Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

### Post by slooksterpsv on 2014-08-08
??? oldfred? I thought he was meaning for transferring files back and forth, not for booting. Wrong thread maybe?

---

### Post by UncleMonty on 2014-08-09
Slooksterpsv - yep I'm looking to transfer files back and forth!

---

### Post by Lars Noodén on 2014-08-10
HFS+ is OS X's native file format.  Ubuntu will read HFS+ no problem and, if journaling is turned **off** on the stick, it will also write.  

There are minor variations in the Disk Utility between versions, but if I recall correctly, Snow Leopard allows you to choose unjournaled as an option.  If not, there should be a button at the top of the Disk Utility window to enable or disable journalling.  If you have to disable journalling manually in OS X, it is like this in the shell:

```

diskutil disableJournal /Volumes/*Foo*

```

... where *Foo* is your USB stick.  

As far as I know, Ubuntu 14.04 works out of the box with HFS+, it works for me, but if you want some of the extra utilities like fsck then you can add hfsplus, hfsutils and hfsprogs.

---

### Post by coffeecat on 2014-08-10
@UncleMonty, you can format your usb device with the unjournalled version of HFS+ as Lars Noodén describes to get read-write in both Ubuntu and Snow Leopard, but you will still trip over another issue. Your UID in Ubuntu will probably be 1000 and in Snow Leopard, iirc, 501. Depending on what specific permissions files are saved with, that may or may not be troublesome. When I was experimenting with unjournalled HFS+ for file transfer between Snow Leopard and Ubuntu, I found it really irritating to have to deal with occasional permission problems.

The easiest and quickest way is to use a Microsoft filesystem which circumvents this problem. FAT32 is supported read-write out of the box in both Snow Leopard and Ubuntu and is the simplest option, but has the disadvantage that the file size limit is 4GB. If you are wanting to transfer video files, this might be an issue, but if not, go for FAT32. 

If you do need to transfer files > 4GB then you could consider NTFS. NTFS read-write support is good in Ubuntu, but Snow Leopard can only read NTFS unless you install the Mac ntfs-3g driver. When I did this a few years ago, it seemed to be less reliable and certainly much slower than the Linux ntfs-3g driver. Perhaps it has improved now - I have no recent experience. 

For files > 4GB there's also a third possibilty: exfat. Apparently exfat is supported in Snow Leopard, and you can get exfat support in Ubuntu by installing exfat-fuse and exfat-utils. Whether that's a viable option, I don't know. I've never done it. Perhaps others can comment.

---

### Post by Lars Noodén on 2014-08-10
I thought FAT32 and the other FATs mung filenames, among other problems.  

As for the UID question, it's easy enough to set the same numerical UID on all machines in question.  I usually adjust the OS X machines to match the Linux machines.  But that 's just in the personal space.  In a larger, work environment the UIDs are usually coordinated and synchronized among all macnines so there it would not be an issue.

---

### Post by coffeecat on 2014-08-10
> **Lars Noodén said:**
> I thought FAT32 and the other FATs mung filenames, among other problems.  

Why would you think that? There are a few characters which are forbidden in Microsoft filesystem filenames, which I wouldn't use anyway, but in years of moving files between Linux, Apple and Microsoft filesystems, I have yet to have a filename "munged". But I have come near to tearing my hair out with HFS+.

---

### Post by oldfred on 2014-08-10
I have seen windows names as an option for NTFS mounting to avoid file name issues.

 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

Yes oldfred did not read OP's first post and just thought boot issue.

---

### Post by slooksterpsv on 2014-08-10
@oldfred, no worries I've done it before, you've seen that for sure; went to post in one thread and typed up my response in another thread, usually you post right after I do in those circumstances. Um...lol

---

