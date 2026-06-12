---
title: "Can't boot windows"
date: 2008-08-18
forum: General Help
---

### Post by Robbinski12 on 2008-08-18
Hi,
A few days ago I installed Ubuntu to my PC. At first my computer didn't boot AT ALL, but now Ubuntu works fine. The problem is that I share my PC with my brother, which hates Ubuntu (as one of the few ones on earth) and wants Windows XP. But, I think because I didn't install Ubuntu on my main drive, I cannot boot Windows from Grub, and I don't know how I can.
This is my */boot/grub/menu.lst* :
```
title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1be478d5-4b2a-4773-8ec2-34df68df1d19 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader +1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1be478d5-4b2a-4773-8ec2-34df68df1d19 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```
As you see I added Windows XP to *menu.lst*, but I get error 13 when trying to boot.

Can someone please help me with this because my brother kills me :(

Robin Kanters
the Netherlands

[SIZE="1"]PS1: If so, sorry for my poor English but as you can see i'm Dutch :)
PS2: Maybe I posted this in a wrong category, but that's because I didn't know sure in which I SHOULD have.[/SIZE]

---

### Post by Herman on 2008-08-18
```
title        Ubuntu
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=1be478d5-4b2a-4773-8ec2-34df68df1d19 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=1be478d5-4b2a-4773-8ec2-34df68df1d19 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

[COLOR=Sienna][B]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
[/B][/COLOR]
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
chainloader +1
```:) Hello Robbinski12,
The first thing I want to help you with is to make sure you understand that your Windows entry in GRUB's /boot/grub/menu.lst should be under where it says '### END DEBIAN AUTOMAGIC KERNELS LIST', and not in the same area as the Ubuntu boot entries. The reason for that is when there is a kernel update for Ubuntu, the menu/.lst file will also be automagically updated too, and your Windows entry will be deleted. If you leave it under the Debain Automagic kernels list, or above it, your Windows entry will be okay.

Second, can you please post the output from 'sudo fdisk -lu' here so I and who-ever else might help you can see which hard disks and partitions you have?
```
sudo fdisk -lu
```It is almost always useful to know the hard disks and partition arrangement, especailly for boot loader questions. :)

I am only guessing, but maybe your Windows is in hard drive 1, so maybe try (hd1,0) for Windows. When I see your fdisk output then I might change my mind about that.

You can also use a [Super Grub Disk]("http://www.supergrubdisk.org/") to boot Windows with until your GRUB is fixed.

Another thing that would be good if you want to is to press your 'c' key from your GRUB menu and go into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and see if you can boot Windows that way. Nevermind if you think it's too complicated, but give it a try, reading that link and maybe you can figure it out. You should be able to boot Windows that way.

For now, the main thing is if you can post your fdisk output here, someone will be able to help you.

Regards, Herman :)

---

### Post by Robbinski12 on 2008-08-19
hello herman,

this is the output of the command you asked 'sudo fdisk -lu':
```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb8cfb8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   154015154    77007546   83  Linux
/dev/sda2       154015155   160071659     3028252+   5  Extended
/dev/sda5       154015218   160071659     3028221   82  Linux swap / Solaris
```

Hope this helps :)
[SIZE="1"]
EDIT: Looks like Windows is gone to me...[/SIZE]

---

### Post by Herman on 2008-08-19
Very good, thank you.
I can't see Windows there anywhere.

If there's only one hard disk in your computer then it looks like Windows has been accidentally deleted and replaced with Ubuntu. Your Linux partition begins at sector number 63, that's where the start of Windows would have been.

If your brother has any important files I hope one of you made a backup of them to some other disk or to DVDs and CDs. IF not if there were any important files there that you need to recover, you should still be able to get most of them back again with [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")  in TestDisk.
TestDisk can be installed (temporarily) in your Ubuntu Live CD and is also found already in the following live CDs: [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/"); [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"); [System Rescue CD]("http://www.sysresccd.org/Main_Page"): [Knoppix]("http://www.knoppix.net/") and other live CDs.
The easiest one is Ubuntu Rescue Remix for USB, because then PhotoRec will just save all the files it finds into the home folder and if your USB is bigger than your hard drive it will be able to fit everything in in one run.
Tell me if you need more help and I'll try to explain more. If either of you has a backup then you don't need to run PhotoRec though. (Unless you just want to learn). 

Regards, Herman :)

---

### Post by Robbinski12 on 2008-08-19
Thanks, but I think the problem is that my C: drive was almost full and I installed Ubuntu to D:

Do you think you know how to solve my problems now?

Robin Kanters
NLD

[SIZE="1"]If I understood what I learned earlier well, thats why it says /dev/SDA??[/SIZE]

---

### Post by caljohnsmith on 2008-08-19
> **Robbinski12 said:**
> Thanks, but I think the problem is that my C: drive was almost full and I installed Ubuntu to D:

Do you think you know how to solve my problems now?

Robin Kanters
NLD

[SIZE="1"]If I understood what I learned earlier well, thats why it says /dev/SDA??[/SIZE]
I think Herman all ready answered your question, and the unfortunate truth is that you accidentally deleted your Windows partition. Just follow his advice about using photorec to try and recover your Windows files. That's about the best you can do at this point.:neutral:

---

### Post by Robbinski12 on 2008-08-20
Are you sure cuz I think it's still on C:

---

### Post by lost.sync on 2008-08-23
hope this worked out for you.  if you say you didn't delete it, im inclined to believe you.  i just installed 8.04 from CD and it completely botched my grub install.  i'm confident that my data is intact but so far i cannot boot either windows or ubuntu.  working on it...not much progress but im confident that things will eventually be fine.

---

### Post by mb_webguy on 2008-08-23
Unless you have two physical hard drives and one isn't showing up in fdisk (which isn't likely), then I'm afraid that I have to agree with the others that you nuked Windows.

If you would like to reinstall Windows, we can help you correctly set up a dual-boot system.

---

