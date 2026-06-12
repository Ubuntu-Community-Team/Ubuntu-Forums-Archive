---
title: "Need Help Booting a Lost System"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Jefferythewind on 2009-07-03
Hello Everybody,

  I need help.  I had Ubuntu running on a partition on my laptop, no problem.  

I just tried to install XP on the other part of the partition, i think everything was alright, but the windows installation was really strange.  It kept installing the windows file system and then restarting, like it should.  But then, it would always return to the menu where i select which partition to install the windows system, and the system would never start.

So...  I restarted my computer, not expecting Ubuntu to start because i know the windows installation deactivates Grub.  And my computer says there is as "Invalid Partition Table" and it can't start at all. 

Luckily i have the Ubuntu Live CD that i am using now.  I have found my old Ubuntu files and even the new Windows file system installed.  (In the picture Ubuntu is installed on the 114 GB drive, and Windows on the other)  But when i run the partitioner it says my hard drive is completely blank.  (See screen shots)  

Also, When i run the Grub installation there is an error that has to do with the partitions. (also see picture)

I don't know exactly what to do.  I would like the dual boot, both Windows and Ubuntu, but right now basically i just what to boot my Ubuntu system.  Any help would be greatly appreciated!  Thanks.

---

### Post by merlinus on 2009-07-03
Post results of

```
sudo fdisk -l
```

Also, what is the booting order of your hdds in bios?

---

### Post by Jefferythewind on 2009-07-03
Hey Merlinus, thanks for the reply,  my HDD is 4th in the boot list behind the CD drive, USB drive, and PCI slot.

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x7bc9401c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5165    39047368+   7  HPFS/NTFS
/dev/sda2   *        5166       20674   117234337+   5  Extended
/dev/sda3           19887       20674     5944018+  82  Linux swap / Solaris
/dev/sda5            5167       19887   111282223+  83  Linux

---

### Post by merlinus on 2009-07-03
You might try this:

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

---

### Post by Jefferythewind on 2009-07-04
Hmm, i got this:   

         [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub>

---

### Post by merlinus on 2009-07-04
If you have a usb drive plugged in, you might try changing the booting order to make the hdd second, and re-run the grub commands.

BTW, what is the 40G drive that shows up in your second graphic?

Another thing I noticed is that your partitions are not in order, and there is no sda4.

---

### Post by Jefferythewind on 2009-07-04
Alright, I changed the boot order so the CD is first and HDD is second.  I tried to install grub in the same two ways that that i have before and i get the same error messages.  

I think there is definitely a problem with the way the drive got partitioned when i tried installing Windows.  Like it shows in the picture, the Ubuntu Partitioner thinks the drive is blank, (and only has 150GB).

Maybe i should tell you that when i installed Windows XP, i changed my SATA Controller Mode Option from AHCI to Compatibility.  

I did this because at first the windows installation wasn't recognizing my hard drive, and i found online that the XP installer can't recognize certain SATA hard drives.  They said it might work to change the AHCI setting, so i tried it, and the windows setup worked.  Well, worked until, like i said above, it kept repeating the step where it asked me on which partition i want to install it.

I noticed in the fdisk printout has two stars next to sda1 and sda2 for the boot devices. That is where the Windows was installed i think. Is there a way i could move those stars down to the sda5?

---

### Post by unutbu on 2009-07-04
There should only be one boot flag set, and the boot flag must always be on a primary partition (not an extended or logical partition). sda2 is an extended partition, and sda5 is a logical partition. So the boot flag should be set on sda1. This command will set the boot flag on sda1 and clear it on all other partitions:
```

sudo sfdisk -A1 /dev/sda
```

Also, the output of "sudo fdisk -l" says:
```

omitting empty partition (5)
```

Whenever you see this, it means there is an error in your partition table.

Could you post the output of 
```

sudo fdisk -lu
```

---

### Post by Jefferythewind on 2009-07-04
Hi, Unutbu, thanks for the help, Should i run the command to set the boot flag on the first partition?

 here is the output:

ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7bc9401c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78094799    39047368+   7  HPFS/NTFS
/dev/sda2   *    78108030   312576704   117234337+   5  Extended
/dev/sda3       300688668   312576704     5944018+  82  Linux swap / Solaris
/dev/sda5        78124158   300688604   111282223+  83  Linux

---

### Post by unutbu on 2009-07-04
Yes, run```

sudo sfdisk -A1 /dev/sda
```

That will correct the boot flag.

I think I see the main problem: sda3 is a primary partition because its device number (3) is between 1 and 4. But sda3 resides within an extended partition, so it should be a logical partition. Logical partitions have device numbers greater than 4. 

Some Windows partition editors do not seem to care, but GParted/GRUB/Ubuntu are sticklers about this.

We can correct this error by renaming sda3 --> sda6. 
Please run
```

sudo sfdisk -d /dev/sda > PT.txt
```

and post PT.txt.

---

### Post by Jefferythewind on 2009-07-04
Alright, that sounds like a good idea.  I have a question, originally i has using Ubuntu for a few months with no problem.  When i installed windows why do you think the partitions got screwed up?

Anyways, here is the output:

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 78094737, Id= 7, bootable
/dev/sda2 : start= 78108030, size=234468675, Id= 5
/dev/sda3 : start=300688668, size= 11888037, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 78124158, size=222564447, Id=83

---

### Post by unutbu on 2009-07-04
Boot from a LiveCD.

Download the attached file, PT-new.txt

Run
```

sudo sfdisk --no-reread -f /dev/sda -O PT.save < PT-new.txt
```

This will rewrite your partition table, renaming sda3 --> sda6.
There will be a fair amount of output.

Look for:
> 
Successfully wrote the new partition table

You can try mounting your linux partition at /mnt by typing:
```

sudo mount /dev/sda5 /mnt
```

Then try merlinus's advice again to reinstall grub:
```

sudo grub
root (hd0,4)
setup (hd0)
quit

```
Then reboot and see if you can boot Ubuntu.

PS. I'm not really sure why the partitions got screwed up after installing windows. A lot of people install Windows after Ubuntu and have no problem. Occasionally there are posts from people who find themselves in your situation however. See for example: [http://ubuntuforums.org/showthread.php?t=1095606](http://ubuntuforums.org/showthread.php?t=1095606)

---

### Post by Jefferythewind on 2009-07-05
Wow!  Its great, i am writing this message from my Ubuntu system.  Beautiful.  I roughly understand what just happened with my system.  I have two questions:

1)  What is sda4?  According to the new partition table it looks like it has no size at all, and sda5 is the filesystem, sda6 being the swap space.

2)  If i want to try installing windows again, where should i do that?  On the space where sda1, sda2, and sda3 are now?

Well anyways thanks a lot to both of you unutbu and merlinus!  This kind of help in the Ubuntu community is what makes using it really worth while.

---

### Post by unutbu on 2009-07-05
I'm glad to hear you can now boot Ubuntu! 

Can you also boot Windows?
> 
1) What is sda4? According to the new partition table it looks like it has no size at all


Your partition table should now look like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5165    39047368+   7  HPFS/NTFS
/dev/sda2            5166       20674   117234337+   5  Extended
/dev/sda5            5167       19887   111282223+  83  Linux
/dev/sda6           19887       20674     5944018+  82  Linux swap / Solaris
```

Right now, you don't have sda3 or sda4 partitions. (If you look inside PT-new.txt, they are mentioned as partitions of size 0, but that is just the way sfdisk likes to list them.)

> 
 and sda5 is the filesystem, sda6 being the swap space.

True.

> 
2) If i want to try installing windows again, where should i do that? On the space where sda1, sda2, and sda3 are now?

If you need to install Windows again, I would recommend using sda1.
sda1 is the only place you could put it right now, without resizing partitions (or overwriting Ubuntu).

sda2 is an extended partition. An extended partition's only job is to act as a container for logical partitions (e.g. sda5 and sda6). Never try to install Windows directly on to an extended partition.

It is possible to install Windows on to a logical partition, but to boot Windows you would need to use a smart bootloader like GRUB. I don't believe the normal Windows bootloader is capable of booting a Windows installation on a logical partition.

Also, if you reinstall Windows, know that Windows will overwrite your bootloader (GRUB). 
To regain the ability to boot both Ubuntu and Windows, you'll need to reinstall GRUB.
We've done that above, or you could use this guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by DrJames on 2009-07-05
Just put in the install disk, and let the system boot from the disk, and that will fix the problem

---

### Post by Jefferythewind on 2009-07-05
Ok, cool i see what you are saying, unutbu, about the partitions now.  

When i first fixed the boot flag, but before i reinstalled Grub, windows started when i turned on the computer.  But soon after it started a blue screen came up, i don't think the system installed correctly.  But now i don't get a Grub menu on startup, it automatically goes right to Ubuntu.

Its too bad, i don't want to have to use windows, but i am using a pretty powerful music production software, with an external sound card, that only works on windows.  I tried something like it once with virtualbox but i couldn't get the sound to work well.

Hey thanks again, i'll check out the tutorial about installing windows.

---

### Post by Jefferythewind on 2009-07-05
Sorry, i realize that you have to press esc to get the grub menu.

---

