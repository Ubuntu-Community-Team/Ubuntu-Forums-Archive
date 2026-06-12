---
title: "Ubuntu Server Hardware Questions"
date: 2014-11-25
forum: Hardware
---

### Post by Ollie_Spurway on 2014-11-25
Hi all, I am currently planning an Ubuntu Home server for a couple of reasons. Firstly, to house all my Music, video and digital photographs in one place, to be accessable to multiple devices in the house. Secondly - because i have never tried anything like this. I have built single workstations, and been playing with various linux distos for a while, but this will be my first server. 

The first step for me is to plan out the hardware. I want to try and keep the cost down and have the following 'shopping list' at present:

[TABLE="class: product-listing"]
[TR]
[TD="class: product-image"][                         ]("http://www.dabs.com/products/intel-celeron-g1840-2-80ghz-s1150-2mb-9D9D.html?src=3")                     Intel Celeron G1840 (2.8GHz 2MB Cache Dual core)  -  Approx £30
A 1150 socket motherboard that supports 1600MHz DDR3 RAM, With gigabit LAN  -  Approx £30
4GB DDR3 RAM  -  £20
A couple of 1TB SATA HDD's  -  £30 each 

Obviously there will be other minor bits and bobs (case, cables, PSU etc) but this is the meat of the beast. My questions are:

1. What is the opinion on this harware spec for a media server
2. What size PSU would you run with this
3. Any good ideas on silent cooling (that don't require the selling of a kidney!)

Any help or opinions much appreciated. 

Ollie

[/TD]
[TD="class: description"][/TD]
[/TR]
[/TABLE]

---

### Post by weatherman2 on 2014-11-25
The CPU sounds fine.  I have built a couple of media center boxes with similar specs in the last few years.  You don't need much CPU power for what you are planning.

You will have a CPU fan for sure (may come with the CPU from Intel depending on how you buy it).  You will probably want a case fan.  Your power supply will probably have a fan too - unless you get a silent PSU like a Pico.  But even with a conventional PSU may not be that loud.  My current media center, attached to my TV, is not loud at all - I can hear it when the TV is off and the room is silent, but if I'm actually watching something I can't hear the fans at all.  I have a 430W Corsair CX430 efficient power supply, which is way more than I need.  This system (similar to your specs) draws about 20 watts at idle, though I have no extra video card.  It might hit 50 watts under load.  I'd want probably a 200W PSU minimum.  I got the 430W because that was cheap and a known good product.

You could probably get a Pico PSU (silent), invest in a better CPU cooler, and get a case with good air flow (maybe not a tiny one if you care) so you won't need extra cooling and fans inside.  Larger fans tend to be quieter FYI.

Personally, I would get an SSD for the operating system and use the HDDs for storage.  SSDs are getting really cheap, and it's nice to have your data on separate drives.

If you are planning to do a RAID with your HDDs, make sure you have a separate backup as well.  RAID is great for reliability to avoid data loss in case of hard drive failure, but it's not a substitute for backup.  File systems can become corrupt, files and folders accidentally erased, etc.  Personally, I would expect to invest in a portable backup drive as well, usually not connected to the server, that you use occasionally to make backups of your data.

Sound: if you are planning to connect this server to speakers or an amp, consider how you will do that.  I have a sound bar connected to my TV, and the sound bar has an optical input.  I got a motherboard that has optical out, so now I can listen to music or streaming radio from the server and the sound bar, without needing to have the TV on.    Most motherboards don't have optical out, but if you are planning some other method of audio, maybe you don't need an optical out.  Just something to consider.

---

