---
title: "Mounting NTFS Raid 0 Array"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by gagge on 2006-05-30
Hello, I've searched the forums and Googled alot but I can't find any good information about my problem.
The thing is I recently switched from Windows to Breezy Badger, I kept my backups on an NTFS Raid 0 array which I now would like to mount.

The disks show up as /dev/sdc1 and /dev/sdc2, 300 GB each, I guess it only should be only one 600 GB if the Raid thing worked.

I have a MSI K8N Neo2 nForce3 motherboard with the nvraid chipset, all raid settings are OK in BIOS.

I guess it wouldn't be too hard to mount an NTFS partition, however, when it's both NTFS and Raid it's just too much for me, could someone post a guide that's easy enough for a newbie like me?

---

### Post by djgrandmarquis on 2006-05-30
I had a similar problem when I installed Kubuntu on my desktop. I had XP running on a RAID-0 array using my Epox mobo. I was under the impression that I had hardware RAID capabilities from my motherboard.

It turns out that the nvraid is not actually hardware RAID, it's "fakeraid." That is, there is a software driver (Windows-only) that runs near the BIOS-level. So it's actually software RAID, advertised as hardware RAID.

That was the last straw for me. I completely swiped Windoze off my drive and started with a fresh Linux ext3 software RAID-0 array.

So, do you have a hardware RAID controller? I assume you mean the controller is part of the motherboard since you said "nvraid." You probably had to install a RAID drive from a floppy during the Windows install process? 

Sorry for the bad news, if I understand you correctly.

---

### Post by gagge on 2006-05-31
Yes, I think it's "fakeraid", however when I boot, during POST I see a screen saying it found a "600 GB healthy striping array"

Hm, yes, software raid:
> 
 • NV RAID (Software)
• Supports up to 4 SATA & 2 ATA133 Hard drives
- RAID O or 1, 0+1, JBOD is supported
- RAID function work w/ATA133 + SATA H/D or 2 SATA H/D


I only need to access my files so that I can move them to another disk, don't need write permission and that stuff.

---

### Post by djgrandmarquis on 2006-05-31
As far as I know, there is not a Linux driver for nvraid. (The one that comes with the motherboard is Windows-only.) So it will show up fine in the POST, but Ubuntu won't be able to decipher what's what on the array. Therefore you won't be able to mount the NTFS array in Ubuntu.

Maybe trying Googling for a Linux nvraid driver? Sorry to disappoint.

---

### Post by bmhm on 2007-01-06
[FONT="Verdana"]Well i found this:
```
bmhm@Sentinel:~$ sudo dmraid -s
*** Set
name   : nvidia_fidecdga
size   : 312602972
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0

```

and this:
```
bmhm@Sentinel:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_fidecdga", stripe, ok, 156301486 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_fidecdga", stripe, ok, 156301486 sectors, data@ 0

```

to activate it, try
```
sudo dmraid -ay
```

if it works, you will see a new device listed in /dev/mapper
If you only have a control file, it didn't work (as for me :( )

Please tell me, if you can find out more.


NVidia permitted using their driver for linux-users, god knows why. Anyway, I found this:
[http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)

If I make some progress, I will keep you up-to-date

Regards[/FONT]

---

### Post by bmhm on 2007-01-06
[FONT="Verdana"]As you can read here: [http://www.kernel.org/git/?p=linux%2Fkernel%2Fgit%2Ftorvalds%2Flinux-2.6.git&a=search&h=HEAD&st=commit&s=sata_nv](http://www.kernel.org/git/?p=linux%2Fkernel%2Fgit%2Ftorvalds%2Flinux-2.6.git&a=search&h=HEAD&st=commit&s=sata_nv)
Many changes are being made to the kernel at the moment, regarding sata_nv.

As soon as the new Kernel 2.6.20 arrives, I'm going to test it for sata_nv to be working.

As my Computer Magazine (c't - [http://www.heise.de/ct](http://www.heise.de/ct) ) wrote, there will be explicit more hardware support for nvidia-based chipsets like nForce 4 (the one I have) :)

Regards[/FONT]

---

### Post by sayword on 2008-01-26
I know this is an old post but wondering if someone can point me in the right direction for the solution of this thread...

I'm booting through the latest version of Ubuntu LiveCD and I have 2 120GB SATA hard drives in raid 0 on a ASUS M2N-SLI Deluxe Mobo that i have windows and all my files stored on...now, I see my raid drives in ubuntu but can not mount it and says:

 "$MFT has invalid magic, Failed to load $MFT: input/output error failed to mount '/dev/sda1': input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on windows then reboot into windows twice.  The usage of the /f paramater is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory. (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details"

now, i do have SoftRAID/FakeRAID on my computer because it's controlled by nvraid software...I have done the chkdsk /f prompt in the windows repair utility because I have a corrupt file in windows which is why I want to run Ubuntu LiveCD just so I can access my drive and back up all my data before I do a fresh install of windows....

Or does anyone offer any other alternative to backing up data on a corrupt file system of windows...

---

### Post by 3vi14n931 on 2008-04-26
I think I may have some help for the people posting in this thread, I too have  a Nvidia fakeraid with a NTFS partition I wanted to preserve. I scoured the web and found a few simple commands that will make things easy on you.

Insure that dmraid is installed. (Search dmraid in your package manager to check)

run the command "> sudo dmraid -ay"
This will activate you raid drives arrays and partitions.
Output should look like this.

> RAID set "nvidia_aifccjbb" already active
RAID set "nvidia_aifccjbb1" already active

The text in quotes will differ from system to system, but the important thing here is the second line, the one that ends in one. That signifies the first partition on that drive. So in order to mount this partition all you have to do is.

> sudo mkdir /media/raid
sudo mount -t ntfs /dev/mapper/nvidia_aifccjbb1 /media/raid

This will mount your raid system (assuming it is already formated with a ntfs partition).

If you do not have a partition one the drive yet all you have to do is.

> cfdisk /dev/mapper/nvidia_aifccjbb

Configure you partition(s) and  mount them.

---

