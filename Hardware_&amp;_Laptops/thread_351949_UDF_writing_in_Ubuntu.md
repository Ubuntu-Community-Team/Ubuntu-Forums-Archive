---
title: "UDF writing in Ubuntu"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by AllBuntu on 2007-02-02
I am after the 100-year archiving solution and would prefer to have a Linux solution for it.

1. Just copying your favorite 4GiB fileset makes Nautilus cop out, so it has to be command window (verified in Dapper and Edgy, samba may be the culprit) The window goes away. So let's go command window.

2. Since samba can not authenticate in a Windows domain, we'll use sshfs to access our Windows boxes with Openssh installed there.

3. Installing and configuring UDF tools, it will not write to a USB writer, it gives error message "trying to change type of multiple extents" (the same as if you try to write to a disk that is mounted) but it does work for an ATA-connected writer. Let's use ATA.

4. Packet writing to a rewritable disk using UDF file system crashes, the command window goes away. We want reliable media, so DVD+R is what we want anyway, so let's use DVD+R without packet writing.

Here comes the question:
What is the magic command-line sequence to produce a UDF revision 1.50 or higher, utf-8 encoded DVD+R using an ATA writer /dev/hda from a folder /data in the file system?

I suspect it would include things like dvd+rw-format, mkudffs, cp -prv and more.

Greatful for any help

---

### Post by AllBuntu on 2007-02-02
In good style I will here answer my own question:

     It is not possible.

a. mkisofs/growisofs uses some old compatibility mode from UDF 1.02 we don't want to hear about.
b. A bug in udftools prevents file sizes larger than 1 GiB (1,073,741,824 bytes.) I think UDF supports 16,777,216 TB (2**64) per file, that is.

Below is the closest we can get for now
```
dd if=/dev/zero of=file.iso bs=1024 count=4589800
mkudffs file.iso
mkdir /mnt/loop
mount -o loop -t udf file.iso /mnt/loop
cp big_file /mnt/loop
umount /mnt/loop
growisofs -speed 4 -Z /dev/dvd=file.iso
```

So, right now two candidates are Windows Vista and Mac OS X 10.4.x. I will try both.
- I think in the mac case you have to use command line, since Apple prefers their own proprietary HFS file system.
- Windows Vista claims UDF and also "Live UDF" which is the random access packet writing feature.

I would recommend the UDF reader issued by the standards folks that will tell you what UDF you really got. There is a lot of UDF you don't want. In particular anything coming out of Windows payware.

---

### Post by AllBuntu on 2007-02-03
So Mac OS X 10.4.8 with the superdrive does the job (my Intel mac is really an Ubuntu server, but there is still an OS X partition on there) A little research revealed the best archive media out there being DVD+R written at 4x or 8x. I wrote a 3.3 GiB file (the Fedora core DVD), a 255-character file name, and an international file name (125 a-ring + 5 character extension) it all came out great in UDF 1.50.

Mac stuff:
(put my stuff in the folder 070201_File on the Desktop)
```
hdiutil makehybrid -o 070201_yes -udf 070201_File/

```
Then  diskutil > Images > Burn, browse to your imagefile, click Burn. The folder name will be used as the name of the disk, in this case 070201_File

On Ubuntu, I installed the udf verifier from here: [http://www.hitech-projects.com/udf](http://www.hitech-projects.com/udf)
found my drive with
```
./udf_test -showscsi
```
and then ran the test with
```
./udf_test -scsi 3:0
```
It verified fine. The only thing is that Apple does not write duplicate media descriptors, in case your directory gets scratched. But oh...

---

### Post by dcstar on 2007-02-03
> **AllBuntu said:**
> I am after the 100-year archiving solution and would prefer to have a Linux solution for it.
.......

Firstly, burnt DVDs will be lucky to last a handful of years - under optimum storage conditions - so using them for any sort of long-term archiving is a big gamble at best, and probably a path not even worth considering if you value the data you want to archive.

You also have the issue of any old-technology based archiving, and that is you must have a hardware platform available to read your archives many years after it is (usually) obsolete.

The only real way to archive electronic data over any period is to keep transferring ALL of your data from one medium to another every two or three years. This usually means that the technology for the old and new mediums you are using is still available and supported, but it is something that must be done on a continuous basis.

I currently have 8" floppy disks that I now have no way of reading, (along with quite a few 5.25" ones), soon 3.5" floppies will be a part of people's memories, and I reckon any CD of DVD that I burnt more than 3 years ago will be problematic at best if I ever try to get every bit of data off them.

---

### Post by Arador on 2007-02-05
> **AllBuntu said:**
> Below is the closest we can get for now
```
dd if=/dev/zero of=file.iso bs=1024 count=4589800
mkudffs file.iso
mkdir /mnt/loop
mount -o loop -t udf file.iso /mnt/loop
cp big_file /mnt/loop
umount /mnt/loop
growisofs -speed 4 -Z /dev/dvd=file.iso
```


I just tried this solution, but it is core dumping:
```
File size limit exceeded (core dumped)
```
I don't have any ulimits. :confused:
[quote=AllBuntu's Avatar  	
AllBunt]A bug in udftools prevents file sizes larger than 1 GiB[/quote]
Am I understanding things right when I conclude that the kernel also suffers from this?

---

### Post by AllBuntu on 2007-02-24
Hi Arador,

You are right, there is a kernel "bug"! They somehow figured out that udftools corrupts files somewhere north of 1 GiB, so there is some sort of hard coded limit implemented. This is why udftools in my mind are not worthy for use. Meanwhile, I use OS X 10.4.8, will attempt Vista, and I emailed the administrator of the udftools, no answer. In all, for Linux: problem known, no fix available.

(whenever I find a piece of anything, I put it to the test to see if it's worthy my use, and udftools clearly is not)

When it comes to UDF and archiving on UDF DVDs, I have found all major operating systems currently supporting UDF (OS X, Windows, Linux.) ISO 9660 has been around for something like 20 years, so I therefore bank on computers being available for at least the next 20 years with the ability to read a UDF 1.5 file system.

The DVD+R media is "guaranteed" for 100 years by various manufacturers, and south of pre$$ed media I think this is our best option. That physical media format (the circular optical disc) has been around for 25 years or so and that's why again, I think this is the best bet.

avoid: disks in cassettes, proprietary burning software, non-lasting media, proprietary technologies, single-source-anything and you'll be fine! I think there is only one threat to our archives and that is scratched disks. And we can handle that!

Harald

---

### Post by AllBuntu on 2007-03-11
Ok, back with a report of Windows Vista Enterprise Edition (kind of similar to Ultimate for consumers) My big-business employer kindly provided a free copy.

Vista allows you two ways of writing optical media, both of which are 100% different from Windows XP. I smell a mess...

MS loaned concepts from OS X, so we have Mastered and Live File System.

Mastered is UDF 1.02, which is probably the most portable format, however, it is so old, we  don't want it. On the mac, using mastered, you can pick what file system you want , using the command window for very specific needs. Also, Vista fails to establish the unique volume ID that kind of keeps your disks apart. Vista 0, Mac 1.

Live File System is UDF 1.02, 1.50, 2.00, 2.01. I tried 1.50, since I was hoping to read it on the mac.
Microsoft-UDF 1.50 does not read on the mac.
Microsoft-UDF 1.50 has tons of errors (39 errors, two warnings) using udf_test
It appears Live File System is not at all portable.
Vista 0 Mac 1.

So MS has you selecting between stonehenge and Vista-only. Piece of crap. btw, Vista does not crash like XP does. However, after a week or so of up-time it slows significantly and starts repainting the screen for minutes at a time looking for lost memory. Don't even think about it with less than 2 GiB RAM. I have not tried it, but Beryl sounds like a dream.

For serious DVD writing: get a Mac

Regards,

Harald Rudell

---

### Post by Titan3025 on 2007-09-07
I also run into this issue on my Thinkpad T43p with a DVD Ram that I am trying to write a 2.6gb file to.

After 1gb the write operation stops and it also says file size limit exceeded (core dumped). :-(

There is nothing suspicious in the system log. No error message or anything else regarding the disruption of the write operation.

Cheers,
titan3025

---

### Post by madpotato on 2007-10-07
For now (till it's fixed), I think you guys are better off with Nero Linux, cause it has no problems with UDF > 4GB

---

### Post by Flice on 2007-10-14
The 1Gb UDF bug is fixed as of current gutsy. I am able to create a dvd-sized image, initialize it with udf, mount it, copy a 4.4Gb file onto it, unmount and burn the image. All this using udftools.

---

### Post by JonathanRRogers on 2007-10-22
You can make file full of zeros without actually copying them from /dev/zero by taking advantage of file holes or implicit zeros.This avoids the wasted time required to copy zeros from /dev/zero to the image file which will only be overwritten when you copy real files into it.

```
dd if=/dev/zero of=/var/tmp/DVD-R_image.udf bs=1024 seek=4589799 count=1
```

This produces a file of 4589800KiB of zeros instantly. It only occupies one KiB on the disk until nonzero bytes are written into it.

---

