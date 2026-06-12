---
title: "Buying A Linux Compatible Laptop"
date: 2008-07-15
forum: Hardware
---

### Post by ankursethi on 2008-07-15
I've been thinking of getting a nice laptop next month. I'll obviously be using Ubuntu or some other Linux distro (probably run in CLI only mode since it will be a coding-only laptop).

Which laptop out there works best with Linux systems? Since I'm in India, I can't get a System 76 laptop here. But I do have the option of getting most big name laptops (Lenovo, Sony, Dell, blah).

I'm thinking of getting either an Acer laptop (most of them are dirt cheap, and I have the option of not buying Vista) or Dell (since I can customize it to my heart's content online). With Dell I have to pay the Microsoft tax (Vista, about Rs.7000), and a friend discouraged me from buying Acer (he claims it uses cheap, low quality hardware).

I'm leaning more towards the Acer system. It's so cheap that I can give it away to someone after using it throughout college and get a better system later on. But Dell has the brand image.

What now?

PS: Good Linux support is of paramount importance to me. And I only want to code on my laptop. I have an above average PC for gaming.

---

### Post by Dark_Stang on 2008-07-15
> **ankursethi said:**
> I'm thinking of getting either an Acer laptop (most of them are dirt cheap, and I have the option of not buying Vista) or Dell (since I can customize it to my heart's content online). With Dell I have to pay the Microsoft tax (Vista, about Rs.7000), and a friend discouraged me from buying Acer (he claims it uses cheap, low quality hardware).
Don't listen to your friend, Acer's are fine. Acer owns gateway for crying out loud, most people just don't know it. If you are going with an Acer laptop stay away from SiS graphics cards. And with any laptop you buy always research the hardware first to make sure it will be compatible. When you think you've found something you like post a link to it and we can tell you if it looks friendly or not.

---

### Post by sdennie on 2008-07-15
I've not used an Acer but, I can highly recommend Dell laptops.  The ones that come pre-configured with Ubuntu have fantastic support and I would imagine most of their other new laptops have about the same support (even if you can't get Ubuntu pre-configured ones in India, you can check to see which models they are and buy the Vista version).  Dell has wikis for fixing common problems for their hardware and even has an apt repository for BIOS updates so you can get them with your normal software updates.  

Regardless of what laptop you get, I would recommend sticking with intel wireless and graphics if possible.  They work out of the box and are the least hassle.

---

### Post by jespdj on 2008-07-15
Brands to avoid: Broadcom wireless chips, ATI videocards.

Brands that are OK: Intel wireless chips, Intel and nVidia videocards.

---

### Post by tamoneya on 2008-07-15
My vote is for lenovo.  My T61 works flawlessly with linux.

---

### Post by timcredible on 2008-07-15
my dell vostro 1000 works fine with ubuntu (although i haven't tried to get the modem to work).  it was $500US shipped, and has:

2gb ram
120gb drive
15.4" screen (1280x800)
ati 1150 graphics
4 usb ports
SD card reader
802.11b/g wireless

i had to boot the ubuntu cd in safe graphics mode and then install the restricted drivers via the menu, and i had to use ndiswrapper on the wireless card (it's a broadcom card, i just pointed the ndiswrapper application to the bcmwl5.inf file on the windows partition, rebooted, and wireless worked).

---

### Post by Odrodzona-Sarmacja on 2008-07-15
ASUS
I read few articles here from people using ASUS laptops and they suppose to work just great. Right now I am thinking of buying it unless the ASUS hardware I ordered will also be freezing my Xubuntu.

DELL
It is correct they sport Ubuntu, but then they collaborate with RIAA&MPAA and disable sound catching in their devices and do other such scum tricks. They also make it very expensive for folks to enable these devices again.

ACER
Cheapest, but never windows-OS-less. Also people with Acer laptops complain the most here for all of kind of reasons. I wouldn't go for that one.

ASUS EEE +linux
Suppose to be the greatest with Linux, but then they put part of main OS on BIOS chip and you can't upgrade it with new versions, or even remove them if you consider some part of it as a parasite&bloatware applications stealing your CPU and other resources.

Anyone know about other laptops?

---

### Post by stchman on 2008-07-15
> **ankursethi said:**
> I've been thinking of getting a nice laptop next month. I'll obviously be using Ubuntu or some other Linux distro (probably run in CLI only mode since it will be a coding-only laptop).

Which laptop out there works best with Linux systems? Since I'm in India, I can't get a System 76 laptop here. But I do have the option of getting most big name laptops (Lenovo, Sony, Dell, blah).

I'm thinking of getting either an Acer laptop (most of them are dirt cheap, and I have the option of not buying Vista) or Dell (since I can customize it to my heart's content online). With Dell I have to pay the Microsoft tax (Vista, about Rs.7000), and a friend discouraged me from buying Acer (he claims it uses cheap, low quality hardware).

I'm leaning more towards the Acer system. It's so cheap that I can give it away to someone after using it throughout college and get a better system later on. But Dell has the brand image.

What now?

PS: Good Linux support is of paramount importance to me. And I only want to code on my laptop. I have an above average PC for gaming.

I have the Toshiba A205-S5859 and EVERYTHING worked OOB with Hardy Heron.  Wireless, webcam, meadis slot (SD only), sound with headphone sense, X3100 video with Compiz.

I don't know if that model is available in India, but it works.

---

### Post by ankursethi on 2008-07-16
After reading this, I suppose Dell would be a better choice. It still comes with Vista, for which I'll have to pay an extra Rs.7000, but anything for good hardware support.

Another question: Dell's website list's "Dell's Wireless" as the wireless network hardware. Is this some kind of in-house hardware from Dell or does it use licensed hardware from some other company? Will this give me any troubles?

There seems to be an option between a 6 cell and a 9 cell battery. Does the 9 cell have any visible benefits?

Thanks guys :)

---

### Post by timcredible on 2008-07-16
dell uses many different wireless cards, none of them built by dell.  dell, hp, compaq, etc. don't actually build anything, except maybe the case, they just put other company's stuff together (intel, amd, ati, nvidia, seagate, etc.).  anyway, in case this helps, here's the details on what i have.  the battery lasts about 3 hours with monitor and wireless on the whole time:
```

-- Vostro 1000 --
-- AMD AthlonTM 64 X2 Dual-Core processor TK-57 (1.9GHz/256KB)
-- [223-5529]
-----------------------
-- LCD Panel --
-- 15.4 inch Wide Screen XGA LCD Display with TrueLife
-- [320-5883]
-----------------------
-- Memory --
-- 2GB Shared Dual Channel DDR2 SDRAM at 533MHZ, 2 Dimm
-- [311-7344]
-----------------------
-- Video Card --
-- ATI Radeon®  Xpress 1150 256MB HyperMemory&#33922;  (integrated)
-- [320-5631]
-----------------------
-- Hard Drive --
-- 120GB 5400RPM  Hard Drive
-- [341-4971]
-----------------------
-- Operating System --
-- Genuine Windows® XP Home Edition
-- [420-7163]
-- [420-7291]
-- [420-7658]
-----------------------
-- Adobe Software --
-- Adobe® Acrobat® Reader
-- [410-1100]
-----------------------
-- Optical Drive --
-- 8X DVD+/-RW with double-layer DVD+R write capability, Cyberlink Power DVD
-- [313-5390]
-----------------------
-- Sound Card --
-- Integrated Audio
-- [313-5383]
-----------------------
-- Wireless Cards --
-- Dell Wireless 1395 802.11g Wi-Fi Internal Card
-- [430-2733]
-----------------------
-- Productivity Software --
-- Microsoft® Works 9. Does NOT Include MS Word
-- [420-8046]
-----------------------
-- Anti-Virus/Security Suite (Pre-Installed) --
-- No Pre-installed Anti-Virus/Security Software
-- [410-0982]
-----------------------
-- Primary Battery --
-- 53 WHr 6-cell Lithium Ion Primary Battery
-- [312-0569]

```

---

### Post by overdrank on 2008-07-16
> **Odrodzona-Sarmacja said:**
> ASUS
I read few articles here from people using ASUS laptops and they suppose to work just great. Right now I am thinking of buying it unless the ASUS hardware I ordered will also be freezing my Xubuntu.

DELL
It is correct they sport Ubuntu, but then they collaborate with RIAA&MPAA and disable sound catching in their devices and do other such scum tricks. They also make it very expensive for folks to enable these devices again.

ACER
Cheapest, but never windows-OS-less. Also people with Acer laptops complain the most here for all of kind of reasons. I wouldn't go for that one.

ASUS EEE +linux
Suppose to be the greatest with Linux, but then they put part of main OS on BIOS chip and you can't upgrade it with new versions, or even remove them if you consider some part of it as a parasite&bloatware applications stealing your CPU and other resources.

Anyone know about other laptops?

Acer works great here. :KS and will by another in the future. :)

---

### Post by heartlessdevil on 2008-07-16
I am in the same boat trying to get a laptop that supports Ubuntu.
I have two options:
1. ThinkPad R61 (Price:$565)
Processor -- Intel Core&#8482; 2 Duo T7100 (1.8GHz 800MHz 2MBL2)
Operating System -- Genuine Windows Vista Business
Screen -- 14.1 WXGA TFT
Memory -- 1 GB PC2-5300 DDR2 SDRAM 667MHz SODIMM Memory
Hard Drive -- 80GB Hard Disk Drive, 5400rpm
Optical Storage -- CD-RW/DVD-ROM Combo 24X/24X/24X/8X Max, Ultrabay Enhanced
Wireless -- ThinkPad 11a/b/g Wi-Fi wireless LAN Mini-PCIe
Warranty -- 1 Year
Battery -- 6 cell Li-Ion Battery
Features -- UltraNav (TrackPoint and TouchPad)
Bluetooth -- No
Video Card -- Intel X3100

2. Acer - Extensa Laptop with Intel® Celeron® Processor 550 
Model: EX5220-2516 (Price: $480+tax+ shipping=$524)

    *  Intel® Celeron® mobile processor 550 with 533MHz frontside bus, 1MB L2 cache and 2.0GHz processor speed
    * 1GB DDR2 memory for multitasking power
    * SuperMulti DVD±RW/CD-RW drive with double-layer support records up to 8.5GB of data or 4 hours of video using compatible DVD+R DL and DVD-R DL media; also supports DVD-RAM
    * 15.4" WXGA widescreen TFT-LCD display with CrystalBrite technology
    * 120GB SATA hard drive (5400 rpm)
    * Intel® Graphics Media Accelerator X3100 with Intel® Dynamic Video Memory Technology 4.0 and up to 358MB of shared video memory; Intel® High Definition audio; S-video out
    * 5-in-1 media reader supports Secure Digital, MultiMediaCard, Memory Stick, Memory Stick PRO and xD-Picture Card
    * IEEE 1394 (FireWire) interface and 4 high-speed USB 2.0 ports for fast digital video, audio and data transfer
    * Built-in wireless LAN (802.11b/g); 10/100/1000Base-T Ethernet with RJ-45 connector; V.92 modem
    * Weighs 6.3 lbs. and measures just 1.7" thin for portable power, lithium-ion battery and AC adapter


I have been searching online for installation feedback of ubuntu on both systems and have not found a solution where everyhing works. the surprising fact is Lenovo supports SUSE installation on R61 and that's $100 extra. 
Also some notes mentioned that the mic and wireless did not work, which is something I need for Skype.
Can someone advise ??

HD

---

### Post by heartlessdevil on 2008-07-17
> **heartlessdevil said:**
> I am in the same boat trying to get a laptop that supports Ubuntu.
I have two options:
1. ThinkPad R61 (Price:$565)
Processor -- Intel Core&#8482; 2 Duo T7100 (1.8GHz 800MHz 2MBL2)
Operating System -- Genuine Windows Vista Business
Screen -- 14.1 WXGA TFT
Memory -- 1 GB PC2-5300 DDR2 SDRAM 667MHz SODIMM Memory
Hard Drive -- 80GB Hard Disk Drive, 5400rpm
Optical Storage -- CD-RW/DVD-ROM Combo 24X/24X/24X/8X Max, Ultrabay Enhanced
Wireless -- ThinkPad 11a/b/g Wi-Fi wireless LAN Mini-PCIe
Warranty -- 1 Year
Battery -- 6 cell Li-Ion Battery
Features -- UltraNav (TrackPoint and TouchPad)
Bluetooth -- No
Video Card -- Intel X3100

2. Acer - Extensa Laptop with Intel® Celeron® Processor 550 
Model: EX5220-2516 (Price: $480+tax+ shipping=$524)

    *  Intel® Celeron® mobile processor 550 with 533MHz frontside bus, 1MB L2 cache and 2.0GHz processor speed
    * 1GB DDR2 memory for multitasking power
    * SuperMulti DVD±RW/CD-RW drive with double-layer support records up to 8.5GB of data or 4 hours of video using compatible DVD+R DL and DVD-R DL media; also supports DVD-RAM
    * 15.4" WXGA widescreen TFT-LCD display with CrystalBrite technology
    * 120GB SATA hard drive (5400 rpm)
    * Intel® Graphics Media Accelerator X3100 with Intel® Dynamic Video Memory Technology 4.0 and up to 358MB of shared video memory; Intel® High Definition audio; S-video out
    * 5-in-1 media reader supports Secure Digital, MultiMediaCard, Memory Stick, Memory Stick PRO and xD-Picture Card
    * IEEE 1394 (FireWire) interface and 4 high-speed USB 2.0 ports for fast digital video, audio and data transfer
    * Built-in wireless LAN (802.11b/g); 10/100/1000Base-T Ethernet with RJ-45 connector; V.92 modem
    * Weighs 6.3 lbs. and measures just 1.7" thin for portable power, lithium-ion battery and AC adapter


I have been searching online for installation feedback of ubuntu on both systems and have not found a solution where everyhing works. the surprising fact is Lenovo supports SUSE installation on R61 and that's $100 extra. 
Also some notes mentioned that the mic and wireless did not work, which is something I need for Skype.
Can someone advise ??

HD
can someone advise on IBM R61 versus Acer ??

---

### Post by 71CH on 2008-07-17
I have the R61.  I highly recommend it.

---

### Post by Killer_B on 2008-07-17
The Thinkpad is more certain to be supported under Linux; The Acer, less certain.

I'm still using an old Thinkpad X23 with 8.04LTS...Can be a touch slow, but that's more because I'm using Gnome, which is a bit heavy for hardware as old as what I'm using on it. One of these days I'll be bothered to experiment with a more efficient WM like IceWM or Fluxbox.

---

### Post by sTpny on 2008-07-22
huh, why not just take your live cd with you when you go shopping... start at the cheap end and stop when everything you need works... just a suggestion.

---

### Post by canoe529 on 2008-07-22
I just bought a lenovo T61. I am very happy with it using kubuntu. The 3D acceleration still isn't quite as fast as I would like, but Intel has released the drivers so one of the things I plan on doing is compiling & using them. I only need that for messing around with games, though, and I'm not a huge gamer, so it is not a high priority.

I went with Lenovo because they had the best price and features unavailable from Dell. I could not get a laptop with 4 gigabytes of RAM and a 7200 RPM 200 gigabyte drive from Dell.

---

### Post by Joeb454 on 2008-07-22
I hear thinkpads work well with Ubuntu (though they're quite dear).

Maybe look into Dell's Ubuntu offerings?

---

### Post by kleo skywalker on 2008-08-19
Ankur, Dell India also has a couple of Vostro models that come with FreeDOS. You can find all details on their website, and you can just call the toll-free number if you need to customize it or get the exact cost.

Lenovo has a few DOS models too, some of them starting out quite cheap. No points to their website for being informative, though. You'd have to call their toll-free number and ask them to email all the information you need.

Compaq and Acer are some of the other brands that have at least one model that comes with DOS only. If there are any big electronics stores in your city (such as Croma), you might find it useful to call them and ask them what non-Windows laptops they have.

---

### Post by krayton8 on 2008-08-19
In my experience, the brands of the internal components are more important. Check the specs on a model that you're interested in. I've always had good experience with Nvidia for graphics or having Intel chipsets all around.

---

### Post by Rumel on 2008-08-19
Get a dell. They have laptops that work perfectly with Ubuntu since they are designed for it. Also then you get DVD support right out of the box. [Dell Ubuntu Page]("http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&dgc=IR&cid=11973&lid=471885")

---

