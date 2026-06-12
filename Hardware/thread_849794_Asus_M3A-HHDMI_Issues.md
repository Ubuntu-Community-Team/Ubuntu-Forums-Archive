---
title: "Asus M3A-H/HDMI Issues"
date: 2008-07-04
forum: Hardware
---

### Post by dcollamore on 2008-07-04
I'm curious if anyone else is having the same problems I am with the Asus M3A-H/HDMI Motherboard.  Here's the relevent hardware:

Asus M3A-H/HDMI Motherboard
4GB Kingston DDR-2 800 Memory (4 1GB Modules)
3 Seagate 160GB SATA HDDs (2 in BIOS Raid-0 for Windows XP, 1 for Linux)
AMD Athlon X2 4600+ Processor

I can install 8.04 64-bit, but the machine 'cycles' immediately after selection in GRUB; soft reboot.  Interestingly enough, this also happens with Fedora 9 64-bit.  I haven't turned up any information on this error from google or in the forums, but I've never seen an issue like this short of hardware error before.  As far as troubleshooting, I've removed the two drives in the RAID from the scenario completely, I've run MEMTEST on the RAM for over 24 hours; no issue there.  The CPU is under 100 degrees F, as is the motherboard.  All three hard drives pass Seagate diagnostic check.  The power supply is a brand new 430W Thermaltake; more than sufficient for this system.  Board, processor, RAM, and P/S are all brand new and out of the package less then three days.  Windows XP boots and runs like a champ and stays stable through a long PRIME95 torture test.

I'm stumped.  Anyone have any ideas?

---

### Post by starcannon on 2008-07-04
If this is your first Linux/Ubuntu install I'd recommend the 32bit version over the 64bit version, if your using <=3.5gb of ram you are likely to not know the difference. If you are using >3.5gb of ram you will only see about the first 3.5gb of ram.

64bit is coming along nicely, but its not quite done yet in my opinion. I have 4x 64bit computers and I run 32bit on all of them.

If you really want to run 64bit be sure to check out this forum as well [http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

---

### Post by dcollamore on 2008-07-05
Thanks for the input, though this is far from my first install.  I started with Redhat 5.2 back in the days when it was on the shelf in Walmart (1998?  maybe 1999?), and Ubuntu specifically since Breezy.  I currently have 8.04 32-bit running on a laptop and one server, and 64-bit running on two others.  

32-bit doesn't like to play with this hardware either; I suspect a problem with kernel support, as it is a relatively new chipset (the 780G).  I was hoping for confirmation from others with similar hardware, or a possible workaround.  I'm really stuck here, as I can't even get any troubleshooting information.  The 32-bit and 64-bit live environment works fine, but once I run through the install, the system either cycles (64-bit) or hard-locks (32-bit) without giving any indication whatsoever what the problem is.

---

### Post by amoniak on 2008-07-06
hello

I also just installed Hardy 64bit on that ASUS M3A-H/HDMI Board. Worked fine.

Now I am wondering if the onboard graphics chip works fine, because when I play videos it sometimes flickers - seems really slow and crappy playback (the opposite what I expected from my new board) :(

I installed the latest ATI Catalyst drivers following this howto: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

any suggestions / hints?



my specs
ASUS M3A-H/HDMI - BIOS 0604
2x2GB AENEON RAM
ATHLON 64 X2 5200

fresh install of Ubuntu Hardy 8.04.1

---

### Post by dcollamore on 2008-07-07
Amoniak - 

Are you by any chance using the BIOS raid on your board?  My next step (haven't had a chance to try it yet) is going to be shifting the SATA mode first from RAID to AHCI, then to IDE emulation to see if that resolves the issues I'm having; this won't really be a solution, as my Windows install lives on a striped RAID that I need to keep intact, but it will at least give some troubleshooting information.

---

### Post by wu-stix on 2008-07-08
I have just installed ubuntu 8.04 on my asus m3a78-emh hdmi with 2.5 ghz phenom and 3gb of ram and 200 gb hard drive and the graphics are working fine but the sound wont come through the hdmi cable.  Except yesterday the graphics reset to 648x400 and I got sound but today it is back to normal.  Besides the sound problem I have also not got the hdmi to output in 1080p and java doesn't seem to work in firefox.  This is my first time trying linux (boycotting microsoft, and I dont like apple either) so I have a lot to learn.

I know sometimes the flickering is caused by the refresh rate not matching the monitors.

---

### Post by Odrodzona-Sarmacja on 2008-07-09
You may want to check first
[http://vip.asus.com/forum/topic.aspx?board_id=1&SLanguage=en-us](http://vip.asus.com/forum/topic.aspx?board_id=1&SLanguage=en-us)
,as these issues just maybe are not exactly Ubuntu bound.

---

