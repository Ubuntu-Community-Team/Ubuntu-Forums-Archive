---
title: "Wondering about  XUbuntu and SSDs"
date: 2017-10-17
forum: Hardware
---

### Post by flipper8827 on 2017-10-17
&#8203;I was curious as  to which solid state disk  Drives work Ubuntu/Xubuntu, as I am strongly considering upgrading my traditional hdd to a  1TB SSD to improve system longevity and performance.?

---

### Post by Bucky Ball on 2017-10-17
Pick any SSD. Doesn't matter.

---

### Post by oldfred on 2017-10-17
Bought a cheaper store brand 60GB SSD back in 2011 just to speed up old BIOS system and was retiring XP on HDD on MBR drive. Had two different / (root) partitions with different installs. Think that drive may still work but upgraded to a new UEFI system with larger SSD, but do not know what to do with space. I use SSD to boot and HDD for data.

Or I have used SSDs with gpt partitioning whether BIOS or UEFI for about 8 years.
I use LTS version as main working install, but have installed every version in last 8 years at least once, often multiple times just to try different configurations.

I do make a few configuration settings changes, but SSD are essentially as reliable as HDD. But any drive can fail at any time.

       [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)

---

### Post by QIII on 2017-10-17
My opinion:

Save some money and get a smallish SSD for the OS and keep data on a mechanical drive.  Data on iron oxide persists for decades.

SSDs suffer from charge leakdown.  The internal structure provides very little insulation to the individual cells and they can lose their state.  1s can drop down below the level detected as 1 (storage media does not exist in ones and zeroes,  but in "close enough").

This is sometimes referred to as "bit rot".  Some enterprise (expensive) SSDs are less subject, but it is inevitable at the current state of the art.  Less expensive SSDs can start to lose fidelity in weeks or months.  You could go back to a photo or movie in 6 months and find it trashed.  

The OS, on the other hand, is constantly reading and writing so the data is refreshed often.

Currently, SSDs are not a good choice for long-term storage.  So a large one may be a waste of your money.

Aside from bit rot,  SSDs are every bit as dependable and long-lived as HDDs now, so that's not a worry.

---

### Post by Bucky Ball on 2017-10-17
> **QIII said:**
> Save some money and get a smallish SSD for the OS and keep data on a mechanical drive.  Data on iron oxide persists for decades.

+1 and +1 to the rest of what QIII wrote. I use a decent quality SSD, Intel or Samsung Evos, and only ever 128Gb ones big enough for OSs. All data on the HDD(s). Fairly normal setup. OSs are fast and easy to backup.

---

### Post by martinr on 2017-10-18
Do you need a Seria ATA interface for an SSD (my laptop has a (mini) IDE interface).

---

### Post by efflandt on 2017-10-21
How old is that laptop? The newest laptop I have with PATA (IDE) drive is a low end Compaq from 2005 (which I got back when getting someone a newer laptop). I don't think it could even boot from USB. When its Windows hard drive failed I think I had to boot Ubuntu from CD at that time to copy data to an external drive. I doubt if there are any PATA SSDs.

A Toshiba laptop I have from 2006 has SATA1 for its hard drive, but I think still PATA for its DVD drive. I was quite surprised that its 5400 rpm drive was no faster than an  external hard drive on USB 2.0. An old 80 GB Intel SSD was 4 times  faster on its SATA1, and additional 2 times faster than that on my SATA2  desktop (twice as fast as its 7200 rpm drive).

A laptop may have a connector that you need to move from its old hard drive to a new one which could be confusing if you look at that connector vs. connection on the drive itself. This shows some examples: [http://www.drivesolutions.com/info/aboutlaptop.shtml](http://www.drivesolutions.com/info/aboutlaptop.shtml)

---

