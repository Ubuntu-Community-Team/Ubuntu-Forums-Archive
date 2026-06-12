---
title: "Installation on Gateway 400Mhz with 64MB Ram"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by GRMrGecko on 2009-04-18
Hello, I'm trying to install Ubuntu Server on a Gateway that I got today, it's really old and had Windows 98 on it. I burned a cd of i386 server and when it gets to starting up partitioner, it stops at 50%, why might that be? I tried moving the hard drive to different ide ports on the computer but same result.

is it even possible to run Ubuntu 8.10 Server on it?

Thanks,
Mr. Gecko

---

### Post by mikewhatever on 2009-04-18
It's too old for Ubuntu. [https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#System%20Requirements](https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#System%20Requirements)
Try slitaz [http://www.slitaz.org/en/](http://www.slitaz.org/en/) or dsl [http://damnsmalllinux.org/](http://damnsmalllinux.org/) instead.

---

### Post by ddrichardson on 2009-04-18
Like the last poster said, you're going to struggle putting Ubuntu on that low spec hardware, especially because the installer requires quite a bit of memory.

I have Damn Small Linux on a much lower specification PC than that though so you shouldn't have any problems with it but you will need a fair amount of swap space.

Depends what you want to do with it afterwards.

---

### Post by GRMrGecko on 2009-04-18
> **ddrichardson said:**
> Like the last poster said, you're going to struggle putting Ubuntu on that low spec hardware, especially because the installer requires quite a bit of memory.

I have Damn Small Linux on a much lower specification PC than that though so you shouldn't have any problems with it but you will need a fair amount of swap space.

Depends what you want to do with it afterwards.

So if I added more ram, would I be able to have Ubuntu?

---

### Post by Chemical Imbalance on 2009-04-18
> **GRMrGecko said:**
> So if I added more ram, would I be able to have Ubuntu?

If you can add a good bit more (say at least 128 or more)  you might be able to install with the alternate disc.  256 MB may be the stated minimum, but I've read testimonials from people with at least 128MB's.

---

### Post by ddrichardson on 2009-04-18
Jaunty recommends 256Mb but even then you'll need the alternate install CD.

---

### Post by mikewhatever on 2009-04-18
> **GRMrGecko said:**
> So if I added more ram, would I be able to have Ubuntu?

You'd be able to install with the Alternate cd (text installer), but the system would probably crawl unable to do any multitasking.

---

### Post by kerry_s on 2009-04-18
> **GRMrGecko said:**
> Hello, I'm trying to install Ubuntu Server on a Gateway that I got today, it's really old and had Windows 98 on it. I burned a cd of i386 server and when it gets to starting up partitioner, it stops at 50%, why might that be? I tried moving the hard drive to different ide ports on the computer but same result.

is it even possible to run Ubuntu 8.10 Server on it?

Thanks,
Mr. Gecko

ubuntu server should run fine on those specs, i suspect the burning, when burning iso's you have to burn slow 4x is best.
if that still doesn't work it could be a bad hd or bad ram, i would check the ram first, as the cd loads to ram when installing.

---

### Post by mikewhatever on 2009-04-18
I missed the server part completely in the original post, so forget what I said so far. Sorry about that.

---

