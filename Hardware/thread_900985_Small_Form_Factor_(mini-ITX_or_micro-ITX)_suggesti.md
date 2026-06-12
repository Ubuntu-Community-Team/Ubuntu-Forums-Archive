---
title: "Small Form Factor (mini-ITX or micro-ITX) suggestions?"
date: 2008-08-25
forum: Hardware
---

### Post by Rapture2k4 on 2008-08-25
Hey all,

I've noticed there are alot of small form factor (SFF) motherboards out there. Trying to decide on the best one for my needs has become a bit daunting since I tend to go for the best of the best. I'm wanting to build two SFF machines. One is going to be my router+firewall. The other is going to be a custom mini-PC for my wife.

For the router+firewall I know I need:
Dual Gigabit NICs
Atleast 256mb RAM (1Gig is cheap though, so I'll prolly go with that)
A way to remote-desktop and/or telnet into the device for on-the-fly config.

For the wife:
1 Gigbit NIC + WiFi (802.11g or n)
2 Gb+ of RAM
Dual Core or better CPU
HDMI and/or DVI out
40+ GB HDD
Quiet fan(s)
Bluetooth/Wireless keyboard+mouse support
90W-120W PSU
Multi-Card Reader (Does SIIG work with Ubuntu?)
CD/DVD Burner (Know any good slot-loading slim drives?)

Router questions/concerns:
I would like the router to act as a print server, if possible in Ubuntu. I'm not sure if Ubuntu is the best choice for router, firewall, and print-server though. I'd like to make the router's case similar to a rack-mount router, I just can't find any decent small PSUs. On that topic, what will my power requirements be? I mean, I can get an AMD Geode uITX board that draws next to no power, but will if have enough oomph? Will a HDD really be needed or can I just use a decent 8-16GB flash drive to boot from? I don't expect there will be much reading/writing to the device except during config changes and booting. Everything else should be in RAM, correct?

Or would it be easier/cheaper to buy a pre-built from LinITX.com?

Mini-PC questions/concerns:
My wife really only does web surfing, web design, photo editing & design, and a little gaming. I don't think I'll need to get a board with PCI-e as long as it can handle older DirectX 8 games and output to HDTV. If I were to dual-boot the PC, should I go for SATA I/II or is ATA100/133 enough? I mean, she might get into a little video editing, but nothing hard-core. Besides, there's always my gamer rig she can use for that. That being said, there are a few boards from Jetway that support quad-core CPUs now (Intel and AMD!) but I honestly don't know if anything can handle a newer Phenom 135w CPU or if she could benefit from it anyways. I'd like her to have a 2.2+ GHz dual core machine, but I also want her to be able to play some newer games (I.E. World of Warcraft).

Basically, should I go for Intel Mobile/Core 2, or AMD AM2/AM2+ CPU? What will my cooling and power requirements be? I would assume a 65W CPU will need atleast a 90W PSU, but with everything I want to do, I think I might go for a 120W PSU unless someone thinks I need more. For a point of reference, I plan on making a one-off case about the size of a lunch box, maybe a little bigger, so I already know it will be a tight fit.

Thank you for your time!

---

### Post by Rapture2k4 on 2008-08-26
Anyone?

---

### Post by Chokkan on 2008-08-27
I'm in the final stages of my Pico ITX based PC. Wouldn't recommend that board for your needs but I can tell you about other stuff.

I'm using a very small Bluetooth adapter with a Microsoft Bluetooth mouse and an Apple Bluetooth keyboard. Both work well. Look for the How-to on the Apple keyboard around here somewhere. Mouse required no special setup.

My slim-line drive is a Panasonic UJ-875. It's noisy when it eats up the discs but I think they all are. Works OK.

I'm using the 120W Pico PSU which is more than enough for the board and what I'm running on it.

Good luck with your project. Have you narrowed your options down on the board? I'd love to do a Mini-ITX project next, but have no idea where to start on choosing a board either.

---

### Post by Rapture2k4 on 2008-08-28
Looking at:

[Intel LGA775 miniITX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121353")
[Intel E8400 Core 2 Duo]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115037")
[DVD Burner]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827106260")
[Seagate 7200rpm 500GB HD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148288")
[Kingston 2x2GB DDR2 800 RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820134730")
[Bluetooth Adapter]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833242001")

$531.44 + S&H so far. Not bad I'd say.


Trying to decide on a Fan+Heatsink. NewEgg doesn't have much for low-profile stuff. Haven't decided on either a custom case or getting a pre-built case with built-in card readers. Also, WiFi 802.11n is an issue since this board doesn't have PCI and I have yet to find a PCI-E 1x WiFi card anywhere.

---

