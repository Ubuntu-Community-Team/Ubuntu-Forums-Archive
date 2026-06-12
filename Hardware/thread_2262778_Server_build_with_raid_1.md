---
title: "Server build with raid 1"
date: 2015-01-27
forum: Hardware
---

### Post by vaudevillian on 2015-01-27
I'm looking to build a private server to host my files/music/movies

The goal

Run ubuntu server 14.10LTS

Hard drive setup

run os on mobo sata connectors (on SSD most likely)
run 2 2tb WD intellipower drives on a card that supports raid 1

I would prefer not to run this in fakeraid.

I want to use a mobo that has a Intel J1900 attached to it. Low power :) , I was looking at boards from Asrock.

Now for the raid card, anyone have any clue as what one will be the least problematic to run with Ubuntu server 14.10 lts

---

### Post by MartyBuntu on 2015-01-27
Why would you want RAID for a simple home file server?

The second disk would be of better use as a backup drive for the first...

---

### Post by SeijiSensei on 2015-01-27
Just use mdadm and [create a software RAID1 array]("http://xmodulo.com/create-software-raid1-array-mdadm-linux.html") using the two disks.  You don't need a RAID controller.

Linux MD is hardly a "fake" RAID.  It's an implementation of the RAID standards at the operating system level rather than in the controller's OS.  Whether the CPU on the controller card is sufficiently faster than the tiny slice of the main CPU Linux MD requires is, ultimately, an empirical question I guess.  I've use both methods and find little observable difference in performance.

The Linux kernel has [good support]("https://www.kernel.org/doc/Documentation/scsi/libsas.txt") for the SAS cards that Dell uses in Linux servers. These are professional-grade devices that run [$100-500]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022630&IsNodeId=1&bop=And&Order=PRICE&PageSize=30").  Linux treats the array as a single SCSI device which it presents as /dev/sda.  

As you can guess, I don't think it's worth it.  Certainly not for video and audio streaming unless you're going to be supporting a whole lot of simultaneous clients.

Also don't use 14.10 or any non-"LTS" version on a server.  Install 14.04.1 which has [support until 2019]("https://wiki.ubuntu.com/Releases").

> **MartyBuntu said:**
> Why would you want RAID for a simple home file server?
The second disk would be of better use as a backup drive for the first...

I can see both sides of this story.  Yes, "RAID is not a substitute for backups," as I myself have experienced.  That said, a 2 TB external device makes a much better backup device than a second internal hard drive.  I'd take advantage of that device's better performance and devote it to RAID, then back up the array to an external drive every night.

Also RAID1 has better read performance than a single disk since the OS can pick blocks off of both devices and merge them into the data stream.  It does have slightly slower write performance, since two copies of every block must be written, but vaudevillian's server will largely be handling read requests.

---

