---
title: "New lease of life for a 2002 Dell Dimension from the rubbish tip (a story)"
date: 2014-04-04
forum: Hardware
---

### Post by Xubuntist on 2014-04-04
I didn't know where else to post this so, mods, if this is the wrong place, please move it.

A couple of days ago my friend José, who knows I "do" computers, brought round a 2002 Dell Dimension 4500 which he salvaged from the local tip. Thinking he might have got himself a working PC for nothing, he'd plugged it in at home but had only got the boot screen and then "No OS found", so he asked if I wanted it. Normally I'd have said No, I have enough computer junk in my workshop but since it obviously fired up I thought it'd be a great Xubuntu project machine. Full specs of the PC were:
[LIST]
[*]Dell Dimension 4500 
[*]Pentium P4 2.26 GHz 
[*]1 Gb RAM (they were sold with 256 Kb, LOL) 
[*]80 GB HDD 
[*]NVIDIA GeForce4 Ti 4200 video card 
[*]Some crappy Soundblaster sound card 
[*]A 10/100 LAN card 
[*]Windows XP Home 
[/LIST]
I plugged it in and the BIOS fired up but hung for ages and gave up without finding a hard drive. It also gave me a "no CPU fan detected" warning. I opened the pc up and found that the CPU heat sink is all it has, as far as I could see it has no fan. I couldn't find anywhere in the BIOS to turn that warning off so instead I ripped a CPU fan out of another PC and cobbled it onto the heat sink and plugged it into the motherboard and at the next boot the warning was no more. Inside the machine I discovered not one but two two hard drives, one a Maxtor with a 1995 date stamp on it! I chucked that one out but kept the 80Gb WD which, after a quick test, turned out to be nice and healthy. I fiddled with the ribbon cables and jumpers and finally the machine booted into Windows XP. Not sure why the original owners threw it away because at the end of the day it worked. Maybe somebody poked his nose into the case and just made it worse. But they should have removed the hard drive before chucking it away.

I ripped out the RAM and put 2Gb in instead. I threw away the video card and put in a Radeon HD3450 which I've had lying around for a few years waiting for the right computer. And then I installed Xubuntu :D.

The installation didn't detect the 10/100 card at all so I booted into the LiveCd instead and plugged in a USB Wifi stick and it found it and connected straight away - what a refreshing change from Windows where you have to hunt for the right driver and have it installed before just about anything works. I then installed Xubuntu from the LiveCD session. Installation was, as always, a breeze - it picked up the Radeon video card without any problem. I then installed the following packages:
[LIST]
[*]GDebi 
[*]7zip 
[*]KDocker 
[*]Teamviewer 7 
[*]GParted (it's on the LiveCd but doesn't seem to be on the hard drive installation) 
[*]Flash player 
[*]Skype 
[*]VLC 
[*]LibreOffice 
[*]Faience theme and icons 
[*]Gvfs and Samba (actually I think Samba is part of the installation) 
[*]Audacity 
[/LIST]
Two problems remained after the updates and rebooting:
[LIST]
[*]There was no sound coming from the speakers although Flash player and VLC both indicated a working sound card and volume control. I did **sudo alsa force-reload** and rebooted and lo and behold that fixed it.
[*]The Ethernet card just didn't want to be detected. But I couldn't frankly be bothered with that because the Wifi key worked great from the very beginning.
[/LIST]
And that was that! I now have a fairly good PC running a brand new OS and all it cost me was a couple of hours of my time. Thank you Xubuntu, because I sure wouldn't have had that result if I'd chosen Windows :)

---

### Post by tgalati4 on 2014-04-04
If your network card is part of the motherboard, then there is a good chance that it got zapped by a power spike--a common problem in older computers and a primary reason they get junked.  You can probably find a gigabit LAN PCI card as a substitute.  Does the network card show up in *lspci*?

```
lspci | grep controller
```

It's possible that the network chip still works but the receiver or transmitter radio has been zapped.

The advantage of a wired network card is you can use Wake-on-LAN (WOL) and turn the machine into a sleeping server.  P4 computers use a lot of power.  About $100 per year if run 24/7.

Nice tutorial on how to revive an old computer.

---

### Post by Xubuntist on 2014-04-04
It's  interesting that you should say that because I was thinking of setting up a server. WOL would be dead handy in that case, especially with this beast, not only because of the potential electric bill (in the great scheme of things not excessive) but also because it's very noisy. The fan I put on it is certainly effective. I touched the heatsink accidentally earlier on before fitting the fan and I nearly burnt myself, but now after pulling the current I can touch it and it's barely warm. Unfortunately I've not discovered any sensors other than on the Radeon video card,  neither in the BIOS nor on the mboard because I would have liked to see the figures:

[ATTACH=CONFIG]251728[/ATTACH]

But it's **really **noisy. WOL would help mute that racket much of the time.

As for the Ethernet issue, it's a PCI card:
```
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620 LE [Radeon HD 3450 AGP]
[B]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[/B]02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
```
So it looks like, although there's no lights on, Xubuntu's recognised it's there. **modprobe 8139too** didn't throw up any errors, so it's something else. I'll play around and report back :)

---

### Post by mörgæs on 2014-04-04
Old hardware is normally less power demanding than new, if you compare within same category:
[http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html](http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html)

---

### Post by tgalati4 on 2014-04-04
Rule of Thumb--100 watt server running 24/7 will cost about US $100 per year.

Electric Rate in Los Angeles is $0.13 per Kilowatt*hour.

A typical P4 desktop machine will burn 100 watts of power at idle and perhaps 115 watts under load.  There is typically no instrumentation built into the P4's.  They are 90-watt total dissipated heat (tdp) processors.  Putting your finger on it should feel like a 90-watt light bulb--hot enough to burn.

100 watts *24 hours is 2400 watt*hours or 2.4 kilowatt*hours.

2.4 kwh * 365=876 kwh's per year.  876* 0.13= $113.88

That's enough to buy a couple of RaspberryPi's.  In another year, a small hard disk.

So spending $10 to $20 on a working network card is worth getting WOL to work.  Your costs would then go to $5 or $10 per year depending on usage.

I put a WOL launcher on each laptop and tablet around the house to wake one of my servers when I need to use it.

Cheesy script:

```
#!/bin/sh
# Super cheesy script to wake my server and put up a notification to that effect
#
/usr/bin/wakeonlan 00:19:d1:fa:0b:90
sleep 3
/usr/bin/wakeonlan 00:19:d1:fa:0b:90
sleep 3
/usr/bin/wakeonlan 00:19:d1:fa:0b:90 
sleep 2
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "Zalman PC is waking up"  "You'll be up in a few seconds."
sleep 10
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "Zalman PC is alive." "It's services are now available."
echo "The current time is:"
DISPLAY=:0.0; notify-send -i clock "$(date +"%H:%M")"
exit 0

```

The icons were copied from somewhere:

tgalati4@Mint14-Extensa ~/Projects/scripts $ locate server.svg
/usr/share/icons/gnome-colors-common/scalable/apps/gdmflexiserver.svg
/usr/share/icons/gnome-colors-common/scalable/apps/vmware-server.svg
/usr/share/icons/gnome-colors-common/scalable/places/gnome-fs-server.svg
/usr/share/icons/gnome-colors-common/scalable/places/gnome-mime-x-directory-nfs-server.svg
/usr/share/icons/gnome-colors-common/scalable/places/gnome-mime-x-directory-smb-server.svg
/usr/share/icons/gnome-colors-common/scalable/places/network-server.svg
/usr/share/icons/gnome-colors-common/scalable/places/redhat-network-server.svg
/usr/share/icons/gnome-colors-common/scalable/places/server.svg
/usr/share/icons/hicolor/scalable/apps/mdmflexiserver.svg

I have a couple of Dell PowerEdge 1750's.  They set the bar for fan noise.  7 fans running at 6600 RPM.  They burn 218 to 240 watts between idle and crunching--2 dual-core Xeons.

---

### Post by Xubuntist on 2014-04-05
This would explain California's power crises ;-)

---

### Post by tgalati4 on 2014-04-05
We lost a nuclear plant last year that provided 12% of our regional power.  France has no such shortage.  The US prides itself on using 25% of the World's energy while only about 4% of the World's population.  What are typical electric rates in France?

---

### Post by Xubuntist on 2014-04-05
I honestly have no idea. Bills arrive and my wife juggles them. I'm sure  they are exorbitant, as is everything in France.

I hope you find your nuclear power plant.

---

### Post by tgalati4 on 2014-04-05
It's stuck in the sand with [2 blown boilers]("http://en.wikipedia.org/wiki/San_Onofre_Nuclear_Plant").

---

### Post by Xubuntist on 2014-04-06
It's good to see so many people [enjoying the seaside next to an unsafe nuclear power plant]("http://upload.wikimedia.org/wikipedia/commons/thumb/4/49/San_Onofre_Nuclear_Generating_Station_photo_D_Ramey_Logan.jpg/1280px-San_Onofre_Nuclear_Generating_Station_photo_D_Ramey_Logan.jpg"). However, I'm sure all is not lost - I'm thinking "Concrete Jungle!" a 21st century kids adventure park, or an environment and ecology conference and leisure centre, it seems a waste to let all that concrete go to waste...

---

### Post by tgalati4 on 2014-04-06
I understand that when the plant shut down, the local sea life were not happy that the warm water stopped flowing.  A lot of rock lobster and fishies that grew up around the warm plume now have to find new digs.

---

