---
title: "Making an image of a full SSD into a HDD in a computer with 2 slots"
date: 2017-09-03
forum: Hardware
---

### Post by bold33 on 2017-09-03
So, I have a 512GB SSD I need to image to analyze with testdisc or photorec (Im looking for a text file). My plan is to buy a 512GB HHD for the remaining slot, make a full image of the SSD into the new HDD and work from a live usb on the image in the HDD alone.

Will this work?

cheers

---

### Post by TheFu on 2017-09-04
Sure.  Use ddrescue to clone it.  However, when SSDs fail, they tend to die quickly with very little warning or ability to get any data off.  Always, always, have backups.  Automatic, daily, versioned, backups.

And you might want to get a slightly higher HDD, since different storage media might have different sector sizes and round offs can suck.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) might be helpful

---

### Post by lammert-nijhof on 2017-09-07
My SSD failed and changed from working to completely dead in 1 msec. I had the zipped monthly back-ups from my virtual machines. I reinstalled the Host OS and restored those VMs and did rerun all software updates from the last three weeks, in total 6-8 hours of work. :)

---

### Post by TheFu on 2017-09-07
> **lammert-nijhof said:**
> My SSD failed and changed from working to completely dead in 1 msec. I had the zipped monthly back-ups from my virtual machines. I reinstalled the Host OS and restored those VMs and did rerun all software updates from the last three weeks, in total 6-8 hours of work. :)

With solid, daily, automatic, backups, each VM should have needed 45-60 min to restore, at most.  I usually finish in 30-45 min.

---

### Post by lammert-nijhof on 2017-09-11
@The Fu: I had to restore 13 VM's and 8 still received periodical OS updates and two (XP and Vista) needed the anti-virus/malware SW updates, so that takes time even if you overlap everything. I back-up to a 320GB 3.5" IDE HDD using USB 2.0 and I maintain the same VMs on my laptop. I don't change very much in my VMs and they all share the same partition to store their data. 
I do not see a need to automate that back-up or to do it more frequently. For that data partition I look for a better solutions then syncing it with laptop and another USB drive.

---

### Post by TheFu on 2017-09-12
>  320GB 3.5" IDE HDD using USB 2.0 
Ouch!

---

### Post by lammert-nijhof on 2017-09-13
What you don't realize that the "Compress" function in Nautilus runs at one CPU, so the real bottleneck is the CPU not USB 2.0. I think my USB 2.0 disk occupation is around 40%. Before doing it again in 14 days I'm looking for another compression program that uses all CPUs. If somebody has a suggestion? Otherwise I might have to use my Windows 7 Virtual Machine, that is possible, because for some forgotten reason the 320GB disk still has the NTFS format.

---

### Post by TheFu on 2017-09-13
Not sure what Nautilus has to do with anything, but ...  [https://askubuntu.com/questions/258202/multi-core-compression-tools](https://askubuntu.com/questions/258202/multi-core-compression-tools)

---

