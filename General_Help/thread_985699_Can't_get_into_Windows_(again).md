---
title: "Can't get into Windows (again)"
date: 2008-11-17
forum: General Help
---

### Post by TV-VCR on 2008-11-17
I can't boot into Windows, as GRUB doesn't have any Windows entries in it. How should I edit the menu.lst file so that I can boot into my Windows Vista install?

Ubuntu is on sda. Vista is on sdb.

---

### Post by TeXtonyx on 2008-11-18
Originally Posted by caljohnsmith
OK, to boot Windows from Grub, how about first opening a terminal
(Applications > Accessories > Terminal), and do: 

Code:

gksudo gedit /boot/grub/menu.lst

And at the very bottom add:
Code:

title	   Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

----------------------------------------------

This above method just worked (try it first) and seems to be a logical way.

If it doesn't work, try my entry to menu.lst. I'm curious
to see if they both work if you have the inclination to test.

title Vista
root (hd1,0)
makeactive
savedefault
chainloader +1 

----------------------------------------

Don't have hiddenmenu enabled or you won't see the Vista choice.
Don't set your timeout to 0 make it 5 (seconds). (settings in menu.lst)

If you have any trouble, then do  sudo fdisk -l (a small L)
and post the result. I think Vista maybe should have an *
next to it in the fdisk report, which means it's bootable.

---

### Post by TV-VCR on 2008-11-18
Doesn't work.
[B]Starting up...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart[/B]

...wtf.

Well, if this helps:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70841fad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061    5  Extended
/dev/sda2   *         250        6474    50002312+  83  Linux
/dev/sda3            6475       60801   436381627+  83  Linux
/dev/sda5               1         249     2000029+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70841faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64061985

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91202   732571648    7  HPFS/NTFS

```

I would try running the vista repair utility from my vista DVD but I think it would screw up GRUB.

---

### Post by amp_man on 2008-11-18
Vista repair utility would overwrite grub in a heartbeat ;) Is vista installed on the 500gb or 750gb drive? If the latter, replace "hd1" above with "hd2". You shouldn't need the version with the "map()" commands, all that does it move drive d: to drive c:, but Vista will happily run off drive d:

EDIT: forget the 500/750 question, you already stated windows was on sdb. and fdisk marks it as bootable.

---

### Post by TeXtonyx on 2008-11-18
"I would try running the vista repair utility from my vista DVD 
but I think it would screw up GRUB."

The error message you received is a Windows error message, not a
Ubuntu/grub error message. I think it means that the entry you
added to menu.lst worked. 

You can try changing the bios so that it directly boots to your
second drive, sdb. In bios I think it will be hd1 rather than hd0.
But, I think you will probably get the same Windows error message.

Each hard drive has its own MBR. So sda has grub in its MBR. I
don't see why Vista, sdb, should have grub in its MBR, unless
you choose to put it there during your Ubuntu install, instead
of the natural place, MBR in Ubuntu -> sda.

So, I see no reason not to use the Vista Startup Repair option.
It should write to the Vista drive's MBR which is sdb. I think
it would be hard for you to figure out to install Vista's MBR to 
sda. Just pay attention, Repair install sdb, your current Vista.

After, I think your already done grub entry will chain to the
Vista bootloader and now Vista should boot without the missing
ntldr error. If you changed in bios to hd1 as first boot device,
maybe it is safest to leave it that way until after you finish with 
Startup Repair, and change bios back to hd0 as first boot drive later.

Also, if you reinstall grub, within sda Ubuntu, it also should
pick up the Vista installation; but you don't need two entries for
Other OS: Vista, in your menu.lst (so just do this if grub doesn't work).

The threat of overwriting your Ubuntu grub MBR (which is of course
fixable) is when they are both installed on the *same* hard drive
and so are competing (Vista and Ubuntu) for writing to the MBR,
and can overwrite each other. There is little danger (actually
none that I know of Vista/sdb overwriting sda's grub MBR) and with
(when in your case not one hard drive, but two hard drives)
more control is available in reinstalling grub, you could install 
grub to the Vista hard drive or MBR which is a big mistake. Ubuntu's 
grub goes to the hd0 MBR, not to hd1 which means the Vista MBR.

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)
How to get Startup Repair going on Vista with pictures.

---

### Post by TeXtonyx on 2008-11-18
When I give advice I often test it. So I deleted OpenSuse on my second drive
and installed Vista. Then I tried both of those entries to menu.lst in order
to boot Vista. Surprise, they both gave me the ntldr missing error that you
received. But I could boot to Vista from bcdedit Vista bootloader menu, so
I knew there was no missing ntldr. After booting to Vista a couple of times
the error message changed to bootmgr is missing. But I was using it while
booting to Vista. Then I discovered that bootmgr and the other Vista boot
files were on my first drive in the XP root directory, and not on second drive.

Vista refers to XP as old windows operating system. Since I had XP set up to
boot Ubuntu, I can boot Ubuntu from my old XP boot.ini menu. I'm gonna try
fixing my XP mbr so I can delete Vista. I'm not sure how this is going to
work out for you. I should have disconnected the the first drive before I
installed Vista which would have avoided Vista files on the XP first drive.

UPDATE: I used XP Recovery Console to fixmbr and fixboot. Then I copied
all the files and one directory back over to the Vista drive that had
been placed on the XP drive. I added a "makeactive" and otherwise used
the same grub entry as before. And it worked from Ubuntu grub ok, no error.

title Vista
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive  <--- not sure it's necessary
chainloader +1

I think the other grub entry also works. I wound up deleting the Vista
installation because it kept reverting back to the Vista bootloader menu
every time I booted Vista. So if this grub entry isn't working for you
maybe the Vista boot files that are supposed to be at (hd1,0) are at
the other NTFS location sdc? So the file is reported as missing. You 
might check to see if you have any Vista boot files on sdc1. Good luck.
My "missing bootmgr" was on sda1 not sdb1 where it was expected.

---

### Post by TV-VCR on 2008-11-18
Ok... so just boot up the computer, put in my Vista disk and have it repair? Ok then.

Edit: Vista isn't detecting either of the installs. :(

---

