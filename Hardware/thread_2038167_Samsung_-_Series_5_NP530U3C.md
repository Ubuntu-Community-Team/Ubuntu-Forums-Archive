---
title: "Samsung - Series 5 NP530U3C"
date: 2012-08-06
forum: Hardware
---

### Post by IcePik on 2012-08-06
I am looking at the Samsung Series 7 NP700Z5C as a replacement for my current laptop.

[http://www.samsung.com/us/computer/laptops/NP530U3C-A01US](http://www.samsung.com/us/computer/laptops/NP530U3C-A01US)

Some of the specs are as below:
Intel® Core™ i5-3317U Processor
4GB DDR3 Memory
500 GB  HDD with ExpressCache™ Technology, 24 GB
Intel® HD Graphics 4000

I would like to know if anyone here has this laptop and whether everything works ok, if not what did you need to tweak to get things started?

I intend to take this one to college so dose anyone know how long the battery will last for(i'm looking for a minimum of 3 hours under load)?

Further can I wipe windows off the express cache and use it as a /boot partition?

Love to hear from anyone who has one of these laptops and thanks in advance to anyone who can help me.

---

### Post by tk83 on 2012-08-08
I bought a Samsung NP530U3C-A01DE a few days ago. Most stuff works out of the box but there are a couple of small problems. 

I'm running Ubuntu 12.04 and the brightness controls don't work on the latest kernel. They did however work on the original kernel that came 12.04 (i.e. before updates) so there is some hope here. This has an affect on battery life.

I haven't tried bluetooth yet either but everything else seems to work - card reader, wifi, ethernet, suspend, HDMI video and audio out, touchpad, USB devices and so on.

---

### Post by testblageneric on 2012-08-08
I'm using this notebook right now and it's working perfectly fine with Windows and different Linux distros.

The battery lasts about 4 hours when using it for uni-stuff. (Coding, Browsing, etc..)

The problem i have encountered ([http://ubuntuforums.org/showthread.php?t=2039263](http://ubuntuforums.org/showthread.php?t=2039263)) is that my expresscache is broken (after 2 months of use), as the BIOS can't recognize it anymore. Also it can't be replaced as it is soldered directly to the mainboard...

On the other hand i had a huge amount of write processes to the drive (removed the expresscache and test-installed some distros and tried windows 7 on it) which definitely decreased the life time a lot. But failing so fast, i think i'll call the support tomorrow...

Also you can't boot directly from the SSD, so you need the boot partition on your regular harddrive! (Maybe a BIOS update helps but im not sure...)

---

### Post by Eugenian on 2012-08-13
How is the video performance under Linux with the Core i5-3317u?  I am considering buying the same laptop, which I would use for (among other things) playing high-def videos on a 1080p monitor.  I wonder if the ULV processor is up to the task; I see its GPU runs at a lower clock frequency than the 35w version of Ivy Bridge.  I don't play games but I want something that will feel quick in web browsing and multitasking, and that will not choke on streaming hi-def video.

I really wanted to buy an AMD Trinity laptop (probably the 14" Trinity version of the Samsung Series 5) for the better graphics, but I've read elsewhere about [problems getting Ubuntu 12.10 Alpha 2 to install/run]("http://askubuntu.com/questions/166538/problems-with-ubuntu-and-amd-a10-4655m-apu") with a Trinity chip. Maybe this will be fixed in the stable release of 12.10, but I'm not sure I want to wait to see if that's the case.

---

