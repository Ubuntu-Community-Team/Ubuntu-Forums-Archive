---
title: "DVD Burner isnt listed"
date: 2005-12-04
forum: General Help
---

### Post by Drunken Pirate on 2005-12-04
I have two CD/DVD Drives:
1) AOpen DVD+RW CD+RW
2) Toshiba DVD/CD+RW

I created an DVD ISO, called TERROR.ISO, and I want to burn it to a DVD. So I right click on my TERROR.ISO, and click on Write To Disk. It opens up the write to disk dialog, but the only drive that is listed is the Toshiba. How can I get it to list the AOpen drive as a burner drive?

---

### Post by root@localhost on 2005-12-17
I have the same problem, and have absolutely no idea how to make it recognize my AOpen DVD burner. There's another topic [here]("http://www.ubuntuforums.org/showthread.php?t=87634") about this, but after my searching, I still haven't found any solution. Perhaps some different burning software might help--I'm just using the default thing that's integrated into the file browser for gnome.

---

### Post by jliedeka on 2005-12-19
Check your dmesg output to see which device was associated with your drive.  For example, here's what I get when I grep for hdc:

jliedeka@damballa:/etc/mplayer $ grep hdc /var/log/dmesg
[4294672.060000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:pio, hdd:pio
[4294673.608000] hdc: MATSHITAUJ-822Da, ATAPI CD/DVD-ROM drive
[4294676.178000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache

Try a grep -i aopen /var/log/dmesg and look for a device like hdc or hdd or similar.  It could be sgX or sdX but probably hdX.

If it's hdc, then just cd to where your file is and use cdrecord like this:

sudo cdrecord -v -eject dev=/dev/hdc TERROR.ISO

---

