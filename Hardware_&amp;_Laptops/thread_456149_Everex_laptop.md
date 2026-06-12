---
title: "Everex laptop"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by sheine on 2007-05-27
A couple of days ago, I ordered an Everex laptop from Wal-Mart because of the good price and specifications. Subsequently, I searched the internet and found that this computer has a hard time with linux including Ubuntu.

It seems likely that the cause is the pre-installed Vista. The head of the corporation that makes the via processor is very friendly toward linux so it seems probable that the computer should work with linux.

As a result, I plan to wipe out Vista and make the computer a pure linux computer. Is there any reason why this should not work?

At worst, I can take it back to Wal-Mart because I do not want a Windows only computer.

---

### Post by chocbar31 on 2007-05-27
From my experience, I've ALWAYS removed pre-installed OS's. They don't configure or setup the units with everyone's best interest at heart. Even though, they try to help and assist everyone. But I am a geek and have some experience with computers and OS's.

However, to be sure; Boot-up the Ubuntu Live CD and give it a test-run. If all goes well, then you will at least know that everything will work. This will also allow you to test the laptop without voiding the terms, by scraping the OS, in-the-event you had to return it. VIVA-la-Live.Ubuntu

I actually run Winblows in VMware Server, which is free for Linux users. It runs VISTA and XP perfectly. I run XP for VB classes, as I am learning to write. I will use my new found education to assist with the improvement of Linux in the future. Don't get me wrong...I'd learn Python, but my school doesn't teach Python. YET!!!

:D

---

### Post by MakLeod on 2007-05-30
I am thinking about buying one of these laptops too.  Can you update us on the functionality of linux once you try it out?  :D

---

### Post by sheine on 2007-06-02
I picked up the Everex today. It made a good initial impression on me.

The first thing that I did was to determine its compatibility with linux. I tried out six live CD's and only Damn Small linux got stuck in the booting process. It uses a Via processor instead of Intel or AMD.  Pclinuxos and simply mephis automatically recognized my wireless connection at the time the computer was booted. Kubuntu had a way to configure the wireless so that I also made a wireless internet connection with it. I have not succeeded in connecting Ubuntu and Puppy to the internet.

I then took my first look at Vista which is installed on it. It also recognized my wireless and connected me to the internet. I have not yet attempted to partition the disk with Vista to make room for linux operating systems. I do not like the fact that when you shut down Vista it automatically updates during the shutdown. I am a little concerned, based on what someone wrote on the internet, that these updates could interfere with linux partitions. Should that happen, I will get rid of Vista.

After being on for quite a while, the computer was slightly warm not hot like my previous laptop.

---

### Post by sheine on 2007-06-03
Round one to Microsoft. 

I tried to add linux by the same method that I used with my xp computers. I used gparted to shrink the size of the Vista partition and then installed linux in the freed space. After it was all done, grub could boot linux but not vista. I tried the "standard" recovery for Vista but it did not work. I then did the "full" recovery which restored the computer to factory settings.

Round two in underway. I shrank a microsoft partition using Vista's disk management. It gave me about half of the hard drive and kept the rest of Vista. I am now installing linux on the freed space. People on the internet say that grub can boot both if you use this method. I shall post my result.

---

### Post by sheine on 2007-06-03
Round two to Microsoft.

I used the Vista software to create a partition, installed linux on the partition with grub, and grub could not start Vista.

Presumably because it is using a via processor, it cannot give a higher resolution than 800x600. It has a nice big screen but you expect better resolution with such a screen.

Finally, I discovered that it only has 3/4 of specified memory. Since I bought it at Wal-Mart I expect to return it without a hassle.

---

### Post by Prisma on 2007-06-08
According to some reviews at new egg store the Everex laptops have some sound card issues with linux. What was your experience running Ubuntu? Also, its quite interesting that Ubuntu cant detect your wireless network but Kubuntu can.

---

### Post by doubleij on 2007-06-13
Which live cd's worked for you Sheine? My Everex Stepnote has an Intel Dual Core and has hung on DSL and Feisty. I am a noob, so I have no idea how to install Linux any other way. I have wiped the hard drive removed Vista entirely but the problem persists, so I think its a hardware issue. Any ideas?

---

### Post by sheine on 2007-07-03
I have now purchased the Everex VA2000T. pclinuxos and simply mepis seem to work flawlessly with it. I have not been able to use Ubuntu with it. Ubuntu insists on an 800x600 resolution. When I tried to install Ubuntu on my hard drive it froze at the partitioning part of the installation.

---

