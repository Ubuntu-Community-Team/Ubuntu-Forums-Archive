---
title: "Bought New 1TB Drive - Format With NTFS or EXT3?"
date: 2010-02-04
forum: Hardware
---

### Post by umechanism on 2010-02-04
I bought a new drive and will format it this weekend.  Should I use NTFS or EXT3?  I have both Vista and Linux machines on my network all of which will have access to the drive.  I know Vista can't read EXT3 but can Linux read NTFS?

Thanks!

---

### Post by wilee-nilee on 2010-02-04
The HD probably is ntfs stock. I left a external at ntfs so it could be read by any computer. Windows can read ext3 with a installed program I believe.

---

### Post by jenaniston on 2010-02-04
> **umechanism said:**
>  can Linux read NTFS?

Thanks!

Yes, it sure can.

 NTFS mounts in linux - so move files around - save files to USBs -
even take things out of the NTFS Recycle Bin and put back on Windows Desktop  . . . or Linux Desktop if you want to . . . yadayadayada

---

### Post by blur xc on 2010-02-04
...but linux permissions don't work w/ ntfs, if that matters to you.  Everything is root:root 777.

ext2fs I think is the driver for windows to read ext3, but maybe I recall there being a different driver for Vista than XP...

BM

---

### Post by pirateghost on 2010-02-04
if you do not plan on sticking that drive on a windows computer you can format it as anything you want.  is it an internal drive that you plan on sharing out via SAMBA?  if so, windows machines dont care about what filesystem is on it because they just use network protocols to access it and do not deal directly with the filesystem

---

### Post by pkm4o93 on 2010-02-04
Hi.   I notice while using large NTFS usb drive uses 30% of CPU (ntfs-3g )process while running torrents off that drive.   I dont know if fat32 would use the volume efficiently either.

---

### Post by jenaniston on 2010-02-04
> **blur xc said:**
> ...but linux permissions don't work w/ ntfs, if that matters to you.  



the 'nix file systems (unix or linux) will recognize and work with*** all*** the Windows partitioning filesystems . . .
In fact, format and*** make*** *all* your Windows fat16, fat32 and ntfs partition filesystems ***from*** linux.

Go into ***any*** file in your ntfs Windows partition ***from*** linux -
Or if it matters to you, do you need to r***emove files*** - ***add files*** - **do Microsoft Word** - delete or restore in the Recycle Bin on your NTFS partition . . . ? - all from linux.

Is there *anything* - even **one thing** - that you can ***NOT ***do on the Windows filessytem using *only* linux ?
Is there really much of any reason to have *any* Windows partition* at all* on your 1 TB drive  ? 

Or maybe just as an operating system "Smithsonian" exhibit to show the grandkids what the old OS "used" to look like -
 so yeah, maybe worth a few GB or so out of the Terabyte hard drive.

---

### Post by pkm4o93 on 2010-02-04
> **jenaniston said:**
> the 'nix file systems (unix or linux) will recognize and work with*** all*** the Windows partitioning filesystems . . .
In fact, format and*** make*** *all* your Windows fat16, fat32 and ntfs partition filesystems ***from*** linux.

Go into ***any*** file in your ntfs Windows partition ***from*** linux -
Or if it matters to you, do you need to r***emove files*** - ***add files*** - **do Microsoft Word** - delete or restore in the Recycle Bin on your NTFS partition . . . ? - all from linux.

Is there *anything* - even **one thing** - that you can ***NOT ***do on the Windows filessytem using *only* linux ?
Is there really much of any reason to have *any* Windows partition* at all* on your 1 TB drive  ? 

Or maybe just as an operating system &quot;Smithsonian&quot; exhibit to show the grandkids what the old OS &quot;used&quot; to look like -
 so yeah, maybe worth a few GB or so out of the Terabyte hard drive.

 Believe me , it will matter when you go to a friends house whos running windows 7, and your 1tb external is ext3. I will be changing my external to ext3 as soon as I get another drive I can backup to.

---

### Post by jenaniston on 2010-02-04
> **pkm4o93 said:**
> Believe me , it will matter when you go to a friends house whos running windows 7, and your 1tb external is ext3. I will be changing my external to ext3 as soon as I get another drive I can backup to.

It ***will not matter that the external drive is ext3.***

It is right that the windows won't recognize the linux, but **NOT** the other way around.
From linux OS, just do whatever on your friend's computer Windows partition - totally.
 
Also believe me - that when you put in your linux or unix live CD or USB in your library or a university computer - 
or your friend's Windows computer without or with an ntfs filesystem  -
you ***will*** be able to do whatever you like to and on their windows partition.

Booting from a live CD or USB will be the easiest for you -
 but an external USB picked in the boot sequence to boot ahead of your friend's hard drive -
whether 1 TB or about 4 GB (about the minimum for an external drive linux OS) will do juuust *fine*.

But, no - it just doesn't work the other way around  as windows only sees linux as "unallocated space".

---

### Post by LighthouseJ on 2010-02-04
I just finished confronting the same decision myself with this new RAID I'm setting up..  I went with ext3 because I didn't really trust Linux reading and especially writing NTFS as much as I might.  I remember when NTFS was read-only and experimental so the stigma of NTFS as being incomplete is still in my mind.

It's nice that it can read and write NTFS, but given the chance to use a filesystem the OS is more comfortable to write with, I'll go with ext3.

---

### Post by Ginsu543 on 2010-02-05
As you can see in my siggy, I have 2 x 1 TB drives. On each, I formatted the first 100 GB for OSes (NTFS for Windows XP and ext4 for Jaunty). I formatted the remaining 900 GB in NTFS as data partitions accessible in both Windows XP and both flavors of Ubuntu. I have never had any issues mounting, reading, or writing to my data drives in Ubuntu. I certainly trust Ubuntu to read NTFS partitions more than I trust Windows to read ext3/4.

I also recently bought a 1.5 TB external usb drive for backup purposes and I left it in its factory NTFS format. Again, no problems whatsoever backing up my files to the external drive.

---

### Post by blur xc on 2010-02-05
> **LighthouseJ said:**
> I just finished confronting the same decision myself with this new RAID I'm setting up..  I went with ext3 because I didn't really trust Linux reading and especially writing NTFS as much as I might.  I remember when NTFS was read-only and experimental so the stigma of NTFS as being incomplete is still in my mind.

It's nice that it can read and write NTFS, but given the chance to use a filesystem the OS is more comfortable to write with, I'll go with ext3.

I have an external 1tb ntfs esata drive that I regularly read and write to from Ubuntu.  I use it more from ubuntu than I do from windows, and it works 100% fine...

With this driver [http://www.fs-driver.org/](http://www.fs-driver.org/) you can access your ext3 partitions from windows.  Personally, I only allow read only access from windows.  

BM

---

### Post by umechanism on 2010-02-05
Thanks for the responses.  I'm going to use ntfs on the new drive since Windows machines will need to have access to it. I know I could partition 1/2 the drive to ntfs and the other to ext3 but ntfs will get me where I need to be.

Thanks!

---

### Post by Cabs21 on 2010-02-05
if you are not going to use this drive for a bootable OS then why not FAT32.  Everyone can read that and it is easy to work with.  Your only limitation is that you can not put files in the HDD that are larger then 4GB.  HD movies might not fit.

---

