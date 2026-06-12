---
title: "Ubuntu does not properly identify my P3's"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by Executioner on 2007-06-24
Had a bunch of spare parts laying around and several hours to play, so I decided to give Linux Ubuntu a shot. I had tried it a couple of years ago, but it was not my cup of tea.

Anyway, I have it installed using a SuperMicro dually P3 1.13GHz cpu's with 2.5 gigs of ram. I have it installed on a cheap 15 gig drive I had laying round. The installation went great with no errors. I must say they have made a great improvement to the version I tried 2 years ago. The interface is more intuitive and user friendly.

While looking in device manager, I noticed that the cpu's are not properly identified. It simply states:
Vendor: unknown
Device: unknown
Bus Type: unknown

I thought that this version of Ubuntu would properly detect my 2 cpu's as SMP system. I'm using 6.10 Ubuntu on a Supermicro P3TDLE. All the other hardware was properly identified. I never thought it would not recognize a P3 cpu. Any ideas from you Linux experts?

---

### Post by louistan3 on 2007-06-24
hi,

im not sure how to fix your problem but have you tried checking the cpu info?

```
cat /proc/cpuinfo
```

you can use this command to see some stuff about the cpu.. or in your case cpu's...

the info on that might be able to help solve your problem.. 

goodluck...

---

### Post by CrispyFried on 2007-06-24
does seem kind of odd. are they recognized in the bios?

---

### Post by Executioner on 2007-06-24
> **CrispyFried said:**
> does seem kind of odd. are they recognized in the bios?They are recognized in the BIOS. I also have Win XP Pro installed, and it's properly identified as a multiprocessor pc.

I just want to make sure it's using both cpu's. Is there any other way to check?

---

### Post by CrispyFried on 2007-06-24
fire up the system monitor (in system -> administration), it should show both cpus.

---

### Post by Executioner on 2007-06-24
> **CrispyFried said:**
> fire up the system monitor (in system -> administration), it should show both cpus.
It only shows one cpu. Someone recommended upgrading to version 7. If so, how do I go about upgrading from this version? I tried to boot with the CD, but it game back with all sorts of error reading the CD. If I boot into version 6 and pop in the CD, I'm able to see the files on the version 7 of the CD, but not sure how to upgrade or install the new version.

---

### Post by Super TWiT on 2007-06-24
When the cd boot menu comes up there should be an option to verify the cd.  Try that to see if the cd is damaged or burned incorrectly.  If you think it was burned wrong try burning at lower speeds. Also the update manager should allow you to upgrade to version seven.  I am not sure how reliable this is though.

---

### Post by Executioner on 2007-06-26
OK finally got it to recognise the 2 cpu's, even though it does not properly identify them. They are show in device manager as 2 cpu's and in system monitor. What I should have done first was to install the 140 updates to the software. I never connected the cable to the hub for internet access. I also ran the Package Manager, and searched for SMP, and found the file. I installed it and it rebooted, but it was still shown as a single cpu until I installed all the 140 updates to the software, which brings me to another question. Where would the downloads be kept? I would like to make a copy of the files in case I wanted to install this version again from scratch.

I'm probably not going to mess with 7.04 as it seems too buggy. I'm getting the bin/sh: can't access tty; job control turned off error message.

---

### Post by CrispyFried on 2007-06-26
/var/cache/apt/archives/*.deb

---

