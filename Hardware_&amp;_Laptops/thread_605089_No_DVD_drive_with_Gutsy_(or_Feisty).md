---
title: "No DVD drive with Gutsy (or Feisty)"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by thejimster on 2007-11-06
Hi there everyone.

Basically I can't get my DVD drive to work with Kubuntu.  I dual boot with Windows and it works fine there.  It didn't work with Feisty, but I thought I'd hang in until Gutsy came along hoping it would sort itself out - 'fraid not.  I _really_ want to ditch windows, but the DVD drive problem is holding me back.

I've read around this problem, and think it might be related to problems with ata_piix.  I've got a SATA HD and the chipset is "82801GBM/GHM (ICH7 Family)".

my fstab contains the line:

```
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
```

If I try to mount manually I get:

```
mount: special device /dev/scd0 does not exist
```

There doesn't seem to be any obvious candidate to use instead of /dev/scd0.

I'm sure that I've not posted enough info here... I'm fairly new to linux (but experienced with computers) so please tell me what info is required to help narrow this down.

If anyone can help me sort this out I'd be eternally grateful.

Thanks in advance.

---

### Post by ofb on 2007-11-06
I spent the weekend going through threads and bug reports. Right now I'm thinking the various IDE device troubles will be sorted once patches come through, and there's not much we can do in the meanwhile.

Funny how your DVD didn't work in 7.04 though. Might be more than one trouble here.

---

### Post by thejimster on 2007-11-07
Thanks for your reply!

I've spent quite a bit of time search through various post related to CD/DVD drives not mounting properly and many of them talk about problems with ata_piix (Something like it incorrectly taking control of the DVD drive when it shouldn't - please correct me if I'm talking out of my @ss).

Suggested fixes often talk about using other modules instead of ata_piix (can't remember off hand, names containing various combinations of piix and ide and generic...).  I've tried a couple but frankly have never manage to stop ata_piix from loading (tried blacklisting it etc.), and in any case I'm concerned that not loading ata_piix would stop my HD from working...

Basically I'm clueless :-)

Cheers.

---

### Post by thejimster on 2007-11-07
Bump - sorry

---

### Post by trak87 on 2007-11-07
Maybe try changing /dev/scd0 to /dev/hdc or /dev/hdd

Something like this:

```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by thejimster on 2007-11-07
Hi trak87,

I seem to remember from previous posts I've read that drive names have swapped between scsi/ide (hda to sda) etc.  So I've taken a look through the /dev directory and nothing looks close to being right for my dvd.  There's only a few block devices available ram0 thru ram15 and sda thru sda4 (which is my hard drive).  That's the lot.

It would seem that the system just hasn't picked up my drive, rather than it just not being mounted properly...

Thanks.

---

### Post by ofb on 2007-11-07
Yeah, I didn't give you much detail because I'd hit the point where I'd heard more than I know. While there's a module swap method out there that helps some people detect missing harddrives (essentially blacklist ata_piix & co, and load generic ide modules), I found that just shifted me into the problem-group of burner being able to read but not burn. By then I'd found lots of threads with a variety of IDE troubles (how about hda and hdb being randomly assigned to two drives on each boot?) and decided this was something deeper than a quick fix - I'd be much better off waiting for patches to come through than making a frankenstein of my system.

What's frustrating of course is no one has been able to make a good head&tail summary of this one yet, so there isn't a nice link to send you & me & all the new "my harddrive/DVD won't work" posters to yet.

You're welcome to flail at it of course. ;) I just thought I'd give you the benefit of my two cents after a long weekend of no luck here.

At least one patch has already been applied to the .23 kernel, and our .22 will follow soon enough.

---

### Post by iamclueless on 2007-12-23
is there still no straight forward fix to this?

i can play CDs and rip them.  i just cant get them to mount so i cant access data on the the drives

---

