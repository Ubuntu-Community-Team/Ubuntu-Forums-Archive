---
title: "Unable to mount CD/DVD"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by ShaqArif on 2007-04-16
Hi.

hope somebody can help me, cos this problem is driving me crazy!

On my PC, with Edgy Eft installed, I have a DVD+-RW and a DVD ROM.  They were daisy chained on one IDE cable with the DVDRW set to master and the DVDROM set to slave.  The DVDROM was working fine, but the DVDRW wasn't mounting.  After having trawled through the boards, I got some hints that Ubutu has issues with two DVDs on one IDE cable.  I've removed the working DVDROM and just have the DVDRW on the cable now.  my /etc/fstab contains this:

```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I know that the device is /dev/hdc, as I see that under Device manager.  However, when I try to mount it, I get the following:

```
sudo mount /dev/hdc /media/cdrom0
mount: No medium found
```

In all other respects, Ubuntu seems to recognize the drive for what it is, eg:

> ~$ dmesg | grep DVD
[17179574.632000] hdc: PIONEER DVD-RW DVR-112D, ATAPI CD/DVD-ROM drive
[17179575.048000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)

I've tried several disks, but I get the same error with all of them - I've tried the same disks in the DVDROM when that was connected and they worked fine on that...

Any advice/suggestions would be extremely gratefully received - I have a nagging  feeling that the drive is bust, despite the fact that it is only a one month old Pioneer.  Ironically, my naff. old DVDROM, complete with dodgy window mod stiill works fine... :(

---

### Post by volksolwagen57 on 2007-04-17
have you configured both of you drives in a master/slave relationship?

---

### Post by ZaphodNE on 2007-04-17
I'm having a similar issue.  DVD/CD combo drive simply will not work.  I have a clean install of Edgy as of 3/23/2007  where the drive used to work just fine.  Now it's dead. 

I admit stupidity when it comes to fstab and such, but I really do not understand why this connection just disappeared.

Can someone educate me on how to get this drive recognized again???

At this point I'm blaming it on XGL and Beryl, but that's just a WAG.  Please help.

---

### Post by tommcd on 2007-04-18
> **ShaqArif said:**
> Hi.

hope somebody can help me, cos this problem is driving me crazy!

On my PC, with Edgy Eft installed, I have a DVD+-RW and a DVD ROM.  They were daisy chained on one IDE cable with the DVDRW set to master and the DVDROM set to slave.  The DVDROM was working fine, but the DVDRW wasn't mounting.  After having trawled through the boards, I got some hints that Ubutu has issues with two DVDs on one IDE cable.  I've removed the working DVDROM and just have the DVDRW on the cable now.  my /etc/fstab contains this:

```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I know that the device is /dev/hdc, as I see that under Device manager.  However, when I try to mount it, I get the following:

```
sudo mount /dev/hdc /media/cdrom0
mount: No medium found
```

In all other respects, Ubuntu seems to recognize the drive for what it is, eg:



I've tried several disks, but I get the same error with all of them - I've tried the same disks in the DVDROM when that was connected and they worked fine on that...

Any advice/suggestions would be extremely gratefully received - I have a nagging  feeling that the drive is bust, despite the fact that it is only a one month old Pioneer.  Ironically, my naff. old DVDROM, complete with dodgy window mod stiill works fine... :(


Since you removed one drive, set the jumper on the dvdrw to master, don't use cable select. I don't know if this will help, but it is a good practice with IDE drives in any case.  You could also try a different IDE cable if you have one.
Do you dual boot, and if so does the dvdrw work ok in windows?

---

### Post by ShaqArif on 2007-04-18
thanks volksolwagen57, tommcd for the replies.

Originally, I had the DVDRW set as Master and the DVDROM set as slave (using the jumpers).  In this case, the DVDROM was working, but the DVDRW was not.  I then removed the DVDROM from the system entirely, so I just had the DVDRW set as master.

When I insert a CD/DVD into the drive, the led comes on, but only for about a second or so, I'm sure it's usually on for longer than that.

I don't have dual boot since my primary hard drive went a bit funny whilst repartitioning in partion magic.  One of the reasons I'd like to get my DVD writer back up and running is so that I can back up my system before I start playing with this hard drive...

I'm expecting a delivery today for all the bits to build a new a new for a relative (installing only ubuntu on it... ; four more souls to experience the wonders of Ubuntu) . This delivery includes a pioneer DVDRW, which is a similar model to mine - it's the DVR112-BK, mine is the DVR112-DBK. I'll try this in my system which should tell me whether I need to get a new DVD writer...

---

### Post by ShaqArif on 2007-04-25
OK, having established that my Pioneer DVD works fine, I'm still no closer to the solution.

Looking back at my original post, I note that the dmesg output shows both the Pioneer and the Sony to be 'hdc' - this is obviously wrong.  I've fixed this so that the Reader is slave and appears as /dev/hdc and the Writer is Master, appearing as /dev/hdd.

Have no problem mounting the Reader under this config, and it plays DVDs through Totem fine.  However, when I put the same DVD into the Writer, and I try to mount, I get the same 'Media not found' error as originally reported.

In my /etc/fstab I have:

/dev/hdc        /media/cdrom0   auto     0       0
/dev/hdd        /media/cdrom1   auto     0       0

and I'm trying to mount using:

sudo mount /dev/hdc /media/cdrom1

Any suggestions would be really welcome - I would like to get the writer working so that I can burn my Edgy ISO and move on up!

---

### Post by hipotermia on 2007-04-25
hey i'm getting a similar problem.

i'm using feisty by upgrade and the dvd wont mount.

i have 2 hd's partionated in 3 drives, and a cd-rw, dvd-rom drive's.

fstab:

# Entry for /dev/hda3 :
UUID=450b0ac3-5da3-4901-8290-81f3954767d6 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=A04816094815DEBA /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda5 :
UUID=10DDC03573FE1009 /media/hda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hdc1 :
UUID=C074914F74914954 /media/hdc1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda6 :
UUID=27985afc-b3b0-4f69-9d82-681dfa399238 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/cdrom /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

:confused:

---

### Post by tommcd on 2007-04-26
ShaqArif,
Most peoples entries for their CD/DVD drives in fstab are similar to hipotermias in the post above, and as your's was originally. Here is mine:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I think you need that udf,iso9660 part. Try it. Back up your fstab first though, so you can restore it easily if it doesn't help. Also, make sure you have the directories /media/cdrom0 and /media/cdrom1.
I see that you had the udf,iso9660 part in your first post, so I don't know if it will help, but give it a try.

---

