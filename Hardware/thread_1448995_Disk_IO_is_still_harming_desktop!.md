---
title: "Disk I/O is still harming desktop!"
date: 2010-04-07
forum: Hardware
---

### Post by isecore on 2010-04-07
This has been a gripe for me with Ubuntu since at least the last two years of releases.

It's always the same: disk activity harms the desktop responsiveness.

Whenever doing something that generates disk-activity (unpacking RAR-files, moving files, whatever) something in the background will start using A LOT of I/O (or whatever) which in turn means that the desktop becomes unresponsive.

Applications turn grey, the computer becomes sluggish.

This was a problem on my previous computer, and it's still the same on my new computer - despite a complete reinstall and completely different hardware. In fact, it's even worse on my new computer. The slightest thing can make applications and the desktop stops responding for 10-20 seconds.

I'm not kidding, there can literally be almost nothing, and the computer simply stops responding for a while. Music stops playing, apps turn grey. As if I was running on a fraction of the computing power available.

I'm incredibly frustrated by this, and it's been an issue for TWO YEARS. I first started experiencing it in Hardy 8.04 on my then-brand new machine. And it's still here on a completely different machine two years later, making it even worse.

Running Karmic 9.10, fully patched, AMD64. Machine in question is a Phenom II 955, 4 gigs of RAM. Harddrives are two almost identical Western Digital 1 terabyte SATA/300 drives, LVM'ed together.

Motherboard is one of these: [http://www.giga-byte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=3258](http://www.giga-byte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=3258)

---

### Post by cchhrriiss121212 on 2010-04-08
Try running system monitor and performing one of the tasks that cause trouble. Make note of how much cpu is being used up by the process, then search for a solution.

---

### Post by isecore on 2010-04-08
> **cchhrriiss121212 said:**
> Try running system monitor and performing one of the tasks that cause trouble. Make note of how much cpu is being used up by the process, then search for a solution.

I can tell you that it doesn't show anything at all. I'm guessing whatever is causing it is very low-level because it doesn't show up in htop or system monitor. It shows a very high load in the background, but no active process consumes the CPU.

Additionally, even at very low disk-activity for no apparent reason the desktop will stop responding. For example, opening Thunderbird with no discernible load will make everything sluggish and often make everything stop responding.

In fact, the system is incredibly sluggish. Opening folders take literally several seconds. Sometimes I wonder if I clicked properly, do it again, then all of a sudden 5-6 windows of the folder (or whatever) opens.

This is absolutely ridiculous.

I think I'm gonna record a screencast of this so you can see for yourselves.

---

### Post by a.walker on 2010-04-08
Have you tried a default partitioning setup on a single hdd? I run ubuntu smoothly on some pretty janky old hardware. If you have raid set up your problem might be there.

---

### Post by isecore on 2010-04-09
> **a.walker said:**
> Have you tried a default partitioning setup on a single hdd? I run ubuntu smoothly on some pretty janky old hardware. If you have raid set up your problem might be there.

No, I haven't tried that yet, but I might do it if I find an old HDD to try it on. However, I want to use LVM, since I have two drives that I want to spread the system over.

I'm not using any type of RAID/fake-raid.

---

