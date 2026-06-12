---
title: "HP Pavilion P6130f"
date: 2009-09-07
forum: Hardware
---

### Post by jasonditz on 2009-09-07
I'm looking to get a new desktop and right now I'm leaning toward the [P6130F]("http://www.amazon.com/HP-Pavilion-P6130F-Desktop-PC/dp/B002BWQA4K"). It sure looks like everything on it should be supported in 9.04 but could someone else take a quick look and let me know if there's any potential trouble spots I might be missing?

---

### Post by jasonditz on 2009-09-11
So I found out the motherboard of this system, the Violet-GL8E is the same one that's used in HP's NC797AA system (a low-end Linux desktop sold in China). Assuming this meant driver support wouldn't be an issue I went ahead and ordered, and it arrived yesterday. I figured I'd share the results in case anyone else is looking for a nice cheap robust desktop. 

About the system:

AMD Phenom X4 9750 CPU 
8 GB of DDR2
750 GB hard drive (originally formatted as 720 GB FAT32 and 30 GB reinstall partition)
16X DL-DVD-RAM drive
Nvidia GForce 9100 
Agere FW323 Firewire
AR928X Wireless PCI-E (with external antenna)

Originally came with Vista Home Premium 64-bit.

What I did to it:

Step 1. Booting up I pressed F10 to avoid booting into Vista. Inserted the same CD-R of 9.04 (AMD64) that I used on my Compaq A932nr a few weeks ago. About 45 minutes of installation and both Vista and its reinstall partition are gone, and the system is ready to boot in Jaunty.

Step 2. Scraped off the Vista sticker that was on the front of the case. No need to have that thing uglying up a desktop, especially when a chrome penguin sticker is en-route. 

Step 3. On booting I notice something unsettling: the display is in 1280x720 resolution and has no clue what my monitor (Viewsonic VG2030wm) supports. Ubuntu, however, immediately pops up a little warning that I'm not using the proprietary drivers from Nvidia, and asks if I want to. I say yes but then another notice pops up suggesting about 100 MB worth of patches, so I hold off rebooting until that's done. System shuts down.

Step 4. The system boots up in 1680x1050 resolution, which is the max the VG2030wm supports. It seems to happily recognize all the hardware, including the Atheros Wifi card (though I have no intention of using that since the tower is right by the router). I have a fully functional quad core AMD64 Ubuntu system with 8 GB of Ram for $550 shipped. 

Notes:

* Some of the programs had a nasty habit of rendering the system unresponsive. 6 hard reboots in 30 minutes while I'm trying to work has me in panic mode. On a hunch I go to System>Preferences>Appearance and turn off Visual Effects. The system hasn't crashed again since.

* Installed the bleeding-edge wine version (1.1.29) and installed World of Warcraft, which was previously an unmitigated disaster on my laptop because of the Intel GMA965 GPU. Mercifully, after about 3 hours of downloading (over 7 GB of data and patches which Charter will no doubt complain about) wow chugs to life, happy with all the default settings and running at a steady 45-50 fps in Windowed mode, with some fancy effects I'd never even seen on my old MacMini. It's not only playable but dramatically superior to the MacMini (with its paltry 1 GB of ram and GMA650) in every way. 

* Also installed EHM 07 in wine, and OOTP 10 (GTK Linux version), both run fine, and a lot faster than their Mac counterparts. 

* Also also installed all the restricted crap so that Handbrake would run. Handbrake took approximately 5 hours to rip a 95 minute movie on the MacMini. It took about 50 minutes on the P6130f. CPU usage never topped 70% on any of the cores while it was running, I suspect this means something else (DVD drive speed?) was the lagging factor. 

* Noticed something: HFS+ drives really don't play nice with Ubuntu. I backed up my old ~/ directory on my MacMini to an external drive with HFS+ on it, and when trying to reclaim some of my iTunes MP3s I get a bunch of permission crap. Finally have to "sudo -s" my way in and grab a few songs one at a time. This seems to work fine, though I then had to go to the directory I put them in and chmod them to something usable (I put them in Music then sudo chmod 6666 ~/Music/*).

---

