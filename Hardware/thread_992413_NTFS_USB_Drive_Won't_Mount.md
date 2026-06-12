---
title: "NTFS USB Drive Won't Mount"
date: 2008-11-24
forum: Hardware
---

### Post by ratdog on 2008-11-24
Hello, I've been having troubles with my USB harddrive.  It worked fine for a while when I first got it, but now when I try to mount the drive it gives me this error...

[I]Unable to mount the volume.
NTFS signature is missing.  Failed to mount '/dev/sdc1':Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.  Maybe you mounted the wrong device?  Or the whole disc instead of a partion? Or the other way around?[/I]

I'm a newbie and don't really understand this message.
Can someone help??
Thanks

---

### Post by taurus on 2008-11-24
The last time you used it, did you just unplug it from a computer without unmount (or safely remove) it first?  Plug it in and open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by cdtech on 2008-11-24
You could try from a command line:
```
ntfsfix /dev/yourdevice
```
This will reset the NTFS journal.

---

### Post by nightmare0 on 2008-11-24
[INDENT]If you have a *cough* windows *cough* box you could try plugging it in, it should fix it, but if you are planning on using that drive mainly for linux and sometimes windows then why not format it in FAT32?
[/INDENT]

---

### Post by ratdog on 2008-11-24
I formatted it in NTFS so it would be compatible with my wife's windows laptop, but we just instaled ubuntu on it so maybe I will change the format sometime soon.  I do want to ve able to access what is currently saved on the drive though.  

Here is what the fdisk command spits back:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007c98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18729   150440661   83  Linux
/dev/sda2           18730       19457     5847660    5  Extended
/dev/sda5           18730       19457     5847628+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000088fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c41c845

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS


Thanks for the help!

---

### Post by thomas228 on 2008-11-24
> **nightmare0 said:**
> [INDENT]If you have a *cough* windows *cough* box you could try plugging it in, it should fix it, but if you are planning on using that drive mainly for linux and sometimes windows then why not format it in FAT32?
[/INDENT]

Hi 
I'm a relative newbie when it comes to linux but one thing I'd be cautious about if you reformat is to know if there are size limits on the format you consider. It looks like your drives are 160 GiB and larger. I believe FAT 32 has a 30 or 40 GiB limit.
Just a thought
Tom

---

### Post by nightmare0 on 2008-11-24
Yeah, if you are using it for your wife's laptop, then it would be relatively risky to resize a partition and reformat it in FAT32. Or if there isn't too much on there and you just put ubuntu/ or whatever linux. You should move her stuff off and reinstall ubuntu. And during installation partition it the way you want, for storage and for Linux and be able to put her stuff onto the FAT32 partition of the Drive.

---

### Post by nightmare0 on 2008-11-24
I did not even think about FAT32 restrictions but according to [http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32) it is limited to 2 Terabytes, I think. Hey I learned something new too!:)

---

### Post by ratdog on 2008-11-24
Yeah, I don't like FAT32 just because of the 4GB file size limit.

Oh, and to the earlier poster, I do believe I unmounted the drive properly last time.

Any ideas on how I can get my computer reading this drive?

---

### Post by taurus on 2008-11-24
What happens if you try to mount it by hand from a terminal?

```
sudo mkdir /media/sdc1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
```

---

### Post by ratdog on 2008-11-24
It gives me the same error:

NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by taurus on 2008-11-24
Can you connect that external harddrive to a windows machine and run defrag and scandisk of that drive?  Then, click the little icon at the bottom right to safely remove it.  Now, see if Ubuntu would automate it or if you can mount it by hand from a terminal.

---

### Post by iminhell on 2008-11-25
I found this thread as well as a few others as I had the same issue. This link --> [http://ubuntuforums.org/showthread.php?p=6247043#post6247043](http://ubuntuforums.org/showthread.php?p=6247043#post6247043)
Is the one that helped me the best, hopefully it will for you aswell.

---

### Post by ddiger on 2008-11-25
I had a similar problem. I had to take the usb drive, physically plug it into a windows machine & on the lower left hand side select remove usb storage device. Wait untill is says, it is safe to remove the device.

Simply unplugging it seems to lock it up & ubuntu won't see it or mount it. I have a 500GB drive formated NTFS with 4 separate partitions. I've had no problems with it since that time.

---

### Post by ndefontenay on 2008-11-25
I had the problem with an external USB HD.
I've found out I had to force mount it because it wasn't properly removed from windows and by then there were no more windows around...

force mounting can work

---

### Post by Kachiko on 2008-12-01
Force mounting is the only solution, unless you have a windows version somewhere (I don't have Windows any more, so I cannot try it for you)
Try these next steps:

A> sudo fdisk -l
This will give you some information that is useful. Even though this step is not necessary imho.

B> ntfsfix /dev/"yourdevice"
If you don't have ntfsfix, you can download it first using:
> sudo apt-get install ntfsprogs

now it is time to force mount your NTFS external USB drive:
C> sudo mount -t ntfs-3g /dev/"yourdrive" /media/"yourdrive volume" -o force

PS: "yourdrive" is the drive you want to mount, e.g. sdd1 or whatever name is given in "sudo fdisk -l"
PS2: "yourdrive volume" = NTFS volume, give by you, e.g. "ExtHD" or "USB-HD" whatsoever.

I hope this will help you further.

---

