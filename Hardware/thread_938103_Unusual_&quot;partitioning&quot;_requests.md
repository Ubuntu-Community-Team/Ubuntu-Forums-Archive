---
title: "Unusual &quot;partitioning&quot; requests?"
date: 2008-10-04
forum: Hardware
---

### Post by computer_freak_8 on 2008-10-04
I was wondering about how to do a couple of things that I haven't been able to get an answer for:

1. How do I setup a partition on an external storage device to be read-only to both Windows and Linux?
2. How do I "partition" (don't know if this is the correct term) an external storage device so that it appears as two different devices? (For example, cause a flash drive to appear as the devices /dev/sdb1 and /dev/sdc1 instead of the devices /deb/sdb1 and /dev/sdb2.)


Thanks,

computer_freak_8

---

### Post by mssever on 2008-10-05
> **computer_freak_8 said:**
> 1. How do I setup a partition on an external storage device to be read-only to both Windows and Linux?I'm not positive about this, but I don't think that's possible. However, some devices have a read only switch, and I don't know how those switches work.
> 2. How do I "partition" (don't know if this is the correct term) an external storage device so that it appears as two different devices? (For example, cause a flash drive to appear as the devices /dev/sdb1 and /dev/sdc1 instead of the devices /deb/sdb1 and /dev/sdb2.)
That's not possible. And it's really not necessary, anyway, as I don't think there's anything that you can do with partitions on separate devices that you can't do with partitions on the same drive.

---

### Post by computer_freak_8 on 2008-10-05
> **mssever said:**
> I'm not positive about this, but I don't think that's possible. However, some devices have a read only switch, and I don't know how those switches work.
...
That's not possible. And it's really not necessary, anyway, as I don't think there's anything that you can do with partitions on separate devices that you can't do with partitions on the same drive.

The first one, I'm not sure about either. The second one, however, I **know** is possible. I'm typing in reference to U3 drives. They have it appear as two different devices - a CD-ROM and a standard flash drive, even though it is really just a flash drive.

---

### Post by mssever on 2008-10-05
Interesting. I checked out my flash drive and discovered that the second "device" specifically shows up as a CD drive, and is named as such: ```
~$:  ll /dev/disk/by-id/usb-SanDisk_U3_Cruzer_Micro_00001671867151C3-0\:*
lrwxrwxrwx 1 root root  9 2008-10-05 18:37 /dev/disk/by-id/usb-SanDisk_U3_Cruzer_Micro_00001671867151C3-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2008-10-05 18:37 /dev/disk/by-id/usb-SanDisk_U3_Cruzer_Micro_00001671867151C3-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-10-05 18:37 /dev/disk/by-id/usb-SanDisk_U3_Cruzer_Micro_00001671867151C3-0:1 -> ../../scd1
```Notice that the U3 partition is labeled scd1, not sdc1.
```
~$: mount
<snip>
/dev/sdb1 on /media/SEVERANCE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd1 on /mnt type iso9660 (ro)
```Note that I had to manually mount /dev/scd1 as it doesn't get automounted--thankfully, since U3 is a bad idea that just gets in the way and provides absolutely no useful functionality.

---

### Post by computer_freak_8 on 2008-10-05
> **mssever said:**
> Note that I had to manually mount /dev/scd1 as it doesn't get automounted
I (temporarily) have mine set so it won't.

But yes, it's odd... What determines what device the kernel(?) sees a device as? I haven't been able to replicate it with "dd" however, since my normal flash drive is seen as, well, _one_ device.

---

### Post by mssever on 2008-10-05
I'm venturing into unfamiliar territory here, but I think that hard drives and CD drives appear different to the system (remember the old days of messing with ATAPI drivers to install Win 95 from the CD?). I'm pretty sure that flash drives generally present themselves as hard drives, while apparently U3 uses the CD interface. You'd have to delve into hardware specs to discover the technical difference. It's probably a low-level difference, and you might not be able to control it from software.

---

### Post by computer_freak_8 on 2008-10-05
Okay, thanks. Do you have any good resources for me to look at? Links?

---

### Post by iponeverything on 2008-10-05
to mount read-only:

mount -o ro /dev/sdax /mnt

if already mounted on /mnt:

mount -o remount,ro /mnt


As for getting a one device to show up as two.. i have no idea.

---

### Post by computer_freak_8 on 2008-10-05
iponeverything:

Thank you, but I already know how to *mount* as read-only; I'm looking to make a partition/filesystem read-only - so that it can't be mounted any way except read-only. Basically, emulate the write-protect switch found on some flash drives.

---

### Post by mssever on 2008-10-05
> **computer_freak_8 said:**
> Okay, thanks. Do you have any good resources for me to look at? Links?
Wikipedia and Google. What I wrote was based entirely on my own memory. Back in the day, I reinstalled Windows 95 many times on a box that could boot from a hard drive (of course), but not a CD. So the process was: boot from the Win95 boot floppy, load the proper CD driver, mount the CD, run d:\setup.exe. So clearly there's a difference. But I never bothered to find out what the difference was. I mess with software for fun, but I only mess with hardware when absolutely necessary.

---

### Post by iponeverything on 2008-10-06
yes.. I should have known that you knew how to mount read-only.

Take a look at SeLinux -  My guess is that it can provide the functionality that you want with regard to read-only filesystem.

ref: [https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)

---

### Post by mssever on 2008-10-06
> **iponeverything said:**
> yes.. I should have known that you knew how to mount read-only.

Take a look at SeLinux -  My guess is that it can provide the functionality that you want with regard to read-only filesystem.

ref: [https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)
You're still missing the point. Read the original post. The OP wants the partition to be read-only in both Windows AND Linux, presumably on any machine he plugs the device into. That means that there must either be a way to accomplish that with software that lives in the device and automatically runs on all OSes, or there must be a hardware setting, like the read-only switches on some devices.

---

### Post by computer_freak_8 on 2008-10-06
> **mssever said:**
> ...wants the partition to be read-only in both Windows AND Linux, presumably on any machine he plugs the device into. That means that there must either be a way to accomplish that with software that lives in the device and automatically runs on all OSes, or there must be a hardware setting, like the read-only switches on some devices.

Yes. I'm thinking of something like the following: 
1. Create filesystem, load with files I want.
2. Mark filesystem read-only using chmod.
3. Copy filesystem to flash drive using dd.
4. Enjoy write-protected (read-only) flash drive.

Now, I'm pretty sure that the above "solution" is impossible, but it outlines my thinking of the type of process that would be used. I mean, I don't think chmod works on entire filesystems, nor dd for preserving those changes from being changed back with chmod.

I'm thinking of something as a solution that the only way to make it writable again would be to copy all files to another device, delete the (read-only) partition, re-create it, and then put the files back on it.

Also, I'm still wondering about the mysterious U3 act of having one device being seen as two.


Thanks all,
computer_freak_8

---

### Post by mssever on 2008-10-06
Somehow, I doubt if you'll be able to use the ext3 filesystem and still meet your Windows requirements, but the chattr +i command would probably do something quite similar to what you want if you're able to use ext2/3. See the [man page here]("http://linuxcommand.org/man_pages/chattr1.html")--for some reason, there's no man page in Hardy.

---

### Post by Chii on 2008-10-06
Hiya!  I might be able to help with the first question at very least this being because I more or less did that.

I dualboot with Vista and Kubuntu 8.04, and each of the OSes have their own partition (big enough to fit the installation and whatever programs they need).  With the rest as a shared space, and while others seem to not like the idea as much.  It has worked pretty well for me.  What I did was set the partition that I wanted to share as an NTFS partition, this way I can freely read/write from Vista, and after entering my password to mount it I can freely read/write from Kubuntu.  Ive even gone so far as to add it as a "D:\" drive in Wine so that I can install and run programs form there as well :)


At this point you can then go back and set the settings in each os (If Im correct at this point) to make them read only.  It's a long way to go about getting it done but it does work. 


As for the flash drive.  You should be able to load it in the partition program and define how you want to break it up.  (or so has been my experience in the past).

Hope this helps!
   -Chii

---

### Post by computer_freak_8 on 2008-10-06
> **Chii said:**
> As for the flash drive.  You should be able to load it in the partition program and define how you want to break it up.  (or so has been my experience in the past).

Herein lies the problem. Partitioning, (at least how I know how to do it,) "breaks up" a device into "pieces" in the form of /dev/sda1 and /dev/sda2. What I am trying to accomplish is to "partition" (probably not the correct term for what I am attempting) it so that is shows up as /dev/sda1 and /dev/sdb1, or something to that effect.

---

### Post by Chii on 2008-10-06
Hmmm, I've not tried to actually name them in any particular order so this is only a guess.

But could you just not define a volume name when you go about doing this?   Or if the partition program you are using is anything like the one that you are presented when you install (K/X/)Ubuntu; would you not be able to define the volume name there?

---

### Post by computer_freak_8 on 2008-10-06
> **Chii said:**
> Hmmm, I've not tried to actually name them in any particular order so this is only a guess.

But could you just not define a volume name when you go about doing this?   Or if the partition program you are using is anything like the one that you are presented when you install (K/X/)Ubuntu; would you not be able to define the volume name there?

I think that you're referring to mounting. Yes, I could mount a two partitions on a device under /media/sda1 and /media/sda2, or I could choose to mount them under /media/sda1 and /media/sdb1. But this does _not_ change what the computer (kernel?) "sees" them as.

---

### Post by Chii on 2008-10-06
Ah...then I'm not sure what else to suggest.  Sorry I can't be of more assistance :/

---

### Post by computer_freak_8 on 2008-10-07
> **Chii said:**
> Ah...then I'm not sure what else to suggest.  Sorry I can't be of more assistance :/

That's okay. You never know until you try.

Thank you for trying!

---

