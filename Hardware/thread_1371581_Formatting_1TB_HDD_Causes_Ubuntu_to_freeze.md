---
title: "Formatting 1TB HDD Causes Ubuntu to freeze"
date: 2010-01-03
forum: Hardware
---

### Post by lynwode on 2010-01-03
Hi,
I have recently purchased a 1TB Seagate HDD to be used as additional storage in my 8.04 install. I have tried to format to ext3 from both gparted and via the command line and each time I attempt this Ubuntu locks up (after 30 secs or so) and I am unable to do anything - cannot even ssh in to check logs etc...

I have googled away but have not found any clues to what the issue may be.

Has anyone come across this issue or have any ideas on how I can get this drive formatted?

Cheers,
Tim.

---

### Post by lynwode on 2010-01-04
Well things got weirder - using a live cd I was able to format the drive as ext3. But then it only showed up as a 32MB drive!!!]

After some more digging around on google I found several threads on similar issues and after downloading a copy of Seagates disk tools and resetting the disk to its Native size and reformatting via live CD all is good.

All up very strange but at least I have the disk up and running.

---

### Post by dcory on 2010-01-16
Could you provide any further detail on how you got it working?  I'm having a very similar problem with a WD drive, but I'm trying to use it as my primary drive.  At first I tried using ext4, and that didn't work.  
Then I tried ext3, and that didn't work unless I used an older version of the OS (8.10), which also happened to be 32-bit.  My system is 64-bit.  I managed to format it, but then the system crashed when installing the 64-bit OS.

I could go on about the various things that worked or partially worked, but the short version is that I'm without a working system.   Your post was the closest to my problem, so I thought I'd ask you first if you had any other suggestions. If you don't have anything else to add, I'll make a new string.

District

---

