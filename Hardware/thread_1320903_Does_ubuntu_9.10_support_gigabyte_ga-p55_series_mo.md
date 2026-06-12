---
title: "Does ubuntu 9.10 support gigabyte ga-p55 series motherboards"
date: 2009-11-09
forum: Hardware
---

### Post by Bryan.Smith on 2009-11-09
Does Unbuntu 9.10 support the new Gigabyte ga-p55 series motherboards (particularly the ga-p55-ud3 board).

I want to avoid purchasing new hardware only to discover that it does not *currently* work.  *(If it does not work now I assume problems will fixed some time in the future.)*

I can find nothing in the Unbutu hardware compatability/incompatability lists on this web site.

On Googling I can find a review which tests an Intel P55 motherboard with Ubuntu (turbo boost did not work with a beta version of 9.10) as well as a separate user report that (Sata2, network, audio, cpu stepping, fan speed works with ga-p55-ud3 / Debian (2.6.30).

Has anyone successfully used the ga-p55-ud3 with Ubuntu?  Could different BIOS versions be expected to cause problems?

---

### Post by leonardo.anchisi on 2009-11-27
My Gigabyte ga-p55-ud4 is fully supported by Ubuntu 9.10.

The only problem I had was that  it didn't detect my SATA DVD RW. I solved it setting the SATA to AHCI mode in BIOS.

---

### Post by Bryan.Smith on 2009-12-13
Thank you for your response.

I have built a system based on the GA-P55-UD3 motherboard and the Radeon hd 5750 video card.  No major problems except that I had to download the video drivers from the ATI site.  Use of the Video drivers in the Ubuntu registry resulted in a "Not supported" watermark visible in the bottom right corner of the screen as well as a strange affect when using 1920 * 1080 resolution.  There was waht I call a "paling" effect (as in fence palings) where the display split into vertical rectangles with a gap between the rectangles.  The right hand portion of the screen was off screen and could not be accessed.

I have tried hibernating once.  After restoring I noticed a strange watermark effect on the bottom right corner of the screen.

---

### Post by FreeLander on 2009-12-16
Hi Bryan.

I have same motherboard + i750 procesor + Ubuntu 9.10. - 2.6.31-16-generic.Last few days im trying to find problem with hardware monitoring ls-sensors.Found shoud be IT8720 chip handling that informations (temps,fan speed,volages)..on [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)  seems it's supported chip,but ls-sensors cant find it!.So Im stuck at no informations on CPU temp and voltages + fan rpms

Anyone know how to overcome this problem with p55 motherboard + Ubuntu 9.10 combination ???

---

### Post by Bryan.Smith on 2009-12-18
After installing the lm-sensors and sensors-applet package I modified the file/etc/init.d/lm-sensors by hand.   I backed the lm-sensors file first and then used the vi editor (I am an experienced programmer) to add the line highlighted below in red.  ([FONT=System]gedit[/FONT] will work just as well as [FONT=System]vi[/FONT].)  Because the file is owned by root you will need to use sudo to gain root privileges.

[FONT=Courier New][SIZE=2]  start)
        log_begin_msg "Setting sensors limits"
[/SIZE][/FONT][FONT=Courier New][SIZE=2][COLOR=Red]**        modprobe it87**[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=2]
        if [ "$VERBOSE" = "no" ]; then
                /usr/bin/sensors -s 1> /dev/null 2> /dev/null
                /usr/bin/sensors 1> /dev/null 2> /dev/null
        else
                /usr/bin/sensors -s
                /usr/bin/sensors > /dev/null
        fi
        log_end_msg $?
        ;;[/SIZE][/FONT]

The hint of what do do is contained in the following output of the sensors-detect script.

[FONT=Courier New][SIZE=2]#----cut here----
# Chip drivers
modprobe it87
/usr/bin/sensors -s
#----cut here----[/SIZE][/FONT]

I gather from Googling that the modprobe command is used to add the it87 module to the kernel.

After you have done this and rebooted simply right click on the panel,  select "Add to Pannel", and choose "Hardware Sensors Monitor"

---

### Post by FreeLander on 2009-12-28
Hi again Brian

Well You save me lot of time !! Thanks !  Solved in 5 mins..Now i dont know wich
sensor is 'describe'lebels components (I have three working) proc 0..2 ?  I have tryed with Everest sw in Win7..there is all described by sensor components..

Any help ?

[http://foto2.inbox.lv/miran/Ubuntu/Everest-1.png](http://foto2.inbox.lv/miran/Ubuntu/Everest-1.png)   link Everest

[http://foto2.inbox.lv/miran/Ubuntu/lm-sensors.png](http://foto2.inbox.lv/miran/Ubuntu/lm-sensors.png)  link lm-sensor

good luck, Miran

---

### Post by magicmax0 on 2010-01-25
Hey guys
I have the UD3 and i5-750(@4Ghz) also. Thanks alot for the tip Brian. But im just curious, why does it only show 3 temps, shouldn't there be 4, one being for each core? Also, i see a difference as much as 10C between the core temps, is this possible?

---

### Post by magicmax0 on 2010-01-25
Actually, i noticed when putting my CPU under load, only temp3 seems to rise in temperature reading, im assuming that the other two are system temps (NB and case temp). Therefore temp3 is most likely an average temp over all 4 cores. Correct me if im wrong :P.

Edit: As for the general support of this platform, im currently running 9.10 and everything seems to work fine, besides the sensor issue which seems to have an easy fix, thanks to Bryan. Turbo boost also did not seem to work for me, although the CPU was scaling down and up as expected (power saving features work). However, i don't really care much for those, as i quickly disabled them, since i was planning on overclocking it to at least 4Ghz, which was remarkably easy to do.

---

### Post by GameManK on 2010-02-06
I just got a Gigabyte GA-P55-UD3L with a Core i7 860.  Kubuntu hangs completely partway into booting -- I've tried an existing 64-bit Karmic installation, a Karmic 32-bit CD and a Lucid 64-bit CD.  Did any of you have to tweak anything to get it to work on your board?

**Update**: it appears this was due to my wireless card, I removed it and successfully booted the Lucid CD.

---

### Post by magicmax0 on 2010-02-06
I did nothing beyond BIOS defaults, but i have the i5-750, as do the others i think. The i7-860 should be fine though, all its got the i5 doesn't is hyper-threading, which i dont think is supported yet. I don't see how that would cause it to hang though, you can try to disable it in BIOS i guess. Also disable advanced CPU options like turbo boost, but again, even left on, these should not cause the system to hang, they simply wont work in ubuntu. Im using the 32bit right now btw, haven't actually tried a 64bit yet. 

Have you had any luck loading any other OS on it yet? Maybe its something more serious, possibly faulty memory, make sure to do a full memtest. And load fail safe defaults in BIOS.

---

### Post by GameManK on 2010-02-07
Thanks for the suggestions, but looks like this is due to my PCI wireless card.  I've tried reinstalling it, and I've even tried another one of the same model (Netgear WG511t) and still Linux hangs shortly into booting when I have the card installed.  I don't really have another OS to try, though maybe I could try a different distribution.  I've used these cards in multiple systems before without any problems.

---

### Post by magicmax0 on 2010-02-07
Hmm, maybe try an older version of Ubuntu, 8.04 or 9.04. Or another distro if you want. I've had bad luck getting wireless working myself in any distro, ubuntu has been the easiest for me to get wireless working though, but its a bit of hit and miss with which wifi adapters work or not. My Dell XPS laptop wireless works perfect out of the box, but my Acer Aspire One is nothing but problems. Good luck with wifi :P. At least your system can install the OS fine without it installed, so the P55+i7-860 platform is not the problem.

---

