---
title: "[SOLVED] Grub error 22.  I reinstalled grub from live cd but error still there."
date: 2008-09-23
forum: General Help
---

### Post by papafreebird on 2008-09-23
My grub got messed up.  Now I am trying to fix it.  I reinstalled it using [the info posted here](http://ubuntuforums.org/showthread.php?t=224351)

After reinstalling grub twice I still get error 22 and do not get the menu offering which OS I want to boot into.  

here is my fdisk info

```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00710070

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d1e9cf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5678    45608503+   7  HPFS/NTFS
/dev/sdb2   *        5679        7223    12410212+  83  Linux
/dev/sdb3            7224        7297      594405    5  Extended
/dev/sdb5            7224        7297      594373+  82  Linux swap / Solaris

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x218e3293

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4998    40146403+   7  HPFS/NTFS

```

Any help would be appreciated.

---

### Post by phidia on 2008-09-23
Since you tried the grub howto and it didn't work you may have to get [Super Grub Disk]("http://www.supergrubdisk.org/") and try that.

Added: The error definition for 22 is: > # 22 : "Must load Multiboot kernel before modules"

This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel  

I believe this is usually some type of configuration file error although it doesn't seem like that from the definition.

---

### Post by caljohnsmith on 2008-09-23
Just curious, but where did you find that Grub error definition, phidia? I believe that a Grub error 22 is:
> **Error 22** : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.
See the [online Grub manual]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors").

Papafreebird, are you getting that error when you select an OS in the Grub's menu, or do you get that error before you even get the Grub menu? How about booting your Live CD, open a terminal (applications > accessories > terminal) and do the following:
```
sudo mount /dev/sdb2 /mnt
cat /mnt/boot/grub/menu.lst
```
Also, do you know which HDD you are booting from on start up?

---

### Post by papafreebird on 2008-09-23
I get the error before seeing any menu.  It just says something like

[b]
Getting Grub stage 1.5
Loading Grub...
Error 22[/b]
and then just stays there.

I'll reboot the live cd and post the info you are requesting.

If you both think that super grub will be worth a try then I might try that also.  

Will post back soon.

Thanks to you both for help.

---

### Post by caljohnsmith on 2008-09-23
OK, I think I know what might be going on. When you boot your Live CD, please also post:
```
sudo grub
grub> find /boot/grub/stage1
```
So was Grub working before--were you able to boot Ubuntu OK? Or has it never worked yet? And did you just recently add one of those HDDs (maybe the sdc drive)?

---

### Post by papafreebird on 2008-09-23
I can tell you that without booting to the live cd.
hd(1,1)

What happened was I recently screwed up my ubuntu install royally.  It was working just fine then I screwed some things up so I just reinstalled 8.04 from cd.  Now I have grub problems.

---

### Post by caljohnsmith on 2008-09-23
Can you change the BIOS boot order so that your Linux HDD boots first? If you can do that, it would be ideal, and we can set up your Grub accordingly. If you can make the Ubuntu HDD first to boot, then do the following so that you install Grub to its MBR (master boot record):
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1)
grub> quit
```
Then all you will need to do is modify your menu.lst to get things working, but let me know if you can do the above first.

---

### Post by papafreebird on 2008-09-23
Okay my bios **would** let me set my linux drive to be the first hard drive booted so I set it that way then installed grub to hd1 as per your instructions.  

What do I need to change in my menu.lst file?

my menu.lst file
```


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f3f4cf8d-9bd6-4092-a6d9-2d4d55f11c49 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f3f4cf8d-9bd6-4092-a6d9-2d4d55f11c49 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by caljohnsmith on 2008-09-23
Since you were able to change your BIOS to boot your Ubuntu drive, you have to change your menu.lst because your Ubuntu drive is now (hd0) or the boot drive, and not (hd1) or the second drive in the BIOS boot order. So all you need to do is open your menu.lst:
```
sudo mount /dev/sdb2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all the "root (hd1,1)" instances to "root (hd0,1)". And one last detail, near the top of the file change the "#groot=(hd1,1)" to "#groot=(hd0,1)". 

Also, your Windows will be on either (hd1) or (hd2) now that Ubuntu is first to boot. So replace the Windows entry in menu.lst to the two following entries:
```
title		Microsoft Windows XP Professional (hd1)
root		(hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader	+1

title		Microsoft Windows XP Professional (hd2)
root		(hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
makeactive
chainloader	+1
```
One of those should work, and when you figure out which one it is, you can delete the other entry afterwards. Let me know how it goes or if you need more details/info.

---

### Post by phidia on 2008-09-23
caljohnsmith, You're right I pasted the wrong error definition-sorry.
I'm not sure how that happened. Good that you caught it though.

---

### Post by papafreebird on 2008-09-23
Holy horse puckey Batman **it worked!**

I now have ubuntu back again.  Thank God.
Spending a week with only winXP has not been fun.  

Thanks so much for your help!

---

### Post by caljohnsmith on 2008-09-23
You're welcome, and that's great news your Ubuntu is working again. Cheers and have fun. :)

---

### Post by papafreebird on 2008-09-23
One last thing.  Ubuntu boots great from grub now but my xp on this computer doesn't.  Not a huge issue but it would be nice to boot into xp on this computer when I just absouletly have to have it.

Any ideas on this.

---

### Post by phidia on 2008-09-23
What happens when you select xp? You may need to look at what fdisk reports for your xp partition and compare that to menu.lst.

---

### Post by caljohnsmith on 2008-09-24
Did you add the entries for Windows XP that I suggested in post #11? And if you did, what exactly happens when you try each of those entries from the Grub menu on start up?

---

### Post by papafreebird on 2008-09-24
Yep.  One gave Stage2readerror and the other gave Grub Geom error.

---

### Post by caljohnsmith on 2008-09-24
Were there any Grub error numbers reported? And you can you still boot OK into Ubuntu?

---

### Post by papafreebird on 2008-09-24
no error numbers.  Yep can still boot into ubuntu just fine.  Running it right now... Still can't thank you enough for at least getting me this far.

---

### Post by caljohnsmith on 2008-09-24
Those type of errors are definitely not a good sign. Do you have a Windows Install CD? If you do, boot it up, press "r" in the first menu to get the "recovery console", and run the following command:
```
map
```
That will show you which drives are Windows, and then run the following command on your Windows drive:
```
fixmbr <drive>
```
So for example, it might be:
```
fixmbr C:
``` 
Then change your BIOS boot order back to your Windows HDD, and see if it boots into Windows OK. If not, let me know exactly what happens.

---

### Post by papafreebird on 2008-09-24
Looks like xp is hosed.  I can't even access the xp drive from ubuntu.  Tried mounting it and no go.  Popped in xp install disc and ran chkdsk and is said that drive has unrecoverable errors.

Looks like I'm going to have to do a fresh install...

---

