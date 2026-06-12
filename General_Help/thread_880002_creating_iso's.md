---
title: "creating iso's"
date: 2008-08-04
forum: General Help
---

### Post by rules on 2008-08-04
Hi all

I have been trying to create an iso image from a dvd but with no luck.

I have tried this ... 
sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024 
... but this only creates a little 1 meg iso which can't be right.

I then installed Kiso, which seems to be working, but it has taken more than 4 hours now and it's not even half way yet.

Any ideas? other, quicker ways?

Cheers.

---

### Post by sisco311 on 2008-08-04
try:
```
dd if=/dev/cdrom of=file.iso
```

---

### Post by H4rm0ny on 2008-08-04
Loathe though I am to discourage people from the commandline, is there a reason why you don't want to use one of the GUI tools?

I use K3b for most purposes, but k9copy is the best, imo as it will copy nearly anything you throw at it (as well as encode movies). You should also be able to just right click on the DVD icon that appears in your file manager (it should appear in "/media" normally).

But if you do want to do it with dd, your problem is almost certainly the **if** parameter. You're getting 1M file regardless because you told **dd** that you had to have 1024 bytes. It probably shouldn't be /dev/cdrom (though it could be), but more likely /dev/scd0 or somesuch. If in doubt, check the file /etc/fstab to see what cdrom corresponds to, or try a df command if it's mounted.

You should also be able to drop the block size parameter unless you need it for some reason such as verifying the file.

dd if=/dev/scd0 of=file.iso

Hope this helps,

H.

EDIT: Wrote KDE instead of K3b first time around. Mental burp.

---

### Post by rules on 2008-08-04
Tried both cdrom and scd0 and both give me an iso of 96Kb ... I'm going to give k9copy a try.

---

### Post by Titan8990 on 2008-08-04
usually your first CDROM drive is /dev/cdrom0 not /dev/cdrom


Hope that helps.

---

### Post by sisco311 on 2008-08-04
make sure the cd is mounted:
```
mount
```
and use the device name listed by the mount command.

example:
> **/dev/scd0** on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=ivman)
```
dd if=**/dev/scd0** of=file.iso
```

---

### Post by sisco311 on 2008-08-04
> **Titan8990 said:**
> usually your first CDROM drive is /dev/cdrom0 not /dev/cdrom


Hope that helps.

you can use
```
sudo lshw -C disk
```
to list the logical name of the device

---

### Post by Titan8990 on 2008-08-04
That is handy command that I was not aware of.

---

### Post by rules on 2008-08-05
sisco, tried this command ... dd if=/dev/scd0 of=file.iso
and this time it created a larger iso, but it appears to be smaller than the amount of data on the dvd. I also did a md5sum check and it was wrong.

Any ideas?

---

### Post by H4rm0ny on 2008-08-05
> **rules said:**
> sisco, tried this command ... dd if=/dev/scd0 of=file.iso
and this time it created a larger iso, but it appears to be smaller than the amount of data on the dvd. I also did a md5sum check and it was wrong.

Any ideas?

How large was the iso? If the DVD isn't full, then the iso doesn't need to be large. The ultimate test would be to burn it back to DVD and see what you get, but you don't need to do that. If it's a movie, you can just open the file and play it. If it's data, then you can actually mount the iso with the following command:

```

mount -o loop -t iso9660 yourfile.iso ~/home/nameofemptydirectory/

```

Swap in the appropriate names in the above. It will be read only, of course.

What happened when you tried k9copy? Or the right-click option in your file manager?

I think you need to tell us:
The type of the DVD (is it data or a movie?)
The output of: *lshw -C disk*
The actual output of the dd command. Are you getting any errors reported? I'm guessing you are. Let us know what it says.

Then we can give you the exact command you should be using and tell you how large we expect the iso file to be (possibly).

Regards,

H.

---

### Post by WRDN on 2008-08-05
Put the disk in and wait for it to mount. Then, right click the icon that appears, select "Copy Disk" and select 'Copy Disk to' "File Image".

---

### Post by prshah on 2008-08-05
> **rules said:**
> 
Any ideas? other, quicker ways?


I've always used GnomeBaker / Brasero to create a disk copy (iso). Works flawlessly, everytime.

(An aside: After creating the iso, I use DVDisaster to augment the ISO image with ECC. Any disk then created with the ISO will continue to work fine even if it has upto 20% data damaged and/or inaccessible- scratches, etc).

---

### Post by rules on 2008-08-05
It is a Suse 11 DVD. For some reason my laptop's cd/dvd drive don't like linux cds and don't want to boot up with them so I have picked up a cool trick using unetbootin (had to use it to install Hardy), but I need an iso for it to work.

I'm trying WRDN's suggestion currently, so will see how that pans out :)

K9Copy did not want to work. Even though it saw/displayed the dvd drive it kept popping up an error about not being able to open dvd.

Here is that info ...

  *-disk                  
       description: ATA Disk
       product: ST9808210A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.01
       serial: 3LF08LKC
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d5aed5ae
  *-cdrom
       description: DVD writer
       product: DVD-RW DVR-K14RA
       vendor: PIONEER
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

---

### Post by H4rm0ny on 2008-08-05
Right. There is something wrong here.

Could you try the following please?

Firstly,
```

dd if=/dev/scd0 of=filetest1.iso

```

This should produce the named file, but I'll guess that it comes out far too small. Please could you paste the output of the command here for us, though. If it gives an error message, it will be useful to know what it is.

Secondly, assuming that the first didn't work properly, try this:
```

cat /dev/scd0 > /dev/null

```

Don't bother waiting for it to finish. Let it do its thing for a thirty seconds or so (you should hear that disc spinning), then stop it with Ctrl+C and follow it immediately with:
```

dd if=/dev/scd0 of=filetest2.iso

```

Let this run and see what filetest2.iso looks like. I'm hoping the cat command will give your system a little jiggle to sort out any read errors from the drive. If it does make a difference, then we'll go from there.

Good luck,

H.

---

### Post by Cresho on 2008-08-05
well, I been using iso master for cd and dvd

[http://www.ubuntugeek.com/iso-master-the-ultimate-cddvd-image-isonrg-editor.html](http://www.ubuntugeek.com/iso-master-the-ultimate-cddvd-image-isonrg-editor.html)

dont forget to select "new" before you start your project.

---

### Post by rules on 2008-08-05
This is what happens with those 3 commands ...

rafiq@rafiq-laptop:~$ dd if=/dev/scd0 of=filetest1.iso
dd: reading `/dev/scd0': Input/output error
224+0 records in
224+0 records out
114688 bytes (115 kB) copied, 2.76731 s, 41.4 kB/s
rafiq@rafiq-laptop:~$ cat /dev/scd0 > /dev/null
cat: /dev/scd0: Input/output error
rafiq@rafiq-laptop:~$ dd if=/dev/scd0 of=filetest2.iso
dd: reading `/dev/scd0': Input/output error
40+0 records in
40+0 records out
20480 bytes (20 kB) copied, 0.971958 s, 21.1 kB/s
rafiq@rafiq-laptop:~$ 

I also just tried Brasero which seemed to work fine till it got to 43% and then it just froze.

---

### Post by H4rm0ny on 2008-08-05
You should **not** be getting an input/output error with 
```
cat /dev/scd0
```

I don't know if you happen to have another drive lying around that you could try. However, in the meantime try this (this thread is turning into a complete HOW-TO on dvd problem diagnosis):

1. Mount the dvd, e.g. by just clicking on it in the Gnome File Manager.
2. From the terminal run ```
df
``` and note down the number of 1k-blocks for /dev/scd0. It will be in the tens of millions, I should think.

3. Divide the number of blocks by 2, this will give you the number of sectors.
*3.5 Unmount the DVD again (just to be thorough) --EDITED* 
4. Try the following: ```
dd if=/dev/scd0 of=filetest3.iso bs=2048 count=type_number_of_sectors_here
```
5. Assuming that step 4. hasn't fixed it, try this next: ```
readcd dev=/dev/scd0 f=filetest3.iso bs=2048 count=type_number_of_sectors_here
```

If that doesn't get it working, I'm running out of suggestions. We've got pretty low-level by this point and I'd suggest getting an iso from somewhere else or grabbing another drive. Do you dual boot and does it work from Windows if so?

**EDIT:** You are sure that the disc itself works okay, yes? Have you tried this command with a different DVD, say a movie or somesuch?

---

### Post by derrick81787 on 2008-08-05
> **rules said:**
> This is what happens with those 3 commands ...

rafiq@rafiq-laptop:~$ dd if=/dev/scd0 of=filetest1.iso
dd: reading `/dev/scd0': Input/output error
224+0 records in
224+0 records out
114688 bytes (115 kB) copied, 2.76731 s, 41.4 kB/s
rafiq@rafiq-laptop:~$ cat /dev/scd0 > /dev/null
cat: /dev/scd0: Input/output error
rafiq@rafiq-laptop:~$ dd if=/dev/scd0 of=filetest2.iso
dd: reading `/dev/scd0': Input/output error
40+0 records in
40+0 records out
20480 bytes (20 kB) copied, 0.971958 s, 21.1 kB/s
rafiq@rafiq-laptop:~$ 

I also just tried Brasero which seemed to work fine till it got to 43% and then it just froze.

I'm pretty sure you need to use sudo.  Try this instead:

```
sudo dd if=/dev/scd0 of=filetest3.iso
```

That will probably avoid the input/output error.  Let me know for sure, though.

- Derrick

---

### Post by H4rm0ny on 2008-08-05
> **derrick81787 said:**
> I'm pretty sure you need to use sudo.  Try this instead:

```
sudo dd if=/dev/scd0 of=filetest3.iso
```

That will probably avoid the input/output error.  Let me know for sure, though.

- Derrick

I'd be very surprised if running it as root made a difference.

---

### Post by rules on 2008-08-05
Hehe no go ... the last couple of dd commands do create iso's, but none bigger than 3-400Mb and sudo doesn't make any difference.

I think this is a lost cause with a semi dead cd/dvd drive. I'm going to see if I can't make an iso from the wife's mac rather.

Thanks for all the help, at least I learned quite a lot from all of this :)

---

### Post by ingeva on 2008-08-16
> **rules said:**
> Hehe no go ... the last couple of dd commands do create iso's, but none bigger than 3-400Mb and sudo doesn't make any difference.

I think this is a lost cause with a semi dead cd/dvd drive. I'm going to see if I can't make an iso from the wife's mac rather.

Thanks for all the help, at least I learned quite a lot from all of this :)

In my computer the dd command produces an empty file (0 bytes.
Tried everything. Right-clicking the desktop icon seems to be the only thing that worked, creating a CD image of the right size. Took a very long time though.

I tested using an audio CD, and I did NOT test the CD image because it was overwritten by another attempt to dd.

I also learned a lot by reading this thread. For instance, I have now installed isomaster. :)

---

