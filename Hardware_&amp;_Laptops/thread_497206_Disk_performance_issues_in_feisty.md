---
title: "Disk performance issues in feisty"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by charles_elwood on 2007-07-10
Apologies if this is a duplicate -- I cant find one but...

charles@smaug:~$ sudo hdparm -Tt /dev/sd?

```
/dev/sda:
 Timing cached reads:   526 MB in  2.01 seconds = 262.33 MB/sec
Timing buffered disk reads:   10 MB in  3.20 seconds =   3.13 MB/sec

/dev/sdb:
 Timing cached reads:   520 MB in  2.00 seconds = 259.58 MB/sec
 Timing buffered disk reads:   10 MB in  3.20 seconds =   3.13 MB/sec

/dev/sdc:
 Timing cached reads:   512 MB in  2.01 seconds = 255.32 MB/sec
 Timing buffered disk reads:   10 MB in  3.18 seconds =   3.14 MB/sec

```

With Ubuntu <7.04 and everything else the box in question has run, bufferred disk reads have been >40MB/s for all 3 disks.

sda is on the builtin SIS 5513 PATA controller, sdb and sdc are on an ITE8212 PATA controller. Said hardware has been happy running debian/gentoo/redhat/dapper/edgy since about 2003 IIRC

hdparm -I suggests all drives are running udma5 as they should be

It seems like an issue with the new ATA layer based PATA drivers. Anyone have similar problems or ideas about how to track this issue down? The box in question is my mythtv box so this is quite literally a showstopper. ](*,)

TIA

---

### Post by fredj on 2007-07-10
Yes this is slow but obviously its only a problem on some PCs so you should post the make and
model number of your PC or laptop and do a forum search for posts about the same model to see
if anyone else has solved the problem.

---

### Post by charles_elwood on 2007-07-11
Hmm. Make and model number of my PC? That *might* be difficult given it's a self build.

I had a look at the kernel config and it looks like only the Experimental PATA drivers are included for the ITE8212, so I'm going to take the gentooists approach and build a kernel with just the old ATA drivers. 

I think I've stumbled into this SATA issue
[http://ubuntuforums.org/showthread.php?t=447474](http://ubuntuforums.org/showthread.php?t=447474)
[https://bugs.launchpad.net/ubuntu/+bug/11973](https://bugs.launchpad.net/ubuntu/+bug/11973)

This at least brings me to a much shorter question, how can one fore the use of the old ATA drivers without having to kernel prod? I *know* I'm going to run into this issue on a bunch of machines that are being a little slow, and it's likely to halt migrations from the more effort intensive distros.

---

### Post by charles_elwood on 2007-07-11
Massive improvements in disk speed using the old ATA drivers. >60Mb/s *grin* 
System is actually useable again.

---

### Post by KubuntuKilledMe on 2007-07-13
Please, what did you do to fix it?

---

### Post by b.q.wemer on 2007-08-13
Hi,

I'm dealing with the same problem. Tried to fix it the whole day till I found that:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636)

This means that there will be no solution for feisty. If the problem will be fixed in gutsy isn't clear, too. 

For this reason I tried to recompile the kernel but I choose the wrong driver so the system stuck when booting the harddisk.

Can please anyone tell me, which drivers exactly are needed to swich back to old ATA drivers? Are there further tweaks necessary?

Thanks and greetz!

---

### Post by b.q.wemer on 2007-08-15
Hi,

sorry for bumping, but this problem really sucks. :(
```
oli@WG4:~$ sudo hdparm -t /dev/scd0
Password or swipe finger: 

/dev/scd0:
 Timing buffered disk reads:    2 MB in  4.47 seconds = 457.75 kB/sec 
```

These poor values make any audio- or videostreaming impossible and lowers performance of realtime recording. 

Doesn't anyone has a solution or at least a workaround?

Many thanks in advance and greetz!

---

### Post by burningstar4 on 2007-08-16
I also had this problem; recompiled the kernel, and the system shows great improvement.

What I did is:
Disabled Device Drivers --> Serial ATA (prod) ... ---> ATA device support
Disabled Device Drivers --> ATA/ATAPI... --> SCSI Emulation Support
Enabled Device Drivers --> ATA/ATAPI... --> Include IDE/ATA2 DISK Support
Enabled Device Drivers --> ATA/ATAPI... --> ((Your IDE controller chipset))
Enabled File Systems --> ((Whatever filesystem(s) you use))

Then used make-kpkg to make .deb files for the kernel image and headers.  dpkg -i for both of those, and then a reboot, now my hard disks show up as /dev/hdX instead of /dev/sdX, and hdparm -tT /dev/hdX gives much better speeds.  Hope this helps anyone, I'm new to kernel tinkering myself and this was my first experience with it.

---

### Post by b.q.wemer on 2007-08-16
Hi,

thanks for reply. I'll try as soon as possible!

mfG

---

### Post by DooDle on 2007-09-02
> **burningstar4 said:**
> I also had this problem; recompiled the kernel, and the system shows great improvement.

What I did is:
[B]Disabled Device Drivers --> Serial ATA (prod) ... ---> ATA device support
Disabled Device Drivers --> ATA/ATAPI... --> SCSI Emulation Support
Enabled Device Drivers --> ATA/ATAPI... --> Include IDE/ATA2 DISK Support
Enabled Device Drivers --> ATA/ATAPI... --> ((Your IDE controller chipset))
Enabled File Systems --> ((Whatever filesystem(s) you use))[/B]

Then used make-kpkg to make .deb files for the kernel image and headers.  dpkg -i for both of those, and then a reboot, now my hard disks show up as /dev/hdX instead of /dev/sdX, and hdparm -tT /dev/hdX gives much better speeds.  Hope this helps anyone, I'm new to kernel tinkering myself and this was my first experience with it.

So, I also have a PATA controller, and my HD shown as /dev/sda, with slow transfers and everything else like ohter people who want to use hdparm.
I'd like to know how did you do what I bolded in the quote!!! (Disabled and enbled drivers!!!)

Thanks in advance! ;)

---

### Post by b.q.wemer on 2007-09-02
Hi,

recompiling the kernel as recommended by burningstar4 didn't work for me. The system stuck, when booting the HD. 

But the lack of functionality is fixed in the newer source code of the Vanilla-Kernel (2.6.23-rc3-git10 in my case).

sudo hdparm -t /dev/scd0 now gives:

Timing buffered disk reads:   14 MB in  3.22 seconds =   4.34 MB/sec   :)

greetz

---

