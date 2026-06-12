---
title: "Failed Partition: Can't Boot Windows"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by ClaytonOT on 2009-02-23
I just attempted an Ubuntu install... and well to say the least it failed miserably. I followed the graphic guide step by step but as soon as the partition came around it hung on 0% but I decided to wait it out so I wouldn't mess anything up. 30 minutes later (around) I got some error but it disappeared immediately and it just dumped me into another partition attempt. At that point I was too worried to try it again so I went back to boot up Windows... and it's not happening.

I dont have my XP cd with me at college so from that point I can't do anything. I do have a RAID1 system, but I'm not sure how I can get that running without an OS. I'm running off a Live CD right now and I'm open to any suggestions. 

Taking a look at GParted my /dev/sdb2/ has a warning;

Goes on about how cluster accounts have failed.... File system check failed... NTFS is inconsistent. (Attached picture)

Tells me to run chkdsk on Windows, but seeing as I can't get into Windows that wont fly.

So looking for some help, thanks guy.

---

### Post by ClaytonOT on 2009-02-23
bump

---

### Post by zwygart on 2009-02-23
Try to run a filesystem check fsck.msdos or something.

On my computer also it has a warning on the ntfs filesystem. But it mount normally and boot normally.

I see that you have free space after the ntfs, try to install ubuntu there by choosing use free space. 

In a terminal type "fdisk -lu". This output similar infos as in your picture. To copy press CTRL+SHIFT+C, to paste CTRL+V in the post.

---

### Post by ClaytonOT on 2009-02-23
ubuntu@ubuntu:~$ fdisk -lu
Cannot open /dev/sda
Cannot open /dev/sdb

I attempted to boot XP from CD (it's not my own since I'm at college) which ended up in a BSOD running it normally. I hit F2 for system recovery and asked for some XP floppy disk which I've never seen before anyways.

I'm thinking my last resort is to just give up my drive to Linux then partition it to install Windows later... 

Its no longer giving me an option to use my free space, as it says I have none (atleast the Installer Partitioner says I don't have any, yet the GPartitioner from my Administration tools says I do have free space... :confused:

Is there anyway to run chkdsk from terminal on a Live CD? 

(I'm really noob to Linux so I appreciate the patience/guidance)

---

### Post by zwygart on 2009-02-23
Yes at this point choose Guided - Use largest continous free space.

If you have boot problem can you post the result.txt of [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) . This will contain full of usefull infos for us.

To run checkdisk : fsck
For others filesystem append the name : fsck.vfat for fat.
For the manual of fsck : man fsck   At the bottom it haves a list of supported fsck's.

---

### Post by ClaytonOT on 2009-02-23
> ubuntu@ubuntu:~$ fsck /dev/sda2
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda2 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
ubuntu@ubuntu:~$ 

I'm extremely hesitant when it comes to this. When it comes down to these technicalities I feel like a complete moron, I pretty much need my hand grabbed for this. 

So are there any specific lines I should be using. I know you've stated some earlier, but everytime I try something like;

> 
ubuntu@ubuntu:~$ fsck.msdos
usage: fsck.msdos [-aAflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the file system
  -A       toggle Atari file system format
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -r       interactively repair the file system
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck
ubuntu@ubuntu:~$ 


Any attempt for me to add an appendage just results in the same message.

---

### Post by zwygart on 2009-02-23
unmount your partition ```
umount /dev/sda2
fsck /dev/sda2
```

you have forgotten to add the partition to your second command. fsck.msdos /dev/sda2

Have you tried to install after in the free space?

Also you need to be root. Write sudo before any command mentioned above. 
Please post the output of "sudo fdisk -lu"

Also why are you talking about sdb and then sda?

---

### Post by ClaytonOT on 2009-02-23
> ubuntu@ubuntu:~$ umount /dev/sda2
umount: /dev/sda2 is not in the fstab (and you are not root)


The installer won't even recognize dev/SDA right now. It only sees dev/SDB. The GPartitioner though still picks up both, I don't know how the same program can see two different things...

> 
ubuntu@ubuntu:~$ fsck.msdos /dev/sda2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/sda2: Permission denied


---

### Post by zwygart on 2009-02-23
sudo fsck.msdos /dev/sda2

See my previous post, I added infos

---

### Post by ClaytonOT on 2009-02-23
Is this what you're looking for;

> 
ubuntu@ubuntu:~$ sudo fsck.msdos /dev/sda2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 0.


If you'd like to talk on AIM that'd be easier I think for the both of us. My s/n: Dear Forbidden

I won't be on till later but hopefully we can get in contact. Thanks again for your help so far.

---

### Post by zwygart on 2009-02-23
Sorry I never chatted and I have to go now.

sudo fdisk -lu

---

### Post by ClaytonOT on 2009-02-23
> 
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      144584       72261   de  Dell Utility
/dev/sda2   *      144585   488263544   244059480    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      144584       72261   de  Dell Utility
/dev/sdb2   *      144585   488263544   244059480    7  HPFS/NTFS


Theres the response.

Alright here's an update on the situation:

0x0000007B Inaccessible Boot Device- That's the BSOD I get after an attempted Windows install, it comes after it says "Windows is starting."

Seeing as I have a RAID, I'd imagine I'd need some drivers but I'm wondering if I could go about just disabling the RAID and see if Windows will boot from the disk.

---

### Post by ClaytonOT on 2009-02-24
Well here's the deal, bud.

I formatted my /dev/sdb and an installed Ubuntu 8.10. I still have my sba with all my Windows information and previous data which I can still access from Linux. I think my Windows stuff won't get fixed until I can get my own repair CD up here. I originally had an Error 25 from GRUB while attempting my first Ubuntu boot, but I disabled my first drive from BIOS and it booted without a hitch, now I have my first drive enabled again and pulling some files off it. 

Thanks for you help. I think from here on, it'll just end up with me formatting my first drive and installing clean Windows.

---

### Post by zwygart on 2009-02-24
I see some "strange" things on your fdisk. sda and sdb seems to be the same drive. This is porably of the RAID thing that you are talking. I don't know what that is, but others fixed the problem like you by disabling it. 

Happy to learn that it worked for you.

---

