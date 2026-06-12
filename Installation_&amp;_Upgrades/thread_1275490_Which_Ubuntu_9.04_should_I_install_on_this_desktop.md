---
title: "Which Ubuntu 9.04 should I install on this desktop system?"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2009-09-25
This is a desktop system:
[LIST]
[*]Case: Mini-ITX
[*]Processor: 1.6GHz Atom 330 Dual Core Processor
[*]Memory: High Quality Mushkin 2GB DDR2 (PC2-6400)
[*]Motherboard: Intel Desktop Board D945GCLF2 LGA775 mini-ITX with Intel 945GC Chipset
[*]Video: Intel Graphics Media Accelerator 950 & S-video output support
[*]Audio: Realtek ALC662 audio codec (5.1 channel HD audio)
[*]Storage: 80GB 7200RPM, SATA
[*]LAN: Gigabit (10/100/1000 Mbits/sec)
[/LIST]
Which Ubuntu 9.04 should I install on this desktop system?
Would it be the Intel iso or the Netbook Remix?

---

### Post by rreese6 on 2009-09-25
Intel is my opinion. 
Boot the liveCD
Run the check CD for errors
if all is good then run it off of CD first to see if everything works.
if it does then install.

---

### Post by boondocks on 2009-10-29
According to [Intel]("http://ark.intel.com/Product.aspx?id=35641"), this is a **[SIZE="2"]64 bit[/SIZE]** 1.6GHz Atom 330 Dual Core Processor.

Can I use the "ubuntu-9.10-desktop-**[SIZE="2"]amd64[/SIZE]**.iso" to install the latest release on this system?

---

### Post by snowpine on 2009-10-30
You have your choice. On my Foxconn Atom 330 computer R10-S4 I've successfully installed 3 different versions of Ubuntu 9.04: i386 (32 bit), amd64 (64 bit), and lpia (Atom optimized). I am still playing around with it to figure out which is the best option. If you are in doubt which to choose, and performance is not a big concern, I'd recommend i386 (32bit) since it is the most ubiquitous architecture and therefore most compatible with the "outside world."

I would not recommend 9.10 at this point for the Foxconn R10-S4; it tends to crash on me within 5 seconds of logging in (unless I disable Compiz desktop effects). Stick with 9.04 is my advice.

---

