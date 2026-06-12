---
title: "Reinstalling XP"
date: 2004-11-19
forum: Hardware &amp; Laptops
---

### Post by Maxium on 2004-11-19
I have downloaded Ubuntu (it is wonderful!) and I've decided that I would like to use it on another computer rather than this one... so I've decided to just install XP again. Upon putting my bootable XP disk in and rebooting, it does not reconginse the disk and will not boot up the Windows Installation. Could anyone please give me any advice. Thanks.

---

### Post by jdong on 2004-11-19
Make sure you computer is set to boot from CD-ROM first, before hard drive.
 
 
 Ubuntu's installer can not cause this kind of trouble.

---

### Post by Maxium on 2004-11-19
[QUOTE=jdong]Make sure you computer is set to boot from CD-ROM first, before hard drive.
 
 
 Ubuntu's installer can not cause this kind of trouble.[/QUOTE]
Exactly how can I do so?

---

### Post by jdong on 2004-11-19
That'll be in your BIOS setup, under Boot Order or a similar option. Each computer has a different BIOS menu, so there'll be slight variations.

---

### Post by Maxium on 2004-11-19
[QUOTE=jdong]That'll be in your BIOS setup, under Boot Order or a similar option. Each computer has a different BIOS menu, so there'll be slight variations.[/QUOTE]
Ok, I've went into my BIOS (Phoenix-BIOS) and edited the "Boot Priority" and put my CD first... it booted and still loaded Ubuntu.  :-|

---

### Post by Klunk on 2004-11-19
Would it not be best to fdisk in linux and remove all partitions first and then install XP ? You might also want to try and get a bootable dos floppy where you can do an **fdisk /mbr** to set the disk ack to a 'standard' configuration. It is normally best to create a small partition to install windows on and then extend it once windows is insalled, this makes the install quicker.

I dont know if XP is the same but I always had trouble when I wanted to revert a machine back to Windows.

One caveat to this, obviously fdisk will completely trash you disk and you will no be able to recover back to any install you currently have.

---

### Post by moon2js on 2004-11-19
I had this problem before, and for me it was a mystery.

Make sure that the boot order is setup correctly. And try using other bootable CDs to see if they work.

In the end, I reinstalled my BIOS and it fixed the problem, but I never understood why my BIOS needed to be reinstalled in the first place. It was also a Phoenix BIOS.

---

### Post by jdong on 2004-11-19
Not really a Ubuntu problem anymore.
 
 I'll move this to the Hardware forum. I'll leave it to Hardware mods to guide this thread to its ultimate destination...

---

### Post by adbak on 2004-11-20
No, JDong, I do believe it is an Ubuntu problem.  Well...perhaps problem is too harsh of a word.

Two days ago I wanted to make my XP partition smaller (1/3 of its original size) so I pop the XP CD in, tell my computer to boot from the CD, nothing....  I then had to install Ubuntu completely (meaning that I had to erase the whole disk) and run the XP CD after Ubuntu install had told me to reboot.  Perhaps it's not so much an Ubu problem but rather a problem from Ubuntu's GRUB.

That's just my story.  I don't know if this helps even anyone, I just felt like blabbing.  :)

---

### Post by ynef on 2004-11-20
It seems your computer does not understand that the CD is bootable. Try another bootable CD to check.

If all else fails, grab a bootdisk for Windows 98 and use fdisk to nuke your harddrive. Also, use fdisk /mbr to remove all traces of GRUB. You can boot with this floppy and start the Windows install from there, if your CD drive is supported by the standard drivers that come with these floppies.

Download a floppy from [www.bootdisk.com](www.bootdisk.com)

---

### Post by avallon on 2004-11-21
I don't know whether the following will help you, but you can always try.
It happened to me a number of times that my new notebook would not boot from any bootable CD, being either w-based or any type of Linux distribution.
By trial and error, and bashing my head a number of times I found that the BIOS of this notebook was simply too fast, and it would run through the booting sequance before CD/DVD rom/writer would even recogonise the CD which was inserted.
It would check for boot record on a CD, got a message that it was not there (while the device was still busy reading the CD), and then go to boot from hard drive and any system that was set up.
The solution was simple:

I would stop BIOS by entering it, or I would chose a separate booting sequence option.
Then, put in a bootable CD containing anyhting that should be booted (W2000, xp, Mandrake 10, Mandrake Move, or any other distribution), and then - WAIT paitently until CD/DVD lights would go off (meaning that the device has completed reading the Cd info). Following that, I would continue the boot sequence. And - further, problem was solved, never to be reapeated again.

I hope this helps.

---

### Post by jdong on 2004-11-21
[QUOTE=adbak]No, JDong, I do believe it is an Ubuntu problem.  Well...perhaps problem is too harsh of a word.

Two days ago I wanted to make my XP partition smaller (1/3 of its original size) so I pop the XP CD in, tell my computer to boot from the CD, nothing....  I then had to install Ubuntu completely (meaning that I had to erase the whole disk) and run the XP CD after Ubuntu install had told me to reboot.  Perhaps it's not so much an Ubu problem but rather a problem from Ubuntu's GRUB.

That's just my story.  I don't know if this helps even anyone, I just felt like blabbing.  :)[/QUOTE]
 Booting from CD is behavior dictated by your BIOS. Ubuntu and/or GRUB can NOT change how your BIOS behaves.

---

### Post by electroglas on 2004-11-22
During boot with the CD, the PC may ask you to "Press any key to boot from CD".

---

### Post by gitano1 on 2004-11-22
The solutions offered are correct. Windows does not recognize the hard drive because it is formatted for Linux. To overcome the problem you have to use a Windows boot disk (floppy), make sure you Bios is set to boot from floppy first, then boot into the floppy. When the A prompt appears type in Fdisk and remove all partitions and then create a primary partition. At that point you should be able to insert you Windows CD which will ask to format the hard drive before installing the OS. The problem is one of compatibility of Operating systems with format styles. Ubuntu will install itself on a Windows formatted disk, but the opposite will not work. Thank you Bill Gates. :?

---

### Post by wallijonn on 2004-11-25
I will usually use Linux's fdisk to undo all partitions. I used the ultimatebootcd and slackware to be able to run fdisk. [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

```

#fdisk
Command (m for help): m
p print the partition table
d delete a partition
w write partiton table
#

```

.

---

### Post by mr_ed on 2004-11-25
[QUOTE=electroglas]During boot with the CD, the PC may ask you to "Press any key to boot from CD".[/QUOTE]

And it will give you about 1 or 2 seconds before it gives up and starts to load GRUB.

---

### Post by wallijonn on 2004-11-25
[QUOTE=gitano1] When the A prompt appears type in Fdisk and remove all partitions and then create a primary partition. [/QUOTE]

You may also wish to ```
fdisk/mbr
``` before you re-run fdisk to blow away all Linux partitions.

If you have WXP installed on its own partition and you wish to blow away GRUB, then you [COLOR=Red]fdisk/mbr[/COLOR], install the WXP CD, boot into safe mode and [COLOR=Red]fixboot c:[/COLOR] and / or [COLOR=Red]fixmbr[/COLOR]. I believe fixboot c: will scan the disk for WXP partitions while fixmbr will recreate an MBR (but it probably will not work because the old mbr was linux based). 

To repair Grub you boot into #sudo init1, [COLOR=Red]/sbin/grub-install /dev/hda[/COLOR] and [COLOR=Red]update-grub[/COLOR].

---

