---
title: "UBUNTU on Acer Aspire 2003 WLMI, almost OK with hoary"
date: 2005-02-28
forum: Hardware &amp; Laptops
---

### Post by stcoulon on 2005-02-28
Hi all,

looking for a simple Linux distribution to install on my Acer Aspire 2003 WLMI got me to give UBUNTU a try.

First hardware configuration:

- Centrino architecture
- Pentium M 1,6Mhz 1Mb cache
- 512 Mb RAM (2x256, should upgrade in the evenning to 1x256+1x512, hope to get to 2x512 as soon as I have 90€ to get a second 512Mb)
- Video is ATI Radeon 9200, 128Mb DDR
- Sound is Intel chipset
- Ethernet realtek, WIFI 802.11G 2200 Intel (was previously 802.11B 2100, and upgraded the mini PCI board
- USB2, firewire
- HD 60GB, ata 100
- Matshita CD/DVD writer

Previously I tried KANOTIX, both Bug Hunter X-2004 and 01-2005, and got some success with them. The system came up, everything was almost working, BUT, I had a strange problem with KLAPTOP (Kanotix is KDE) battery monitoring (only annoying). I also found that their was too many installed software in it (I'm looking for a simple distribution to start with), and I wasn't able to get any suspend option to work with KANOTIX (which makes use of suspend 2 patch). Kanotix is certainly a great Linux distro, but I should try some others, so let's go to UBUNTU.

I had the opportunity to try both UBUNTU warty and hoary on VMWARE on my office laptop, and decided to give hoary a try. That's done now, and here is the report.

- First, I have read reports of problem with partitionning this kind of acer laptop and loosing the acer aspire multimedia software (basically, a small linux partition dedicated to multimedia applications, and which can bu run outside windows, from dedidated keys on the front panel of the laptop). No issue here, I used to create using qtparted some free space at the end of my NTFS XP main partition, just before the acer aspire partition, and created an extended partition in it. Then logical drives were created into it for root, swap, ... This, at least for me, has preserved the acer aspire mulimedia functionality.

- Then, after partitioning for UBUNTU (10Gb globally allocated for Linux) I was able to install seamlessly, except that I had to delay my network configuration. I tried once to configure my wep key (hexadecimal string, I had to copy on a paper sheet ...) but the installer couldn't get the network up, so I delayed the installation.

- The two steps installation process got me to an up and running UBUNTU system, where I was able to configure my wireless network card very easily.

- Sound is OK, graphic is OK (with 1280x800 display and standard X radeon server, not the ATI one I had to install on Kanotix). Synaptics touchpad and USB mouse OK. USB2 is OK to access my external USB2/Firewire drive (had no opportunity to test the firewire connectivity, though). Keyboard OK.

- Didn't check infrared.

- I currently have some configuration issue with the NTP software I think, but I'll look later to this as it is not important to me.

- I swapped to the 686 kernel and modules, everything's OK.

- I soon discovered that my wireless 2200 board would deconnect from time to time. Recovering from this situation would require at least to re-initialize the driver module (rmmod+modprobe again). I installed the latest Intel driver (1.01, UBUNTU came with 0.19, there was 0.21 and 1.0 inbetween). The firmware for 2200 was OK in UBUNTU. It appears to be at least more stable now with the last driver, but I'm unsure that the problem is completely fixed. Under observation.

- I tried advanced power management with disk and mem suspend. UBUNTU uses suspend included in 2.6 kernel. Suspend to disk almost runs out of the box, except that it appears that the Intel 2200, which is unloaded before going to suspend, tries to load the firmware without UBUNTU's suffixes (something like 2.6.10-4.686 appended to Intel's original filenames). I simply unpacked Intel's original tarball in /lib/hotplug/firmware and the wireless lan is OK after returning from suspend. Maybe I should investigate more on that. Some glitches on the screen but after some time the display is OK.

- suspend to ram doesn't resume at all. The laptop goes quickly to suspend to ram state, then pressing a key, it seems that it wakes up, but will deadlock some where. I've seen some strange things in /etc/acpi/prepare.sh and resume.sh, but nothing that clears the problem.

This is currently my main issue with UBUNTU on Acer Aspire 2003wlmi.

I've found some information which could help in [http://www.doesi.gmxhome.de/linux/tm800s3/s3.html](http://www.doesi.gmxhome.de/linux/tm800s3/s3.html), I will try to follow this path. Obviously ram suspend is the main issue with alot of laptops and linux.

Anyway any help appreciated on this subject of course.

---

### Post by kaaloo on 2005-05-05
Thanks for sharing your experience here !  I have the same computer and am preparing to install.  I was wondering if you had found a solution to the suspend to RAM issue ?  Also, when you installed, did you change the way the disk is originally partitioned with the 8 G "DATA" partition ?  Thanks !

---

