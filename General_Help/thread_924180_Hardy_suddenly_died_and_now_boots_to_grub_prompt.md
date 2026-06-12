---
title: "Hardy suddenly died and now boots to grub prompt"
date: 2008-09-19
forum: General Help
---

### Post by riknos on 2008-09-19
I was just browsing away last night (also downloading backtrack and slax) and suddenly my Ubuntu 8.04 just died. The desktop froze and then the toolbars and all windows disappeared. I tried to reboot but instead of the usual menu.lst choices I was dumped at a grub command line. I tried various grub commands but grub could not find any files so could not boot. 

I took a look at the system with a Knoppix disk. Gparted showed the partition and the expected used and unused space. When I browsed the partition there was just lost and found - no other folders or files!!!

Please help someone and say there is something I can try to recover my system! I was only saying the other day how much I was enjoying using Hardy.
Could my system have had some sort of virus attack. Is it maybe just the file indexing that is lost?? 

Thanks in advance,

Richard.

---

### Post by AusIV4 on 2008-09-19
It's very unlikely that it's a virus. It sounds like a problem with your hard drive, though it may just be that your file system was corrupted.

I would suggest booting from your live CD and running fsck on the offending drive. Start out with something like:```
fsck /dev/sda1
```Though you may have to specify a different drive. If it doesn't run, we may have to use more options.

---

### Post by riknos on 2008-09-19
Thanks, this is the output:
> 
[root@main-pc media]# fsck /dev/sda8
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
Ubuntu_8.04: clean, 207508/3662848 files, 3225391/7323624 blocks



---

### Post by caljohnsmith on 2008-09-19
So all that is left in your Ubuntu partition sda8 is a "lost+found" directory? Have you browsed it to see if all your files are there, and maybe if the directory structure still exists? I'm wondering if sda8 really is your Ubuntu partition if that is the case. Please post the following:
```
sudo fdisk -lu
```

---

### Post by riknos on 2008-09-19
Yes, I have browsed the partion many times just to check. No directory structure, nothing apart from lost and found. sda8 is the right partition. Here is the output you requested:
> [root@main-pc media]# fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf24bf24b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   128696714    64348326    7  HPFS/NTFS
/dev/sda2       263466000   446446349    91490175    5  Extended
/dev/sda5       263466063   305411714    20972826    7  HPFS/NTFS
/dev/sda6       305411778   336866984    15727603+   7  HPFS/NTFS
/dev/sda7       336867048   368322254    15727603+   7  HPFS/NTFS
/dev/sda8       368322318   426911309    29294496   83  Linux
/dev/sda9       426911373   446446349     9767488+  82  Linux swap / Solaris



---

### Post by caljohnsmith on 2008-09-19
Well, I have no idea what happened then to your Hardy on sda8, but it sounds like you are faced with a reinstall. If you had some important files that you want to recover, you can use ["photorec"]("http://www.cgsecurity.org/wiki/PhotoRec") to recover them. Let me know how it goes.

---

### Post by riknos on 2008-09-19
Thanks again. I'll try photorec and and give you an update either way.

---

