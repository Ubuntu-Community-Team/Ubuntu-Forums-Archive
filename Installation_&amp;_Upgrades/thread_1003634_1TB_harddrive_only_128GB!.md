---
title: "1TB harddrive only 128GB!"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by CalvinMcGee on 2008-12-06
I've been running Ubuntu since 7.04 on my laptop. I have recently put together my own stationary and were suppose to install 8.10 on it.

I ran the installation and made all the partitions. Beside SWAP, / and /home I also made /media/Media and /media/File to cover the rest of my Seagate 1TB disk.

When I started Ubuntu I had some problem with mounting the /media/File partition. I got a "check fail" upon boot from /dev/sda8, which was /media/File. When I checked the partitionmanager there were only one unpartitioned disk that was 128GB small. None of my other partitions were there. i found this really odd. After that I ran an update, and among the packages the Linux kernel was there, linux-headers. After I rebooted I recieved an "Error 22" from GRUB and I couldn't start from the harddrive. In bios I recieved information that my harddrive only was 128GB small.

WTF! I tried to run the live-cd and test with the partitionmanager, but same answer there. Only a 128GB unpartitioned disk. I did a new install on that disk and my other partitions still don't show up. What the **** should I do?!!

I also tried with a Vista-DVD, but same thing there only the 128GB disk.

All help is appreciated. I didn't spend a lot of money to get a 128GB harddrive.

---

### Post by taurus on 2008-12-06
Maybe you want to update your BIOS!

---

### Post by CalvinMcGee on 2008-12-06
> **taurus said:**
> Maybe you want to update your BIOS!

Do you really think that's the problem? In that case I might give it a try.

Why is my 1TB harddrive 128GB? I don't get it!

---

### Post by taurus on 2008-12-06
Mostly the BIOS.  How old is your machine?

---

