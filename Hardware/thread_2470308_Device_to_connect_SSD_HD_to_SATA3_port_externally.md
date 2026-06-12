---
title: "Device to connect SSD HD to SATA3 port externally"
date: 2021-12-25
forum: Hardware
---

### Post by satimis on 2021-12-25
Hi,

Some software require to run on bare-metal HD.  It is inconvenient each time to open the computer case to change a new SSD HD.  Is there a solution to connect SSD HD to SATA3 port externally, not via USB port which speed is not fast,

Please advise.  Thanks

Regards

---

### Post by Autodave on 2021-12-25
Why don't you just get a longer SATA connector and run it outside of the PC case?  Same with the power: they are all readily available on Amazon and a bunch of other places.

---

### Post by oldfred on 2021-12-25
If using SATA, not NVMe I find USB3 to be not that slow.
I was a bit surprised how well my SATA SSD worked using USB3. I have always used flash drives which were very slow.

My not well documented speed test is an install of Ubuntu, now Kubuntu which is a bit faster.
Installs are always using toram parameter so ISO fully in RAM.

Full install to flash drive is about 45 minutes.
Full install to internal SSD about 10 min.
Full install to internal HDD about 14 min.
But full install to USB3 external SSD  was somewhere between internal SSD & HDD.
I thought USB3 was big part of bottleneck, but it is not.
My next system will have USB-C and faster speeds. And then I may not use flash drives anymore.

---

### Post by satimis on 2021-12-26
Hi all,

Thanks for your advice.

Autodave's suggestion is a good idea.  I have long SATA connector and power extension cable.

Just bought a Crucial MX500 SSD, 500G storage and 6GB/s speed.  I'll start my adventure soon

Hi oldfred,

USB-C stick is fast and its price is not cheap for the time being.  My problem is none all my desktop computers having USB-C port.  

I have 3 desktop computers.  Now it is time for me to build a new AMD Ryzen 7 desktop computer, if having spare time.  My AMD Ryzen 5 desktop computer is already 4 years old.  I'm now fully focused in enhancing the quality of my old video clips.

[B][COLOR="#FF0000"]Edit-1
====[/COLOR][/B]
I have another thought.

Would it be possible to get a large storage SSD, say for example 2TB
Partition the SSD into 4 partitions
Install OS on the 4 partitions at the same, simultaneously.

Then I'll have 4 bare-metal 500G SSDs, ready for future test

If this arrangement works;

The only disadvantage compared to VM/Guest is unable to run 4 OS on 4 partitions at the same time.  But it is possible running several VMs/Guests at the same time

**[COLOR="#FF0000"]Edit-2[/COLOR]**
HOW TO ADD USB-C PORTS TO YOUR COMPUTER
[https://www.youtube.com/watch?v=b-yUZvEbjn4](https://www.youtube.com/watch?v=b-yUZvEbjn4)

But it needs a PCIe slot on your computer

Regards

---

