---
title: "Lenovo T530"
date: 2012-07-06
forum: Hardware
---

### Post by jbblack on 2012-07-06
I searched for Lenovo T530 and only found two threads.  One was stating the person was picking the T530 because of the Trackpad, the other was talking about the nVidia video drivers.  All I want to know is if I will run into issues with this build as I don't know where to look for driver compatibilities/incompatibilities.

Before I copy-and-paste the build, I will be mostly using this as a mobile computing platform.  I currently have a desktop with these specs:

AMD Athlon II x3 435
4GB RAM
AMD 5570 HD video card
Win 7 x64
Ubuntu 12.04 (wubi)

My desktop runs mostly amateur radio applications.  For these, I have found either the same program or something comparable.  I play a couple of games - Diablo3, WoW, and SWTOR.  Those can stay on the desktop unless I'm traveling which I do infrequently.  I also publish a club newsletter using MS Publisher.  For MS Publisher, all I have found in Linux is too powerful.

As I said, a laptop will be a mobile computing platform for me.  Something I can take out of my "man cave" and put it on the dining room table.  Something I can take to the field when operating portable with my radios.  However, I also want something that will not be outdated in a year (hard to do, I know).  I would love a "Sputnik" Project Laptop from Dell.  Doesn't matter that I'm not a developer - I like that laptop.

Here's the build from Lenovo.  Any advice is welcome.

ThinkPad T530 - 1 Year Depot Warranty	
Processor:	Intel Core i5-3210M Processor (3M Cache, up to 3.10 GHz)	
Operating system:	Genuine Windows 7 Home Premium (64 bit)	
Operating system language:	Genuine Windows 7 Home Premium 64 - English	 
Display type:	15.6" HD+ (1600 x 900) LED Backlit AntiGlare Display, Mobile Broadband Ready	
System graphics:	Intel HD Graphics 4000	
Total memory:	8 GB PC3-12800 DDR3 (2 DIMM)	
Keyboard:	Keyboard Backlit - US English	
Pointing device:	UltraNav with Fingerprint Reader	
Camera:	No Camera, with Microphone	
Hard drive:	500GB Hard Disk Drive, 7200rpm	
Optical device:	DVD Recordable	
System expansion slots:	Express Card Slot & 4-in-1 Card Reader	
Battery:	6 Cell Li-Ion TWL 70+	
Power cord:	90W AC Adapter - US (2pin)	
Bluetooth:	Bluetooth 4.0 with Antenna	
Integrated WiFi wireless LAN adapters:	Intel Centrino Wireless-N 2200 (2x2 BGN)	
Integrated mobile broadband:	Mobile Broadband upgradable	
Language pack:	Publication - US English

Thanks,
Joel - W4JBB

---

### Post by sbarmeier on 2012-07-07
Sorry, I can only help you by populating this thread. It seems that the author of the last (6th) post [here]("http://ubuntuforums.org/showthread.php?t=2008824") seems to run the latest ubuntu on the T530 without too many problems. It would be nice to see some benchmarks, though, before investing in such a powerful machine...

---

### Post by jbblack on 2012-07-07
> **sbarmeier said:**
> Sorry, I can only help you by populating this thread. It seems that the author of the last (6th) post [here]("http://ubuntuforums.org/showthread.php?t=2008824") seems to run the latest ubuntu on the T530 without too many problems. It would be nice to see some benchmarks, though, before investing in such a powerful machine...

Yeah, tell me about it.  The Internet is mum on this one.  :)

I had looked at that thread previously, but it seemed vague to me.  I will post there and see if there might be an update.

Thanks,
Joel

---

### Post by vab3 on 2012-07-25
Joel,

I just ordered the T530.  I'll let you know how it goes. Feel free to ping me if you don't hear back in a couple of weeks. 

Vic

---

### Post by lalligood on 2012-07-25
I just got my new T530 last week. After trying the 12.04 Desktop 64-bit CD & seeing that everything worked--and I do mean everything--I installed it right over Windows...

Here are the specs of my T530:
Intel Core i5-3210M Processor (3M Cache, up to 3.10 GHz)
Genuine Windows 7 Home Premium (64 bit)
15.6" HD+ (1600 x 900) LED Backlit AntiGlare Display, Mobile Broadband Ready
Intel HD Graphics 4000
4 GB PC3-12800 DDR3 (1 DIMM)
Keyboard Backlit - US English
UltraNav without Fingerprint Reader
720p HD Camera with Microphone
320GB Hard Disk Drive, 7200rpm
DVD Recordable
Express Card Slot & 4-in-1 Card Reader & Bezel
6 Cell Li-Ion TWL 70+
90W AC Adapter - US (2pin)
Intel Centrino Advanced-N 6205 AGN
Mobile Broadband upgradable
Publication - US English

All of the <Fn> key combinations work (to turn on the backlit keyboard, adjust brightness, lock terminal, etc.). There are some simple settings in the Mouse control panel that enables multi-touch vertical & horizontal scrolling. Display was recognized at full 1600x900 resolution with no additional drivers to install (or fret over!). The webcam worked during the install & I installed guvcview (didn't try Cheese but I don't see why it wouldn't work either). Audio, USB 3.0, wireless & ethernet LAN all worked right away. Speaking of the wireless, it also worked when I was using the live CD! No lag in any of the videos (various .avi, .mp4, & .wmv formats in VLC) nor games (Minecraft & a few Humble Bundle games) I've played. Only problem I ran into with any game was I had to export a variable to get Minecraft to work in 64-bit). Otherwise, not a single problem.

If you or anyone has any questions about running Ubuntu on the T530, feel free to ask!

HTH,

--Lance

---

### Post by Mikeb85 on 2012-07-26
I'm getting a T530 with dual-core i7, Intel graphics, 1080p screen, most of the options, etc...  I'll definitely post a review when I get it, but it probably won't be here for 2-3 weeks.

---

### Post by cprofitt on 2012-08-02
Debating a T530 myself... anyone using the mSATA drive option with theirs?

---

### Post by Mikeb85 on 2012-08-03
Just got my T530.  So far so good, except I can't get the fingerprint reader working, nor can I adjust the screen brightness.  An openSUSE live CD can adjust screen brightness, but no fingerprint reader either...

---

### Post by vab3 on 2012-09-06
Lenovo Thinkpad T530 arrived. Intel i7-3720QM CPU (quad core). Running well with Ubuntu 12.04.1 64-bit.  

I added an SSD and 16G Ram (from Crucial) before installing and it went fine.   You do have to remove the keyboard to replace the  memory, but it is straightforward.  It has two memory slots, one is accessible from a hatch on the bottom, the other is under the keyboard. 

Before installing, I set the BIOS to use ONLY the integrated (Intel HD4000) graphics, which worked fine.  However, in the docking station, the integrated graphics didn't seem to be able to find the attached monitor.   So, I switched to ONLY discrete (nVidia) graphics and installed the nVidia drivers (nvidia-current is working fine).   I will set up auto-disper to recognize when it is attached or not.   Unless someone finds a solution, I'll probably just open the BIOS and change it back to integrated when I know I'll be traveling.  

I have the battery that bumps out the back.  It reported about 4 hours of run time when booted fully charged at the coffee shop. 

I had to attach speakers to the headphone jack on the laptop (not the docking station).  I'm still looking for a solution there. 

I ordered the optical drive bay that allows you to attach a second hard drive.  So far I used it to move data from my previous hard drive.  It saved me several hours.   My plan was to move the drive that came with the system into the bay, but it is a slim hard drive and will need some padding so it doesn't flop around.  Probably just a bump of foam on one end so as to allow the drive to dissipate heat.    I did see an issue somewhere that required a tweak to get the laptop to sleep properly without un-mounting the second drive.  (I'll post if I run across it again). 

I ordered the 95%-color-gamut monitor.  It looks great.  Not quite Mac quality, but very bright and colorful.  Mac uses IPS-switching monitors that don't change brightness when you tilt them.  This one changes brightness.   I look forward to tweaking some digital photos.

Most function keys seem to work.  I'm able to dim the screen, and adjust the volume. I can turn on the back-lit keyboard, but don't yet know how to turn on the "thinkLight".  

The touchpad worked cleanly right out of the box.  I haven't noticed my cursor jumping around unexpectedly like with the touchpad on my Dell.  

I'm running big hardware because I often run two virtual  machines.  For its size, the laptop is light and compact.  It is a shade  lighter than my Dell Latitude 6510 with similar configuration.   The 135W power supply is heavy. I haven't seen good information on whether the 90W will work with the quad core.  

Speed-wise,  my VMs are running quickly, and best of all the start and stop fast -- no doubt a result of the SSD. The  system itself boots up to a login prompt in 15 seconds.

---

### Post by lalligood on 2012-09-06
> **vab3 said:**
> but don't yet know how to turn on the "thinkLight".  

Keep pressing <Fn> + <Space>... First time turns on keyboard backlight low, second time keyboard backlight high, third time turns keyboard backlight off & turns thinkLight on. Fourth time turns all lights off again. ;)

HTH,

--L

---

### Post by cprofitt on 2012-09-06
I ended up chosing the System76 Gazelle Professional over the T530. I ended up getting the following specs: 

[LIST]
[*]Ubuntu 12.04 LTS 64 bit
[*]15.6" 1080p Full High Definition LED Backlit Display featuring 95% NTSC Color Gamut in Matte Finished Surface ( 1920 x 1080 )
[*]Intel HD Graphics 4000
[*]3rd Generation Intel Core i7-3720QM Processor ( 2.60GHz 6MB L3 Cache - 4 Cores plus Hyperthreading )
[*]16 GB Dual Channel DDR3 SDRAM at 1600MHz - 2 X 8 GB
[*]500 GB 7200rpm SATA Hybrid Hard Drive with 4 GB SSD
[*]United States Keyboard Layout
[*]8X DVD±R/RW/4X +DL Super-Multi Drive
[*]Intel Centrino Advanced-N 6235 - 802.11A/B/G/N Wireless LAN + Bluetooth Combo Module
[*]1 Yr. Ltd. Warranty and 1 Yr. Technical Support
[/LIST]
At a much lower cost than the T530 would have resulted in. The battery life is no where near what a T530 with the 9-cell battery would get though... but I rarely use the battery.

---

### Post by vab3 on 2012-09-24
The System76 has a good spec sheet.  I ordered the *T530* before I saw they had released the *Gazelle*.  Send me a note if you post your experience with it. 

A few more notes. --   If I'm running the nVidia graphics.  I'm unable to adjust the brightness.  Looks like this may be a bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1001337](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1001337)

When attached to the docking station, I was unable to activate my one external monitor unless I enabled the nVidia graphics in the BIOS. The monitor was using a DVI cable.  Just today I replaced it with a VGA cable, and am able to run the external monitor using the Intel HD4000 graphics.  The advantage on battery life is HUGE with the HD4000 Graphics.  My system reports 3-4 hours on a full charge with nVidia, but 10* hours with HD4000.  (*Actual performance may vary.)

---

### Post by balu435 on 2013-05-31
Hi,

I had issues with grub after installing ubuntu 12.04 on my T530 with the default windows7. Problem was grub was not loading and  windows was booting straight away. I reinstalled grub and it worked fine. Everything else seems fine. Had two queries.

1) the inbuilt web cam does not work on pressing Fn+F6. Other function keys work fine and camera was working fine when I was installing ubuntu.
2) there is no caps lock indicator in the key board. What on-screen indicator are you guys using. I would be happy to see the caps lock key status alone..dont think I would want an indicator for other keys.

---

### Post by linrunner on 2013-06-01
Hi!

1) There is no Fn+F6 functionality in Linux, just start Cheese or Skype to use the cam.
2) I have caps lock disabled  ...

---

### Post by cprofitt on 2013-06-01
linrunner:  My unit does not have a camera so I would not have noticed the issue.  I do not have an onscreen indicator for the capslock, but that would be nice.

---

### Post by lalligood on 2013-06-01
I also wanted to add that I recently bought a Bluetooth module for my T530 on eBay. (I'm kicking myself for not ordering the Bluetooth module back when I originally bought the T530!) Aside from the installation hassles--taking out the HDD, keyboard, & the entire front bezel to get access to the area--Ubuntu completely recognized the Bluetooth module at boot time & put the BT icon on the menu bar. No problems getting it to sync up to my phone or tablet...

> **lalligood said:**
> I just got my new T530 last week. After trying the 12.04 Desktop 64-bit CD & seeing that everything worked--and I do mean everything--I installed it right over Windows...

Here are the specs of my T530:
Intel Core i5-3210M Processor (3M Cache, up to 3.10 GHz)
Genuine Windows 7 Home Premium (64 bit)
15.6" HD+ (1600 x 900) LED Backlit AntiGlare Display, Mobile Broadband Ready
Intel HD Graphics 4000
4 GB PC3-12800 DDR3 (1 DIMM)
Keyboard Backlit - US English
UltraNav without Fingerprint Reader
720p HD Camera with Microphone
320GB Hard Disk Drive, 7200rpm
DVD Recordable
Express Card Slot & 4-in-1 Card Reader & Bezel
6 Cell Li-Ion TWL 70+
90W AC Adapter - US (2pin)
Intel Centrino Advanced-N 6205 AGN
Mobile Broadband upgradable
Publication - US English

All of the <Fn> key combinations work (to turn on the backlit keyboard, adjust brightness, lock terminal, etc.). There are some simple settings in the Mouse control panel that enables multi-touch vertical & horizontal scrolling. Display was recognized at full 1600x900 resolution with no additional drivers to install (or fret over!). The webcam worked during the install & I installed guvcview (didn't try Cheese but I don't see why it wouldn't work either). Audio, USB 3.0, wireless & ethernet LAN all worked right away. Speaking of the wireless, it also worked when I was using the live CD! No lag in any of the videos (various .avi, .mp4, & .wmv formats in VLC) nor games (Minecraft & a few Humble Bundle games) I've played. Only problem I ran into with any game was I had to export a variable to get Minecraft to work in 64-bit). Otherwise, not a single problem.

If you or anyone has any questions about running Ubuntu on the T530, feel free to ask!

HTH,

--Lance

---

