---
title: "Booting partitions?"
date: 2011-07-21
forum: Hardware
---

### Post by musicguyguy on 2011-07-21
I recently installed UbuntuStudio 11.04 and Windows 7 Ultimate on a single 1.5TB hard drive.

The current partitions are (approx):
Ubuntu Studio 50GB ext4
Ubuntu swap 25GB swap
Windows 7 250GB NTFS
Windows system 100MB ???
unallocated 1.2TB

I am able to view the partitions in any software, including GParted, Partition Wizard, etc, but my motherboard seems unable to recognize it; i.e. when I startup and boot from hard drive, Windows starts.

My motherboard is MSi GF615M-P33 and is connected to the hard drive via SATA cable (not 24-pin).

---

### Post by oldfred on 2011-07-21
Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Windows 7 standard install creates two partitions. One is a 100MB boot/recovery partition and the other is the main system. The boot is separate in case you want to encrypt the main partition.

---

