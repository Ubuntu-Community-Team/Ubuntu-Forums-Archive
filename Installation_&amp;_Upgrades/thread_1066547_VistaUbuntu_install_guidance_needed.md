---
title: "Vista/Ubuntu install guidance needed"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by GrahamM on 2009-02-11
I have Ubuntu installed on my home desktop, but at present I am on an extended trip and would like to install it (8.10) on my laptop. I don't have a very fast internet connection, so I picked up a magazine that has v8.10 on a DVD. 

My laptop has a 160Gb drive. It is a Compaq Presario V6000. Windows indicates there are two partitions - Drives C and D.

I at first thought I would install to a USB thumb drive, but Ubuntu indicates that 4Gb is too small. 

I used the Vista shrink utility to open up a space of 39Gb on the drive. Because I have no means of backing up, I want to be very careful. I started the install, but am not sure what it is doing. I tried the guided install with install to largest contiguous space. The messages are not exactly clear. It says something about partitions 5 and 6 (to be used for ext3 and swap) being formatted and possibly destroying data. But how did we get to 5 & 6? There were just the two Vista drives to start with plus the 3oGb of unallocated, unformatted space.  Is the installer using part of the Vista partitions?

If I use manual install, could someone explain exactly what I should enter in the boxes that come up? Or is there a guide somewhere? I was not certain what to do when I tried, so aborted.

The DVD does not seem to have Wubi - If I am concerned about messing up my drive would that be a better option?

I have tried running from Live CD, but cannot get wifi to work.

---

### Post by jbrown96 on 2009-02-11
I haven't used the Vista tool, but from what I understand, the tool will take a single NTFS partition and make it smaller. the remaining section should be an unpartitioned space. 

You don't want to use the guided partitioning. choose manual. It will then list your partitions. Your D drive is probably some sort of recovery partition and probably has fat32 as its file system. It would be nice to keep this, but your Vista partition is what you need to watch out for. Don't format/delete anything of type NTFS. You should probably break the unpartitioned space into two sections: one for swap (if you plan to hibernate/suspend, then 1.2x your RAM size) and the rest for /

About the 5 & 6 part. The Vista tool may not have known what to do with the free space and created logical partitions instead of primary partitions. Since you can have only 4 primary partitions, logical partitions start at 5 and go up.

---

### Post by Mark Phelps on 2009-02-11
Just so you know -- anything that does not work using the LiveCD is very likely to also NOT work after installation.  So, unless you luck out and Wireless DOES work, be prepared to spend a lot of time in these forums figuring out how to get wireless working.

Also, before you install ANYTHING, make sure you have a Vista recovery CD available -- just in case you mess up the MBR or the Vista partition in some way.  Without that, should your Vista partition become corrupted in any way, you will be unable to correct it and will permanently lose the use of it.

---

### Post by GrahamM on 2009-02-11
> **Mark Phelps said:**
> Just so you know -- anything that does not work using the LiveCD is very likely to also NOT work after installation.  So, unless you luck out and Wireless DOES work, be prepared to spend a lot of time in these forums figuring out how to get wireless working.

Also, before you install ANYTHING, make sure you have a Vista recovery CD available -- just in case you mess up the MBR or the Vista partition in some way.  Without that, should your Vista partition become corrupted in any way, you will be unable to correct it and will permanently lose the use of it.


Now you have me worried! My recovery CD is 1000 miles away.

I could  install to a USB drive. The 4Gb one I have is apparently too small, but I could buy a larger one. But even with that, I guess the MBR could be messed up?

This is a relatively late model Compaq laptop. But, loading the liveCd does not show up any wifi connections although there is one here (using it now!). What would be missing if presence of wifi is not detected?

Finally - would downloading Wubi and going that route be a safer choice?

BTW - Thanks for the input!

---

### Post by avtolle on 2009-02-11
Take a look on the DVD; Wubi may be there already, as it is now part of the official CD iso. If it is, then you could install from the DVD solely, I think. Safer? Well, I've not had any problems with my Wubi install of 8.10, but YMMV. As you have already shrunk the Vista partition, and as Wubi installs a virtual disk within Vista (in your case), how much free space do you have for the Wubi install? I went with 15 gb, although 10gb might be sufficient. I guess the Wubi install is "safer" in that you aren't dealing with partitions. 

Good luck with however you go; the wireless issues, once installed with Wubi or otherwise, will be the same. Do you know what your wireless card is? If an Atheros as was my Compaq, there is a fairly simple "fix" to use (it is in the release notes for 8.10) to get the driver installed, which I used and it worked for me. Again, good luck.

---

### Post by avtolle on 2009-02-11
Oops; misread your earlier post. Before doing an install with Wubi, defrag the HDD at least twice before starting the installation; many problems I've seen on the Wubi forum have been related to disk fragmentation which was not cleaned up before using Wubi to install.

---

### Post by GrahamM on 2009-02-11
> **avtolle said:**
> As you have already shrunk the Vista partition, and as Wubi installs a virtual disk within Vista (in your case), how much free space do you have for the Wubi install? I went with 15 gb, although 10gb might be sufficient. I guess the Wubi install is "safer" in that you aren't dealing with partitions. 

If an Atheros as was my Compaq, there is a fairly simple "fix" to use (it is in the release notes for 8.10) to get the driver installed, which I used and it worked for me. Again, good luck.

The drive has lot's of space and I can unshrink it if I use Wubi. I would defrag as you suggested TWICE :)

Device manager reports a Broadcom 802.11 b/g WLAN. 

I could not find wubi on the DVD - I got it out of a magazine [www.linuxpro.com](www.linuxpro.com) . I went to site and downloaded it.

I will probably go the wubi way.

Thanks for input.

---

### Post by GrahamM on 2009-02-12
> **GrahamM said:**
> The drive has lot's of space and I can unshrink it if I use Wubi. I would defrag as you suggested TWICE :)

Device manager reports a Broadcom 802.11 b/g WLAN. 

I could not find wubi on the DVD - I got it out of a magazine [www.linuxpro.com](www.linuxpro.com) . I went to site and downloaded it.

I will probably go the wubi way.

Thanks for input.

Well, I tried Wubi - It first checked out the DVD and then seemed to commence the install. Then it just crashed out and I got the usual MS box asking if I wanted to send them the crash report.

Tried it again, and now Wubi goes and tries to get Ubuntu from an on-line mirror site. At the 11Kb/s it quoted, this would have taken 16 hours. Could not get Wubi to try the DVD again after I had cleaned it.

Isn't this fun!  I do have another unused 8.10 DVD from a second magazine. Might try that, but will need to figure out how to get it to use the DVD.

I would just run from the live DVD, but is there any way to get the Wifi working if I only have web access through windows (for downloading drivers etc)

---

### Post by GrahamM on 2009-02-13
> **GrahamM said:**
> Well, I tried Wubi - It first checked out the DVD and then seemed to commence the install. Then it just crashed out and I got the usual MS box asking if I wanted to send them the crash report.

Tried it again, and now Wubi goes and tries to get Ubuntu from an on-line mirror site. At the 11Kb/s it quoted, this would have taken 16 hours. Could not get Wubi to try the DVD again after I had cleaned it.

Isn't this fun!  I do have another unused 8.10 DVD from a second magazine. Might try that, but will need to figure out how to get it to use the DVD.

I would just run from the live DVD, but is there any way to get the Wifi working if I only have web access through windows (for downloading drivers etc)

After reading the many posts where people are having problems with installing Ubuntu on their laptops, I think I have decided to pass for the moment.

I have Ubuntu on my Desktop at home and it is working OK. But while on the road, I can't see risking messing up my laptop when most of my resources are 1000+ miles away!

Thanks to those who tried to help.

---

