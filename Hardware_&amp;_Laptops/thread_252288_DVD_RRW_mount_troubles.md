---
title: "DVD R/RW mount troubles"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by Valencik on 2006-09-06
I just bought a Samsung DVD writer.
Model name is: Super Multi - SH-S162A(L)
I am using Ubuntu 6.06.1 LTS (not that it should matter but i have updated straight from 5.04)

Problem: Cannot recognize any disc, whether it be CD or DVD.

I am quite positive that I have manually installed the drive correctly, i mean there are only so many possible wire to hook up. I have it set as the master and an old MSI CD burner set as slave.
If i go into Places > Computer, I can see both my CD and DVD drive. However, if I put a DVD in the DVD drive nothing happens. If I try and manually mount the drive I get this:
  "mount: no medium found"

Through google i found [http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt) and first followed their instructions.

> Playing DVDs
------------
The Ubuntu Wiki discusses restricted formats [4], which include CSS and
DVD playback.  To add DVD playback capability to Ubuntu, use your favorite
text editor and add the following line to your /etc/apt/sources.list file.

	deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Then sync your package index and grab the infamous DeCSS.

	$ sudo apt-get update
	$ sudo apt-get install libdvdcss2

Add a dvd link and enjoy DVDs with MPlayer and Ubuntu.

	$ sudo ln -s /media/cdrom0 /dev/dvd

When that didn't work (no errors just didn't work) I went here: [http://ubuntuguide.org/](http://ubuntuguide.org/) and followed it's instructions, no luck.

Any help? I really would like to not have to return this just because I can't figure out how to work it. Please help.

---

### Post by Ciego on 2006-10-02
Have you resolved this problem yet?  I seem to be having the same issue with my CD-RW drive.  Any advice?

---

### Post by mgmiller on 2006-10-02
I have 2 optical drives, a DVD burner, a Samsung which identifies as a TSSTCorp TS-H552U and an Asus DVD-rom E-616P3.  They are each hooked up as master on their own cables.  I do not have a drive slaved to either one.  They both work properly.
Make sure the jumpers are not set to cable select, but you are using master/slave.  Also, then try disconnecting the slave drive and only have the burner hooked up as master.  If it works, then you may want to try them on seperate cables.  My suggestion, is if you need one of your IDE cables for your hard drive, make that master and put the DVD rom drive with it as slave.  Hopefully, your DVD rom is ATA 66, 100 or 133, so it won't slow down your hard drive.  This is why I selected the Asus DVD rom.  It's just as fast as any PATA hard drive and won't slow it down.  Although, in my case, I have since upgraded to a SATA hard drive, so this no longer matters.

---

### Post by Ciego on 2006-10-04
I tried only connecting the CDRW with the jumper in the master position with no luck.  

Please check out this thread that I made on the subject.

[http://www.ubuntuforums.org/showthread.php?p=1581875#post1581875](http://www.ubuntuforums.org/showthread.php?p=1581875#post1581875)

Any advice is greatly appreciated.

---

### Post by wkulecz on 2006-10-05
Have you tried setting bot drives to cable select?  I've in the past ran into motherboards (usually Dell if I remember correctly) that would only work with drives set to cable select.

As you said, there are only so many ways to hook things up, just make sure you've really tried them all.

--wally.

---

