---
title: "[SOLVED] Just reinstalled Ubuntu, where is windows?"
date: 2008-12-02
forum: General Help
---

### Post by koolcracker on 2008-12-02
Okay, so I just reinstalled Ubuntu because of a problem I was having and did it in the same way I always have on a separate partition leaving ym windows alone, but now Windows won't boot, and this is the print out from fdisk:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12162    97685783+  ee  GPT

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe28daf03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             128       38913   311548545   83  Linux
/dev/sdb2   *           1         127     1020096    b  W95 FAT32

Partition table entries are not in disk order

```

I have do idea what is going on with that there, and would love if I could get my access to windows back again. Can anyone offer some insight possibly?

---

### Post by DagMan on 2008-12-02
can you paste the contents of the file /boot/grub/menu.lst here please.

Also, is Windows meant to be on the first hard drive by itself or on the same drive as Linux.  I see the FAT32 partition but it looks small is why I'm wondering.

---

### Post by caljohnsmith on 2008-12-02
So is Windows supposed to be on your 100 GB sda drive? Because it looks like your sda drive now has a GPT partition table, not the usual MS-DOS partition table. Your sda1 partition is labeled as a GPT partition, not NTFS or FAT like it should be for Windows. Do you instead have OS X installed on your sda drive? And lastly, do you know which drive you are booting on start up?

Please also post:
```
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd  -l  2 -p /dev/sdb
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
And note "-l" is a lowercase L, not a one. We can work from there if you want.

---

### Post by koolcracker on 2008-12-02
Okay, here is my GRUB file
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		423f912e-7eee-4a86-b6a3-3f2af7904ea2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=423f912e-7eee-4a86-b6a3-3f2af7904ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		423f912e-7eee-4a86-b6a3-3f2af7904ea2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=423f912e-7eee-4a86-b6a3-3f2af7904ea2 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		423f912e-7eee-4a86-b6a3-3f2af7904ea2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=423f912e-7eee-4a86-b6a3-3f2af7904ea2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		423f912e-7eee-4a86-b6a3-3f2af7904ea2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=423f912e-7eee-4a86-b6a3-3f2af7904ea2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		423f912e-7eee-4a86-b6a3-3f2af7904ea2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

I'm assuming they shoudl not be saying hd0, but I think that might be my trouble, I actually have no idea what my windows partitions are anymore. Before I reinstalled, all of my drives had names beginning with hd, rather than sb. I'm assuming that isn't an issue, but I think I'm a little lost.

You were saying it isn't formatted any more? That scared me a little, and no I have never installed OSX. I really don't have the knowledge to tell if something happened to my windows there, so anything you guys can tell me would be just awesome.

For
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda

i got eb48 and f26f respectively. The other drive is my external drive.

EDIT: Looking again at my fstab, that 100GB drive should be divided up. I only have about 60GB of it in use as my home folder, and windows is taking up the other 40. So somehow the drive is no longer recognized as being partitioned? Is there any way to remedy that?

Also, if it makes things clearer, this is what fdisk spits out when I remove my external harddrive:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12162    97685783+  ee  GPT

---

### Post by TeXtonyx on 2008-12-02
hd0 means the first drive. (hd0,0) means the first drive and first
partition. It is the same as ^sda1, they number parts differently.
It seems to me that you did something recently to create that GPT.

---

### Post by koolcracker on 2008-12-02
Ya, I got the part about the hda and sda, but do you think someone could kindly explain to me about the GPT? I don't fully understand that.

---

### Post by HermanAB on 2008-12-02
I would boot a Knoppix CD to see what is going on.  That is the easiest way I know to figure out what is what.

Cheers,

Herman

---

### Post by TeXtonyx on 2008-12-02
[http://technet.microsoft.com/en-us/library/cc773223.aspx](http://technet.microsoft.com/en-us/library/cc773223.aspx)

That explains what GPT is but not how it replaced ntfs.

---

### Post by caljohnsmith on 2008-12-02
According to those xxd commands you ran, it looks like you have Grub in the MBR (Master Boot Record) of your sda drive, but it also appears the Grub stage1.5 file was overwritten by the GPT sectors that come immediately after the MBR. Did you use gparted (Ubuntu's partition editor) on that drive recently? What have you done recently that might have accidentally converted that drive to use GPT instead of the usual MS-DOS partition table?

---

### Post by koolcracker on 2008-12-02
The only thing I did other than reinstalling ubuntu itself was remaking the swap file because it was inoperational. I don't think that would have had an effect on windows, but I'm unfamiliar with this kind of file system business. I used gparted to check my drives, and it lists my windows partition as sd2, but from the way you're talking it makes me think like it won't boot up even if I point GRUB in that direction.

---

### Post by caljohnsmith on 2008-12-02
OK, how about doing:
```
sudo dd if=/dev/sda count=100 | gzip -c > ~/Desktop/sda.MBR.gz
```
That will create a really small "sda.MBR.gz" file on your Ubuntu desktop. Please attach that to your next post so I can try to see what happened with your sda drive's MBR. You can attach it by clicking the "paper clip" icon in the Ubuntu Forum message box in your web browser.

---

### Post by koolcracker on 2008-12-03
Alright, sorry for the delay, but thanks for the help if you are still willing to look at this. 

The reason I reinstalled Ubuntu was because I was experiencing constant kernel panics, so I was trying to determine if it was hardware, and I resoled that problem, but then this came up. I tried a couple things from threads before I did the reinstall, but I'm not totally familiar with these filesystems or tables, so I don't know what I could have done. I thank you again.

---

### Post by caljohnsmith on 2008-12-03
OK, I took a look at the file you posted which is the first 100 sectors on your HDD, and unfortunately it doesn't look promising; according to the MBR, you have a single partition that begins at sector 1 and has an apparently bogus "ee" file system (GPT) as reported earlier by your fdisk results. The first problem with that is the first partition on the drive always starts on the second track or greater, or the 64th sector of the drive; also, I don't think it is just a problem with maybe the MBR being corrupt, because there is nothing but zeros on the drive from sectors 3 - 100. It might be though that your Windows partition starts at a track further into the drive. I really don't know what happened to your HDD, but you could try to use "[testdisk]("http://www.cgsecurity.org/wiki/TestDisk")" to see if it will find any partitions on the drive. Or you could use "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to simply try and recover whatever files it can dig off the drive. Let me know what you decide to do.

---

### Post by koolcracker on 2008-12-03
I know I installed testdisk a while back to analyze some errors I was getting, so I'll see if I can figure out what to do with that first. Thanks for the attention here.

---

### Post by koolcracker on 2008-12-03
Okay, so I ran it and it definitely found my windows partitions. 

Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS                 2048   13748223   13746176 [ServiceV002]
P HPFS - NTFS             13748224   55685119   41936896 [SW_Preload]
P Linux                   65681408   86652847   20971440

I'm feeling a bit confused now.

---

### Post by caljohnsmith on 2008-12-03
Did you get those results after doing the "deeper search"? Did you follow these steps: after starting testdisk, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. The results of the deep scan are what you want to have the best chance at recovering the correct partitions. Please post the deep scan results.

Also, you'll want to erase the traces of the GPT code in the sectors after the MBR in order to effectively convert your HDD back to using a MS-DOS partition scheme:
```
sudo dd if=/dev/zero of=/dev/sda seek=1 skip=1 count=2
```
Then using testdisk should hopefully work to find the correct partitions, but post the output of the deep search first if you would like help with that.

---

### Post by koolcracker on 2008-12-03
Okay, my results:

```
     Partition               Start        End    Size in sectors
D HPFS - NTFS                 2048   13748223   13746176 [ServiceV002]
D HPFS - NTFS             13748223   27494398   13746176
D HPFS - NTFS             13748224   55685119   41936896 [SW_Preload]
D HPFS - NTFS             13748224  195368959  181620736 [SW_Preload]
D Linux                   65693696   86665135   20971440
D Linux                   65816576   86788015   20971440
D Linux                   65818624   86790063   20971440
D Linux                   65835008   86806447   20971440
D Linux                   65847296   86818735   20971440
D Linux                   65869824   86841263   20971440
D Linux                   65894400   86865839   20971440
D Linux                   65900544   86871983   20971440
D Linux                   65914880   86886319   20971440

```

I hate to keep bothering you, but if all looks good there, do you think you could help me with that second part?

---

### Post by caljohnsmith on 2008-12-03
OK, the next step would be to move up and down to select each of those partitions listed, and then press "p" to see if testdisk can list the root directory of the partition; make sure you are using testdisk version 6.9 or later though, which is what comes with Intrepid, because earlier versions of testdisk will crash I think if you try and list the NTFS partitions. Please let me know exactly which partitions you can successfully get a directory listing of, and also let me know what you think your partitions should be from what you can remember. And when you do the directory listing of the NTFS partitions, look for a partition that has the following files/directories:
```
boot.ini
ntldr
NTDETECT
/WINDOWS
```
It looks like the 4th NTFS partition in that list is the most promising. Do you want to also recover any of the linux partitions, or is it OK with you to leave them deleted?

---

### Post by koolcracker on 2008-12-03
Okay, for the 1st and 3rd partitions I get a list of things that come up, but for the 2nd and 4th ones the filesystems appear to have been damaged. Without knowing exactly where to look for all of those files, I really only found the windows directory. The 3rd partition looks a lot like my windows, and the other looks something like my recovery.

If by remembering what the partitions should be you mean the sizes, i think the windows should be roughly 20 gb and th recovery should be around 6gb. Haha im completely at your mercy here, I have no idea where this is headed next. I really appreciate the time.

---

### Post by caljohnsmith on 2008-12-03
OK, that's actually good news if your Windows partition was about 20 GB, because that's how big that 3rd NTFS partition is. So go ahead and select each partition, and then using the left/right arrow keys to change the partition type, how about marking the partitions as follows:
```
[COLOR="Red"]P[/COLOR] HPFS - NTFS                 2048   13748223   13746176 [ServiceV002]
D HPFS - NTFS             13748223   27494398   13746176
[COLOR="Red"]*[/COLOR] HPFS - NTFS             13748224   55685119   41936896 [SW_Preload]
D HPFS - NTFS             13748224  195368959  181620736 [SW_Preload]
D Linux                   65693696   86665135   20971440
D Linux                   65816576   86788015   20971440
D Linux                   65818624   86790063   20971440
D Linux                   65835008   86806447   20971440
D Linux                   65847296   86818735   20971440
D Linux                   65869824   86841263   20971440
D Linux                   65894400   86865839   20971440
D Linux                   65900544   86871983   20971440
D Linux                   65914880   86886319   20971440
```
In other words, all of them should be deleted except the 1st and 3rd partitions. Once you are sure they are all marked as shown above, press enter to get the next screen, and then select "write" to write the new partition table. Also, have you run that "dd" command I gave in my previous post? It's really important you do that so the GPT code is erased. And lastly, it would be good to reinstall a Windows MBR to that drive since only Windows will be on it, so you can do that with:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
Once you've done everything above, please post the output of:
```
sudo fdisk -lu
```
And we can work from there. :)

---

### Post by koolcracker on 2008-12-03
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    13748223     6873088    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    13748224    55685119    20968448    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe28daf03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1         2040255   625137344   311548545   83  Linux
/dev/sdb2   *          63     2040254     1020096    b  W95 FAT32

Partition table entries are not in disk order

```

Thanks a lot for the help, I wouldn't be anywhere right now without you haha. I have a feeling that looks somewhat right, but my eyes are on the newer side to this.

---

### Post by caljohnsmith on 2008-12-03
[QUOTE=koolcracker]Thanks a lot for the help, I wouldn't be anywhere right now without you haha. I have a feeling that looks somewhat right, but my eyes are on the newer side to this.[/QUOTE]
You're welcome, and it fortunately looks so far like you may be in luck about saving your Windows install. Did you run the last two commands in my previous post to install a Windows MBR? Also, please post:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
Note "-l" is a lowercase L, not a one.

---

### Post by koolcracker on 2008-12-03
Yup, I ran everything.

ls -l /mnt yields:
```
total 2361794
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-06-25 17:45 Boot
-rwxrwxrwx 1 root root     333203 2008-01-20 21:24 bootmgr
-rwxrwxrwx 1 root root       8192 2008-02-05 17:08 BOOTSECT.BAK
drwxrwxrwx 1 root root     475136 2008-11-19 22:45 Config.Msi
-rwxrwxrwx 2 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 08:02 Documents and Settings
drwxrwxrwx 1 root root          0 2008-06-25 19:03 DRIVERS
drwxrwxrwx 1 root root          0 2008-06-25 18:42 Icons
drwxrwxrwx 1 root root          0 2008-06-25 15:35 Intel
drwxrwxrwx 1 root root          0 2008-09-18 18:24 MSOCache
-rwxrwxrwx 1 root root 2417524736 2008-11-19 22:41 pagefile.sys
drwxrwxrwx 1 root root          0 2008-01-20 21:32 PerfLogs
drwxrwxrwx 1 root root       4096 2008-10-07 17:24 ProgramData
drwxrwxrwx 1 root root      24576 2008-10-20 17:49 Program Files
drwxrwxrwx 1 root root          0 2008-06-25 15:34 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-06-25 19:12 RRbackups
-rwxrwxrwx 1 root root         86 2008-06-25 18:25 setup.log
drwxrwxrwx 1 root root       4096 2008-07-03 10:53 SWSHARE
drwxrwxrwx 1 root root       8192 2008-06-25 15:07 SWTOOLS
-rwxrwxrwx 1 root root         61 2008-06-25 18:04 syslevel.lgl
drwxrwxrwx 1 root root      28672 2008-11-19 22:45 System Volume Information
-rwxrwxrwx 2 root root       1732 2008-06-25 19:11 tvtpktfilter.dat
drwxrwxrwx 1 root root       4096 2008-06-25 15:31 Users
drwxrwxrwx 1 root root      49152 2008-11-18 14:33 Windows

```

but I don't think that my boot.ini file exists, and I don't know how solveable that is, but I have a feeling you might.

---

### Post by caljohnsmith on 2008-12-03
OK, I see now, I didn't realize you had Vista instead of XP; that's why you don't have a boot.ini file. Anyway, that's great news the Windows partition mounted OK, and it looks like everything is there; how about rebooting, set your BIOS to boot the Windows sda drive (if it isn't all ready set that way), and let me know exactly what happens when you try booting the sda drive. :)

---

### Post by koolcracker on 2008-12-03
Haha sorry I wasn't clear. One question before I do, would I set the boot line to be sda2, or would I use hda0, 2? 

I don't want to restart yet either, because I just noticed something that alarms me. My linux root or home folders dont show up anymore when I run the fdisk command, the only linux partition was my external harddrive. Omitting my harddrive, the only partitions listed are:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         856     6873088    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         856        3467    20968448    7  HPFS/NTFS

```

Is there a reason they shouldn't be showing, or did something go wrong?

---

### Post by caljohnsmith on 2008-12-03
I asked you in post #18 if you wanted to recover any of those linux partitions that were listed, and you didn't answer, so I assumed you didn't need them. You'll have to go through the whole testdisk procedure again if you want to recover them; go ahead and post the output of the deep scan results in case they are slightly different, and go through each of the linux partitions using "p" to list the root directory of each partition. Based on what they list, let me know which are the linux partitions you want to recover.

---

### Post by koolcracker on 2008-12-03
Okay, thats my mistake. I was under the impression that all of the partition int he list were ones that had been deleted, and thats what the D stood for, but that included all partitions, correct? So just to clarify, in order to keep the linux file structure I have now with my root and home partitions as well as the two windows ones, I will have to recover 4 partitions in total? I feel like I'm learning something.

---

### Post by caljohnsmith on 2008-12-03
> **koolcracker said:**
> Okay, thats my mistake. I was under the impression that all of the partition int he list were ones that had been deleted, and thats what the D stood for, but that included all partitions, correct? So just to clarify, in order to keep the linux file structure I have now with my root and home partitions as well as the two windows ones, I will have to recover 4 partitions in total? I feel like I'm learning something.
Yes, exactly, you'll need to recover all four partitions. Once you get the deep search results, make sure you select the exact same NTFS partitions that you did before by comparing their start/stop points and sizes with the previous partitions that testdisk listed; in other words, don't depend on them to be the 1st and 3rd NTFS partitions, although most likely they will be that way. Mark them as before, with the recovery NTFS partition as "P" and the Vista partition with "*". Then go through the linux partitions, and when you find the root and home partitions, mark them as either "P" or "L", depending on what choice it gives you. All the other partitions should be marked with "D" for delete. Did you have a swap partition on that drive too? If so, you would want to recover that too. After that, write the partition table again, and please post the output of the new fdisk results.

---

### Post by koolcracker on 2008-12-03
Alright, so now I have an issue. 

The harddisk (100 GB / 93 GiB) seems too small! (< 124 GB / 115 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                 8008   2  1 15136 119 61  114518752

and all of my other linux partitions have no information. It looks like I'll have to reinstall my linux, at least thats what I'm getting. I've gone ahead and backup all my data, so it will just be a matter of redoing everything. At least linux is free right?

I just want to make sure you think my windows will work so I have some sort of backup while I'm working on linux, or if there is still a way to recover linux then that would be perfect. Either way, Windows was what I was worried about because I need it for compatibility with certain things, and i most defintely do not have a cd.

---

### Post by caljohnsmith on 2008-12-03
That screen you posted I think occurs before you do the deep scan; did you go through the deep scan again and try using "p" to listed each partition's root directory? That's what you want. Also, before you use testdisk to rewrite the partition table again, it would be a good idea to backup the one you have that currently works for Windows at least. To back it up, just do:
```
sudo sfdisk -d /dev/sda > ~/Desktop/sda_partition_table.txt
```
And then save that sda_partition_table.txt file on your desktop some place safe.

---

### Post by koolcracker on 2008-12-03
I got that after both scans, and none of the linux partitions had any useable data on them unfortunately.

---

### Post by caljohnsmith on 2008-12-03
OK, it sounds like you'll just have to stick with the two Windows partitions and then reinstall Ubuntu. I would go ahead and try rebooting now to see if you can boot directly into Windows.

---

### Post by TeXtonyx on 2008-12-03
caljohnsmith hasn't gotten back to you yet so I will suggest something.

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         856     6873088    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         856        3467    20968448    7  HPFS/NTFS

This looks right because 1->856 is a rather small partition for
Vista to install into. You are not going to be booting with the
grub menu because Linux appears gone. That means you will be
booting with Vista. To boot Vista, Vista has to be installed to
the MBR. That was the step that cjs asked you to do.

So you need to set your boot order in bios, cdrom, hd0 (= sda)
So if Vista doesn't boot, you will need to have your Vista 
install cd ready. You want to use the Startup Repair option.
Here are instruction with pictures, and an attached screenshot.
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)
You want to choose "Startup Repair"

Now if you don't have a Vista install cd, but a manufacturer
recovery disk this won't work. So don't try it. Wait for cjs.
If it does work, then I would use Vista to delete any partitions
and leave them unallocated, meaning don't format them.

The reason is, that when you reinstall Ubuntu, one of the install
options is, 'largest continuous free space (guided)'. 
(the free space comes from the partitions you just deleted)
If you choose that then Ubuntu will automatically install there and
 leave Vista untouched. It will also write grub to the MBR, which
means you will boot Vista off the grub menu. If booting Vista
from the grub menu doesn't work, it usually means that menu.lst
needs a correcting entry to include Vista.

---

### Post by koolcracker on 2008-12-03
Alright, just to update, Windows still isn't doing anything, the recovery mode will boot, but windows itself won't. Unfortunately the recovery won't let me recover windows, so I feel like I'm probably stuck. I want to thank you for all the help you've given me today though, if you come back and read this.

Haha also, if you have any other suggestions, I would be fully open to hear them!

---

### Post by TeXtonyx on 2008-12-04
> **koolcracker said:**
> Alright, just to update, Windows still isn't doing anything, the recovery mode will boot, but windows itself won't. Unfortunately the recovery won't let me recover windows, so I feel like I'm probably stuck. I want to thank you for all the help you've given me today though, if you come back and read this.

Haha also, if you have any other suggestions, I would be fully open to hear them!

I showed you a screenshot so you would know what to look for.
That is what a Vista install cd shows you. From the Vista install
cd you can start bootrec or Startup Repair. A recovery cd will
not have those options so don't use it and don't use the word
recovery, because I can't tell what type of cd you used. I would
be able to perhaps help if you give the error message rather than
saying something vague like Windows won't boot. You might think
of booting into Safe Mode as "recovery mode will boot".

You should report something like: I booted from the install cd
and tried Startup Repair, but it failed and gave the following
error report foo foo foo foo. Or you say Startup Repair seemed
to work, no error messages, but Windows still would not boot
and gave the following error report foo foo foo foo.

So when you say 'it didn't work' I can't tell from that kind of
information what went wrong, so I can't say how to fix it. I
can't offer another suggestion because I don't know what you've
tried. So did you get to the screenshot I included in the last
post? How about a more detailed account including errors that
describes what happened after you saw or didn't see Startup Repair.

---

### Post by koolcracker on 2008-12-04
Sorry, I never recieved a cd with my windows, it came preloaded on my machine. The error message that comes up however says that the file "windows\system32\winload.exe" is damaged or cant be found. I'm kind of freaking out now, since I have to compeltely reconfigure my ubuntu and I didn't even get my windows working again, so it was sort of all for nothing.

---

### Post by TeXtonyx on 2008-12-04
> **koolcracker said:**
> Sorry, I never recieved a cd with my windows, it came preloaded on my machine. The error message that comes up however says that the file "windows\system32\winload.exe" is damaged or cant be found. I'm kind of freaking out now, since I have to compeltely reconfigure my ubuntu and I didn't even get my windows working again, so it was sort of all for nothing.

Ok, those kinds of computer often come with a recovery cd made by
the manufacturer. If not, then they often have a hidden recovery
partition on the hard drive with special instructions about how
to boot to that hidden partition, like tap F11.

Anyway, so you don't have a Vista cd then? You said "the recovery
mode will boot". Did you mean Safe Mode where you tap F8 during
bootup? If you get that far it's a good sign. 

But if you didn't mean that then you need some sort of rescue cd
and Neosmart has a download for a Vista rescue cd. The thing is
you can't install Vista with it like a regular Vista install cd.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

It is inconvenient that it is a .torrent file which means that 
you need a torrent downloading program to download the .iso
file so that you can burn it and boot to it. You'll need to
make your cdrom first to boot in the bios boot order. The
boot process often displays a message about what key to use to
enter into the bios so you can change the boot order to cdrom
if you haven't already done that.

I have a copy of this disk but I haven't had to use it, so I'm
not entirely sure what all is on there. I'm am sure that you
can run fixmbr, and fixboot which is part of bootrec. 

In the meantime I'll look up your error message. 
Well, it doesn't look good, the solutions suggested Startup Repair
or a full Repair install, so you need a real Vista install cd.
It seems to me that you ought to try a Vista Recovery Disk from
the Neosmart torrent because I don't see any other options.

---

### Post by TeXtonyx on 2008-12-04
Well, my Vista recovery cd from Neosmart wouldn't boot, so I can't help you
with instructions other than to run fixmbr and fixboot.

Byw, did you complete caljohnsmith's suggestion?

"And lastly, it would be good to reinstall a Windows MBR to that drive 
since only Windows will be on it, so you can do that with: 

Code:

sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda  "

---

### Post by TeXtonyx on 2008-12-04
Finally, some good news. I burned the vista recovery cd again and
it worked this time, and it did offer Startup Repair. I'll attach
the image again of the Startup Repair screenshot.

[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)
You want to choose "Startup Repair"

I don't know what else to try if this doesn't work, the next step
is a Repair install which takes a Vista install cd.

After I downloaded the Vista .iso file. I browsed to the folder 
that it was in and right-clicked. This pops open a menu with some
choices, one of them is close to 'write to disk'. Select that
option and another window pops up and lets you select the writing
speed, I always use 4x. You need to have a blank cd in the burner.
Set bios to boot from cdrom, put the cd in the cdrom drive,
and then it gives a message boot from cd: press any key
Don't forget to read the tutorial above first. You will be
choosing "Repair your Computer" at an early stage.

No computer procedure is infallible, so remember to do your backup first.

---

### Post by caljohnsmith on 2008-12-04
It looks like TeXtonyx has all ready given you some great advice about fixing Vista with the Vista Recovery CD from Neosmart, but I just wanted to add that part of your problem might be because your Windows "disk signature" in your MBR is all zeros; Vista uses a 4-byte disk signature that comes right before the partition table in the MBR, and if you ever change the disk signature, Vista often will refuse to boot. So I'm guessing that the original disk signature in your MBR was not simply zeros (not likely), so that could be at least one cause of your Vista problems right now. If you follow TeXtonyx's instructions, that should hopefully be enough to get Vista to recognize the new disk signature and adjust accordingly, but if not, then I would try doing the following command from the Vista Recovery CD:
```
bootrec /rebuildbcd
```
Anyway, let us know how it goes.

---

### Post by koolcracker on 2008-12-04
You guys are great, thanks for sticking with this with me. Im going to download that cd right now. i was looking for soemthing like it last night, vut all I could find was ordering a new one from windows, and they wouldnt accept my serial code because mine was an OEM install, and I couldn't find a place at Lenovo to request one. Thanks alot! And I had run that command.

---

### Post by TeXtonyx on 2008-12-04
bootrec /rebuildbcd

Yes, I forgot that one. I just looked this up on the Microsoft 
website and they say, that if Startup Repair doesn't work, then
to try bootrec next and also the next two commands as well.

bootrec /fixmbr
bootrec /fixboot
(bootrec /rebuildbcd)

All of those commands are executed from the Command Prompt. The 
Command Prompt is the bottom option under "choose a recovery tool"
in the screenshot I've uploaded before.

One types in commands at the Command Prompt very much like how one
types in commands after opening a terminal in Ubuntu. <enter>

This Vista recovery cd doesn't come with the full capability as
the Vista install cd, so this had better work. I'm afraid that
Lenovo would have sent you their manufacturer recovery cd that
is less capable than the Vista install cd. The OEM cd works but
erases all the data on the drive and then reinstalls. If this
Startup Repair and/or bootrec works, you will still have your
data. All in all, it seems like a good idea to backup key data.
The Vista recovery cd which you are downloading is different
from the OEM recovery cd which has drivers for your system also.

---

### Post by koolcracker on 2008-12-04
Thank you so much you guys, you saved my system! Those commands worked like a charm I owe you guys big time, this is such a relief.

---

### Post by caljohnsmith on 2008-12-04
Since you lost your Ubuntu root partition on the Windows drive, just reinstall Ubuntu and you will get Grub back. Anyway, glad to hear your Vista is working again; cheers and let us know if you run into problems installing Ubuntu. :)

---

### Post by koolcracker on 2008-12-04
Haha no actually, I didn't lose my root partition at all. I just had to boot up the live cd and reinstall GRUB and everything was fine and dandy. This baby's coasting along just fine now. Thanks again for all the time you spent with me yesterday guys, I really appreciate it.

---

