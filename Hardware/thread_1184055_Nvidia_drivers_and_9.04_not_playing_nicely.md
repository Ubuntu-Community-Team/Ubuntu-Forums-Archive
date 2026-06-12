---
title: "Nvidia drivers and 9.04 not playing nicely"
date: 2009-06-10
forum: Hardware
---

### Post by metaldrummer610@yahoo.com on 2009-06-10
Hi everyone,
I've had a few problems with my nvidia cards and 9.04. I have 2 nvidia 8600GT cards in sli mode. In windows everything works just fine, but when I went into ubuntu and tried to install the restricted drivers, everything went to hell. Upon startup, I dropped to a terminal and when I ctrl-atl-F7'd, all I see is a black screen with a cursor in the top corner. The driver I installed was the 180 version.

Is is possible that my cards just aren't compatible with 9.04? If that's the case, does anyone have an opinion on what some good nvidia cards are for linux (that actually work :)

Any help or advice is appreciated.



My lspci output is below:

```

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
02:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

```

---

### Post by jward3010 on 2009-06-10
Are you sure the drivers avtually downloaded and installed? Sounds stupid but the reason I ask this is for a while the version 180 drivers weren't uploaded to all repositories in the world and the way the downloader worked it was hard to know whether it did actually successfully download.

Options :
[1] - Make sure version 180 is installed by going to terminal and type [sudo apt-get install nvidia-180-kernel-source]

[2] - If it's not available try a lower version like "177" - [sudo apt-get install nvidia-177-kernel-source]

[3] - Try taking out one card, switching off SLI mode in BIOS and see if Ubuntu runs ok with that. I use a single 7800GTX and from 8.04 up to 9.04 I haven't had a damn problem with nVidia cards either with the free drivers or nVidia's proprietary ones and that includes running Compiz etc. etc. so I'm thinking it should run pretty fine with one card and if it does - it's an SLI problem, possibly driver related, but at least you'll have a working system until a fix is brought out.

---

### Post by metaldrummer610@yahoo.com on 2009-06-11
Ok. I'll try it out when I get the chance later on today. Hopefully it is just an sli problem, because that would suck if I couldn't use the cards in linux.

One other thing I thought might be helpful. I've had this problem since 8.10. I'm pretty sure that when 8.04 came out, everything worked just fine and then when 8.10 came out, it didn't work after the update.

Thanks.

---

### Post by jward3010 on 2009-06-11
In fact it could just be a minor X problem, possibly a little tinkering with your xorg.conf file can get stuff like this working. Try out the previous suggestions first and then head to the tinkering.

---

### Post by carcar1 on 2009-06-11
Have you tried envy?

---

### Post by metaldrummer610@yahoo.com on 2009-06-11
Wow... Complete fail for my desktop. I took out one of the cards and everything worked perfectly... I'm not exactly sure why taking one of the cards out of my computer made everything work. The only thing that I can think of is that I didn't have an sli compatible driver installed.

---

