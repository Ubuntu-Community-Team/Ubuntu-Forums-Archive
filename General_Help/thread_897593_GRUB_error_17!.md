---
title: "GRUB error 17!"
date: 2008-08-22
forum: General Help
---

### Post by budding_h4x0r on 2008-08-22
I've been running Ubuntu (not daul booting, ubuntu's all there is there) for several months now on my Dell Inspiron 1420 without any problems, but yesterday I found that my computer was running a lot more slowly than it should. Today I booted it and found GRUB error 17. I tried usin a Super GRUB disk,but that didn't work, and I've tried booting from the startup disk and editing the partitions but that isn't working eihter. GParted says that my linux volume is unkown filesystem type...

Please help!

---

### Post by budding_h4x0r on 2008-08-22
bump

---

### Post by budding_h4x0r on 2008-08-22
bump again please help

---

### Post by ajgreeny on 2008-08-22
If you have a live CD boot it up and then check what the properties are of the partitions on the hard disk with ```
sudo fdisk -l
```That will tell you what the file type of all the partitions is, which I presume Dell will have made ext3, at least for the ubuntu partition.

Thast may give some clues as to what is going on, but it sounds rather suspiciously like a bad hard disk, so if you can, while the live CD is running, backup all your personal files to a USB disk, if you have one.  Hopefuly, however, you do that as a matter of course so already have them backed up.

---

### Post by Luchostein on 2008-12-10
I got EXACTLY the same problem. It happened once some months ago. The only thing I could do was to repartition and reinstall. Now it happened AGAIN. The way things go is:

* Dell Inspiron 1420, 80GB, Windows Vista.
* Full HD cleanup. Not interested in Windows.
* Clean install. Kubuntu Linux 8.04 Gutsy Gibbon.
* Multiple partitions on my 80GB HD (all Ext3):
- Primary:
-- 1: 100MB on /boot (Grub, kernel, menu.lst and so)
-- 2: 10GB on /
- Extended:
-- 5: 2GB for swap
-- 6: 5GB on /tmp
-- 7: remaining on /home

* Months of typical use: wi-fi, browse, docs, IM, e-mail.
* Regular daily updates.
... and then ...
... Reboot ...
Grub stage1.5: Error 17

No way to boot from HD. I tried:
- BIOS reset: ... nothing happens.
- BIOS test (+ full): ... nothing bad happens. After this, the BIOS tried to run the Dell Diagnostic Partition, which was not found (naturally, I erased it at the beginning of the times).

Then I tried with a LiveCD (Kubuntu 8.10 Intrepid Ibex). My fdisk -l only shows one partition with some random size and is reported as Win95 FAT (where did it come from??!!). I mounted it read-only to see what the bleep does it contain. After some file browsing, it looks like a regular clean Windows install (??!!).

I guess it is some kind of restore partition which was flashed somewhere...

So I tried to run the Media Direct. After the Media Direct welcome screen I get again the same Error 17 from Grub.

Now I try again with the LiveCD and fdisk -l now reports a different size and a different type of partition (just "extended"). WTF???

As far as I can see, somehow, the partition table was automatically wiped out and overwritten with trash.

Last time I had everything backed up, but now it caught me with some important files not yet backed up.

What happened? How did it happen? Why did it happen? How can we fix it? It just breaked from one day to the next... carrying it out with our information.

I seems to me that Media Direct might be involved. Does Dell say anything about it?

I'd apreciate if you can share any information about it.

Regards.

---

### Post by caljohnsmith on 2008-12-10
Luchostein, sounds possibly like you could have a hardware problem. How about first posting:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
sudo xxd -l 2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
```
And then to check the health of your HDD, how about doing:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the contents of those two files on your desktop so I can see the results. We can work from there if you want. :)

---

### Post by Luchostein on 2008-12-10
Gotcha!

[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1420]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1420")

> The Dell MediaDirect Button opens up the Music Player application if the laptop is on. If the laptop is OFF, the Dell MediaDirect application loads itself and appears to modify partition information and write files to the hard drive. I collected evidence to support this. The manual states that the MediaDirect application is wiped out if the hard drive is repartitioned, but this is either not true, or partially true. I was UNABLE to reboot after pressing the button while off, reinstallation was the quickfix. Further research indicates that the behaviour can be corrected by turning the Flash Control Module off in the BIOS. This is the recommended solution. After turning the FCM off, the MediaDirect button merely starts the operating system, and therefore becomes a secondary on switch. 


Obviously, you SHALL KNOW that you can't press the Media Direct button on your Dell Inspiron if you repartitioned at your own will.

Now, let's find out how to clean this partition mess...

---

