---
title: "Very slow writing of DVD-RAM"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by timetunnel on 2005-07-22
Hi guys,
I switched from SUSE to ubuntu about two months ago and am very happy with it. Now I've got a brand new LG GSA-4163B DVD-Burner (supports CD/CD-R/CD-RW/DVD-/+/R/RW and DVD-RAM) which has been detected without problems. All the CD/DVD-/+ stuff works, except for writing to DVD-RAM, which is very slow.

I want to use the DVD-RAMs like a file system and managed to make it work with this line in fstab

/dev/hdc  /media/cdrom1 udf,iso9660 noatime,rw,sync,user,noauto  0  0

and by creating a UDF file system on it:

mkudffs --spartable=2 --media-type=dvdram /dev/hdc 

Writing works but the speed is bad:

1 file of 20.9MB: time cp ~/test.zip /media/cdrom1

real    2m37.811s
user    0m0.029s
sys     0m1.793s

That's about 136KB/s only. Using much bigger or much smaller files doesn't change the speed significantly. Same thing when I delete these files on the DVD-RAM.
I already tried something I found in the usenet: "sudo sysctl -w vm.dirty_ratio=0", but no change at all. 

Anyone any idea?
 
Many thanks
Jens

---

### Post by rikai on 2005-07-22
[QUOTE=timetunnel]Hi guys,
I switched from SUSE to ubuntu about two months ago and am very happy with it. Now I've got a brand new LG GSA-4163B DVD-Burner (supports CD/CD-R/CD-RW/DVD-/+/R/RW and DVD-RAM) which has been detected without problems. All the CD/DVD-/+ stuff works, except for writing to DVD-RAM, which is very slow.

I want to use the DVD-RAMs like a file system and managed to make it work with this line in fstab

/dev/hdc  /media/cdrom1 udf,iso9660 noatime,rw,sync,user,noauto  0  0

and by creating a UDF file system on it:

mkudffs --spartable=2 --media-type=dvdram /dev/hdc 

Writing works but the speed is bad:

1 file of 20.9MB: time cp ~/test.zip /media/cdrom1

real    2m37.811s
user    0m0.029s
sys     0m1.793s

That's about 136KB/s only. Using much bigger or much smaller files doesn't change the speed significantly. Same thing when I delete these files on the DVD-RAM.
I already tried something I found in the usenet: "sudo sysctl -w vm.dirty_ratio=0", but no change at all. 

Anyone any idea?
 
Many thanks
Jens[/QUOTE]
 according to [http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=12429](http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=12429) the burner can only burn DVD-RAM at 5x max, AFTER you've got firmware version 2.2 or newer, 3x if you dont, so i'm not suprised the burining is slow... with 4x, i believe that a full dvd burn takes somewhere close to 20 minutes, or maybe it was 40... cant remember.

---

### Post by timetunnel on 2005-07-22
[QUOTE=rikai]according to [http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=12429](http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=12429) the burner can only burn DVD-RAM at 5x max, AFTER you've got firmware version 2.2 or newer, 3x if you dont, so i'm not suprised the burining is slow... with 4x, i believe that a full dvd burn takes somewhere close to 20 minutes, or maybe it was 40... cant remember.[/QUOTE]
Thanks for your reply. I think you got the figures of my posting wrong. I wrote that the speed is about 136 KB (!) per second, so that 20 MB (!) takes 2.5 minutes to write. That's not even 1x. A whole DVD-RAM would then take about 9 hours to write (not burn, I want to use it like it file system and write the data with rsync).

Jens

---

### Post by timetunnel on 2005-07-22
Additional info: burning a DVD-RAM with K3b is lightning fast (1 file of 80MB in less than 30 sec. from start to end of the burning process, K3b says writing speed was 10x !). So it's not a problem of the drive or it's firmware, is it?

---

### Post by timetunnel on 2005-07-23
Additonal information: 
- updating to the latest firmware didn't change a thing 
- the speed when burning with K3b or GnomeBakeer is about the same, it starts fast for the first 100MB (probably because of internal buffering), but then it goes down to 500KB/sec and less (with DVD-/+R/RW it's much faster).

So again, is anyone able to help me? 

Jens

---

### Post by pato101 on 2005-08-18
Same happens to me. Same happens to me also with usb-sticks whenever using filesystems other than vfat or reiserfs.

Using reiserfs for the DVD-RAM filesystem solves the problem but has the problem that using a journal on a DVD-RAM is a bad idea (same place of the DVD-RAM being rewritten constantly may damage the disk at mid-term). You could use the "nolog" option at the mount time.

GOOD NEWS: using the device asyncronously (remove the "sync" option) recovers the lost performance. That is not an issue for a DVD-RAM since requires umounting prior to disk extraction but is a point to be taken into account for USB-sticks.

I've filled a bug with that info, see [http://bugzilla.ubuntu.com/show_bug.cgi?id=13740](http://bugzilla.ubuntu.com/show_bug.cgi?id=13740)

---

### Post by timetunnel on 2005-08-19
Thanks for your reply. Actually, like you said as well, async doesn't make sense for DVD-RAM. There's no advantage in getting more speed when mounted async, because you have to use a "sync" (or something that calls "sync" implicitly) in order to really write the data to the disc - and THAT is veeery slow again then. 

I read somewhere that one's generally advised against using any other than UDF on DVD-RAM, otherwise you'll extremely shorten the lifetime of the discs.

I'm hoping for the next Unbuntu/kernel to have that fixed. With DVD-RAM being widely spread in Asia and getting more and more attention in Europe I can't imagine that there's no interest in fixing this problem.

Jens

---

### Post by pato101 on 2005-08-22
> There's no advantage in getting more speed when mounted async, because you have to use a "sync" (or something that calls "sync" implicitly) in order to really write the data to the disc - and THAT is veeery slow again then.

Not really! the **weird** point is that just by mounting when async it behaves much quicker. If you compute the time of umounting you will see that it is far smaller than the time to write the files in sync mode. [B]The bug that slows thing down seems not to apply when async.
[/B]
And as for the filesystem, don't care if you are going to use the DVD-RAM only between linux boxes... but reiserfs is not the best choice unless you disable the journal (which could easily reach the 100000 writes so you might damage the disc)

---

### Post by timetunnel on 2005-08-22
[QUOTE=pato101]Not really! the **weird** point is that just by mounting when async it behaves much quicker. If you compute the time of umounting you will see that it is far smaller than the time to write the files in sync mode. [B]The bug that slows thing down seems not to apply when async.
[/B][/QUOTE]
Ah! I didn't know that. I didn't tested that actually, just read it somewhere and believed it. Proofs again that it's always better to check something yourself rather than reposting that unchecked. 
Thanks for the information.

Jens

---

### Post by timetunnel on 2005-10-01
For all those who want to know: I just checked the described problem with the latest Breezy 5.10 live CD and: it works fine there! Very fast. Looking forward to the upcoming release. Love it. :D 
Jens

---

### Post by pato101 on 2005-10-03
[QUOTE=timetunnel]For all those who want to know: I just checked the described problem with the latest Breezy 5.10 live CD and: it works fine there! Very fast. Looking forward to the upcoming release. Love it. :D 
Jens[/QUOTE]
wow. Willing to update. I guess that it is the 2.6.12 kernel:razz: :razz:

---

### Post by timetunnel on 2005-10-13
After my last post about the test with the live CD, I did the upgrade to Breezy now, fresh install. And what happens: it's painlfully slow again!!!  Argh! :confused: 

Luckily the solution is pretty simple :D , like already mentioned in this thread: DON'T put a "sync" in the mount options for the dvd drive:
/dev/hdc    /media/cdrom0   udf,iso9660 noatime,rw,user,noauto  0    0

This test 
time cp test.zip /media/cdrom/tests | sync
copies and syncs one file of 24MB size.

At first with "sync" in fstab:

real    2m27.588s
user    0m0.037s
sys     0m1.911s

Bad. Like before with Hoary.
Now the same file remounted without the "sync" option in fstab:

real    0m12.693s
user    0m0.004s
sys     0m0.141s

This is definitely better than the times I saw on Hoary when I ran that test there.  That's ok for me.

But it still doesn't work with "sync" in the mount option. No idea what happens if you want to copy 2 GB of data without sync... hmm.

---

### Post by pato101 on 2005-10-24
Bad news indeed. I wish the problem was really solved.

Same has happened with my usb-stick: with the LiveCD it was fast no matter which filesystem I format the thing. After breezy upgrade, I have the same problems that I had at hoary :-(

Have you tried a fresh install? I have no time to do one right now, to see if I have the same problem there...

---

### Post by timetunnel on 2005-10-24
Yes, it was a clean install.  

You wrote about your slow USB stick. The USB-stick I use has been running really fast, even on Hoary.  I never did any setup for it, just plugged it in, waited for it to be mounted automatically, and started copying. It's as fast as it is supposed to be.

Jens

---

### Post by pato101 on 2005-10-25
Yes, USB-stick is fast until you format it with ext2 or udf. Then it is pain slow except at liveCD. Removing sync speed things up, if I recall correctly, so the problem is parallell to DVD-RAM thing....

---

