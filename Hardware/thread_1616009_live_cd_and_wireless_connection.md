---
title: "live cd and wireless connection"
date: 2010-11-07
forum: Hardware
---

### Post by Fardin on 2010-11-07
my laptop hard drive gave up.
I can run ubuntu on live cd but can not connect to internet
it seems like a wireless driver (b43) needs to be installed.
I connected the laptop to ethernet and tried to download and install the driver
it did
but it asked for a restart to complete the installation
after restart, it seemed as no download or installation ever had happened.

is it possible to somehow include the wireless driver in live cd?

in other words is it possible to connect wireless with live cd?

---

### Post by garvinrick4 on 2010-11-07
Live CD will not hold changes, no persistence they call it. Need a USB install with persistence to hold changes in Live mode.

---

### Post by Fardin on 2010-11-08
> **garvinrick4 said:**
> Live CD will not hold changes, no persistence they call it. Need a USB install with persistence to hold changes in Live mode.

Can I use a write/rewrite cd instead of usb?

---

### Post by garvinrick4 on 2010-11-09
> **Fardin said:**
> Can I use a write/rewrite cd instead of usb? I do believe they are about 700 meg and iso file about 699 meg so changes will be held in RAM and not in the cd itself. Only place is RAM ,HDD is not even mounting any partition at all. So I would say give up on persistence in CD.

---

### Post by mastablasta on 2010-11-09
1 GB USB (which should be enough) is cheap and persistance is easy to make.

---

### Post by Fardin on 2010-11-10
> **mastablasta said:**
> 1 GB USB (which should be enough) is cheap and persistance is easy to make.

I nuked my hard drive and found that some sectors were defected.
after repartitioning and reformating it seems to be working fine. 
However I was wondering if I should just use ubuntu from 1 or 2 GB USB.

My question is that when I used live CD Ubuntu was very slow and it was also using my cd drive intensly.

How fast is Ubuntu using USB?  Same as installed on hard drive or same as live CD or in between?

---

### Post by garvinrick4 on 2010-11-10
> **Fardin said:**
> I nuked my hard drive and found that some sectors were defected.
after repartitioning and reformating it seems to be working fine. 
However I was wondering if I should just use ubuntu from 1 or 2 GB USB.

My question is that when I used live CD Ubuntu was very slow and it was also using my cd drive intensly.

How fast is Ubuntu using USB?  Same as installed on hard drive or same as live CD or in between?
4 gig max persistence in Start Up Disk Creator in Ubuntu and a live USB at same time.
So 4 gig is nice and login: ubuntu  password; is blank (no password)

---

### Post by Fardin on 2010-11-12
> **garvinrick4 said:**
> 4 gig max persistence in Start Up Disk Creator in Ubuntu and a live USB at same time.
So 4 gig is nice and login: ubuntu  password; is blank (no password)

Could you explain please I did not understand.
Do i need 4 gig on hard drive or on usb?

---

### Post by garvinrick4 on 2010-11-12
Startup disk creator in Ubuntu will give you up to 4 gig of persistence (holds changes) on a flash drive. Can use 2 gig or whatever you want will go up to 4. Can use 8 gig and partition to two 4 gig partitions one for Live USb with 4 gig persistence and one 4 gig partition for extra home. It just has a limit to 4 gig of persistence. Read up on squashfs and casper, google if you want to understand the hows and whys. 
 You can actually install a system on flash drives, lots of threads on that. Flash drives will
wear out quicker if used a lot. Disk drives are just flat dirt cheap nowadays, USB portables 320 gig 49 bucks and need no case just plug and play. 20 years ago SCSI 3.4 GIG Seagate
5 1/4 inch was 10,000.00 wholesale. RAM $700.00 for every 16 meg chip. Put together a mac system for desktop publishing 256 meg of Ram and 3.4 gig Seagate, 21 inch dual page monitor with video card and some software. $50,000 grand a crack, have to make decision then 4 computers or pay cash for a house. Now a $500.00 box can do everything but kiss you good night. Is really quite astonishing how quick this all happened. Ok done rambling.
 Answer was 4 gig on flash drive to original question.

---

### Post by Fardin on 2010-11-17
> **garvinrick4 said:**
> Startup disk creator in Ubuntu will give you up to 4 gig of persistence (holds changes) on a flash drive. Can use 2 gig or whatever you want will go up to 4. Can use 8 gig and partition to two 4 gig partitions one for Live USb with 4 gig persistence and one 4 gig partition for extra home. It just has a limit to 4 gig of persistence. Read up on squashfs and casper, google if you want to understand the hows and whys. 
 You can actually install a system on flash drives, lots of threads on that. Flash drives will
wear out quicker if used a lot. Disk drives are just flat dirt cheap nowadays, USB portables 320 gig 49 bucks and need no case just plug and play. 20 years ago SCSI 3.4 GIG Seagate
5 1/4 inch was 10,000.00 wholesale. RAM $700.00 for every 16 meg chip. Put together a mac system for desktop publishing 256 meg of Ram and 3.4 gig Seagate, 21 inch dual page monitor with video card and some software. $50,000 grand a crack, have to make decision then 4 computers or pay cash for a house. Now a $500.00 box can do everything but kiss you good night. Is really quite astonishing how quick this all happened. Ok done rambling.
 Answer was 4 gig on flash drive to original question.

Thanks, I didn't know flash drives can go out fast.  Good to know.:popcorn:

---

