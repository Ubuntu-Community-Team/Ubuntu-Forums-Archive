---
title: "Best Motherboard for ubuntu 8.04 LTS"
date: 2008-07-28
forum: Hardware
---

### Post by kristiandawe on 2008-07-28
What is the Best Motherboard (Asus Preferably) for Ubuntu 8.04 LTS. I plan to to use a Intel Core 2 Quad Q9450 CPU, nVidia GeForce 8800 GT 1024MB, 4GB of RAM, 1TB Hard Drive.

---

### Post by paulisdead on 2008-07-28
I've been really happy with my Asus P5Q-E.  I don't have the same proc as you're getting, but my 6420 runs just fine at 3.36ghz on it, overclocked up from it's default of 2.13.  Plus it's a PCI-E 2.0 mobo, so it's more future proof.  It runs ddr2 RAM, so you don't have to shell out a huge amount of cash for memory that ddr3 does.  My 4GBs of OCZ 1066 runs just fine on it.

Everything I use onboard works good, though I have to admit i haven't tried the onboard sound.  I still love my old Audigy for the hardware mixing support in ALSA.  

It's a little bit pricier than what you could get, but there's a lot of little touches that make it nice, especially if you intend to overclock.  With my 1.2ghz overclock, the only voltage I had to touch in the bios was the vcore.

It's also got external SATA on built in on the back of the mobo, so if you have AHCI enabled, you can hotplug SATA drives right into the back of your computer.

The layout is also really nice and well thought out.  A good amount of space between the ram, CPU, and PCI-E slots.  It's the little touches like having the RAM spaced far away from the top PCI-E slot where a video card would go, so if you use a high end video card, you don't have to take it out to mess with your RAM.  And if you ever decide to run it in a testbench, it's got power and reset buttons built onto the motherboard itself.

---

### Post by stchman on 2008-07-28
> **kristiandawe said:**
> What is the Best Motherboard (Asus Preferably) for Ubuntu 8.04 LTS. I plan to to use a Intel Core 2 Quad Q9450 CPU, nVidia GeForce 8800 GT 1024MB, 4GB of RAM, 1TB Hard Drive.

I have the Asus P5K with the 8800GT and Core 2 Quad.  The mobo works perfectly.  I recommend it much.

---

### Post by Sef on 2008-07-28
I have a P5VD2K-X, and it works great.

---

### Post by tubbygweilo on 2008-07-28
kristiandawe, 
A quick look through [phoronix]("http://www.phoronix.com/scan.php?page=category&item=Motherboards") may well repay the time spent browsing as they nearly always comment upon how well a product works with Linux.

---

### Post by rakan_dr on 2008-07-30
stchman, plz list your computer specifications, cuz i want to buy a new one.
Plz tell me about your motherboard experience. Is it fully compatable with Ubuntu 8.04????
I don't have enough budget now, so I want to buy a great motherbard now and then i'll upgrade my componenets.
I want to buy a motherboard so i have the ability to upgrade to INTEL core 2 quad processor. Do you recommend this motherboard?? how many points do you give it????
These are my computer specifications now:
CPU: INTEL P4 3.6 2MB L2.
Motherboard: ASUS 
RAM: Dynet 1GB
video card: Intel built in 64mb.
I want to know if this motherboard is great for OC and gaming.
by the way is it P5Q or P5Q premium???

---

### Post by BillJohnson on 2008-08-03
Running 8.04.1 LTS (AMD64)

Currently using:
Asus P5E3 WS Pro,
Q9450 OC'd to 3.0 Ghz
8 GB OCZ DDR3
nVidia 9600 GT 512 MB (using nvidia's latest driver)
4.5 TB of Sata drives

So far:
I am just using 8.04 stock install:
- ethernet is ok
- sound is ok
- video was ok (I upgraded to nVidia's drivers for better performance).

The only problem that I currently have is that 8.04.1 doesn't recognize the Marvell PATA chip so ubuntu is not finding the dvdrom that I have on the PATA bus. It does find the sata dvdrom ok (thank god..), but I have not found a solution yet. Marvel did provide linux drivers, but only for redhat and suse. They also provided the source, but I haven't a clue as to how to get them to compile and install.

---

### Post by jett on 2008-08-19
> **paulisdead said:**
> I've been really happy with my Asus P5Q-E.  

were you able to get Hardy to work on the P5Q? I'm seriously considering this board but I've read in other threads that they've had no luck in getting onboard sound and networking to work.

---

### Post by rjmichaelson on 2008-08-20
I just put together a new system based upon the ASUS P5K Deluxe WiFi and I have had ABSOLUTELY NO SUCCESS installing Kubuntu, Ubuntu, and even tried Fedora 9 and Xandros 4 and they did not work. This machine runs XP 32 Pro, XP 64 bit pro, and Vista Ultimate 64 bit without problems. The ONLY Linux distro that works on my machine is a Knoppix live disk. 

I ended up in this thread by looking for a more Linux-friendly MB and was surprised to see that somebody has had good luck with the ASUS P5K. My problems seem to be related to the disk drives. Xandros won't install at all. Kubuntu and Ubuntu get through the installation sequence, but on reboot I get all kinds of disk drive errors. 

I have two Western Digital 500 GB SATA drives and one Seagate 750 GB IDE drive. I have tried every combination of BIOS settings that I can muster, but nothing works. I used to be able to run Linux fine on my ASUS P5B, but this P5K has been a nightmare. Attempting to install any flavor of Linux basically makes my machine unbootable so that I have to rebuild the Windows boot loaders to get back online. 

Any ideas why I am having so many disk drive difficulties?

---

### Post by guenthert on 2008-09-27
> **jett said:**
> were you able to get Hardy to work on the P5Q? I'm seriously considering this board but I've read in other threads that they've had no luck in getting onboard sound and networking to work.

Ubuntu 8.04.1 runs here fine on an Asus P5Q-E with Intel 8500 dual core 2, including sound and both network adaptors. Better yet, network, sound and SATA controller were detected automatically. I was able to take the disk of my former PC (~5year old P4 based system) and put it into the new and Ubuntu worked (almost) right away (*). The only hurdle to overcome is that the Linux kernel (or rather the SATA driver) will detect disk drives only if the BIOS is configured so that the 'SATA Configuration' is set to 'Enhanced' and 'Configure SATA as' to 'AHCI', which is a bit cumbersome in a dual-boot PC, as Windows XP (up to SP2) wants that mode to be 'IDE' (which is the default). See [http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html](http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html)

The most recent version of R.I.P. Linux (6.7) which comes with the 2.6.26.5 kernel Linux finds the disk even in IDE mode, so there is a chance that in the next version of Ubuntu this BIOS reconfiguring isn't necessary anymore.

(*) the other inconvenience is not related to the MB: udev will find new devices (even if they were used in the old PC, just because meanwhile there is a new PCI id for the controller) and give them new names, i.e. eth2 and eth3 instead of eth0 and eth3, as well as dvd1 instead of dvd, etc. . You might want to edit /etc/udev/rules.d/70-persistent-cd.rules etc. to fix the names.

hth

---

