---
title: "AverMedia A180 tuner with Phillips SAA7130 Chipset Not Installed"
date: 2009-06-17
forum: Hardware
---

### Post by MattyGabe on 2009-06-17
Hello,

I'm having a terrible time attempting to install a card that I certainly know works with Ubuntu, but I have heard that it is supposed to work with Ubuntu because there are v4l drivers out there (video4linux).  In a round-about way, I have attempted several ways to get my hardware recognized, yet I get little or nothing accomplished.

Early on, one tutorial had me adding "saa7134" to my modprobe blacklist so that I could install saa7134-dvb.  A few others had me dropping .fw (I'm guessing it's a FIRMWARE file) into certain kernel directories and then running modprobe... I've tried a few others that had me download a package, and then attempt to use MAKE and MAKE INSTALL to compile the driver itself, only to find out that the latest kernel deprecated some of the code used in those files, so on and so forth...

I'll provide whatever information you need to know, I would just like to ask for some help in getting my TV tuner working.  I have both MythTV and TvTime installed, and neither can recognize the card whatsoever.

Thanks ahead of time for any help provided.  Here are any and all dmesg entries pertaining to the tuner:

```
[   10.067970] Linux video capture interface: v2.00
[   10.143165] saa7130/34: v4l2 driver version 0.2.14 loaded
[   10.143329] saa7134 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.143337] saa7130[0]: found at 0000:00:09.0, rev: 1, irq: 17, latency: 32, mmio: 0xea005000
[   10.143343] saa7130[0]: subsystem: 1461:1044, board: UNKNOWN/GENERIC [card=0,autodetected]
[   10.143371] saa7130[0]: board init: gpio is 110400
[   10.296244] saa7130[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   10.296252] saa7130[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   10.296259] saa7130[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 00 10 00 00 00 00
[   10.296265] saa7130[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   10.296271] saa7130[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   10.296277] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296283] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296289] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296295] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296301] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296307] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296312] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296318] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296324] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296330] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296336] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296541] saa7130[0]: registered device video0 [v4l2]
[   10.296642] saa7130[0]: registered device vbi0
[   10.340507] saa7134 ALSA driver for DMA sound loaded
[   10.340540] saa7130[0]/alsa: saa7130[0] at 0xea005000 irq 17 registered as card -2
[   10.707720] bttv: driver version 0.9.17 loaded
[   10.707724] bttv: using 8 buffers with 2080k (520 pages) each for capture
```

---

### Post by MattyGabe on 2009-06-21
I still have not had any luck in installing this card.  I really don't have the knowledge of what to do to figure this out, but I know it works which is why I'm so frustrated.

So I've come back to it after a few days of not touching it.  Found the Perl get_dvb_firmware script in it's entirety, created my own in a local folder, and even edited the URL for Avermedia's site (I guess they changed it since Jun7, 2009?), and successfully downloaded and extracted the .FW for the Nxt2004 drivers.  And, because the 2.6.16+ Kernels already have support for this card, the saa7134 drivers are also available.

With that being said, I have blacklisted drivers, attempted to modprobe saa7134-dvb, looked at dmesg and to no avail.  In MythTV when I go to add a card, it defaults to Analog V4l card at /dev/video0.  Which is fine, I won't get pushy.  All wikis point to me needing to add a DVB card, because by this card's nature it ONLY receives digital signal (that's why I bought it, but that's another discussion).  So I add it because it seems to think that's what I need.  It does not work. MythTV's information station reports that "Tuner x (either 1 or 2) is unavailable.", and I get no picture whatsoever.  I've seen no other devices listed in /dev/ that seem to indicate that they represent my tuner card, other than video0, but that's obviously not it.  There's a folder /v4l/ in /dev, but I have no clue what it's there for, what it does.

Is there a way where I could completely nuke everything that pertains to tuner cards in the way of drivers and get a clean slate in terms of installing the correct software that I have on-hand, or what has been pre-included with my kernel?  Any help here is greatly appreciated, and as I've said before I'll provide whatever diagnostic information you need.

---

### Post by MattyGabe on 2009-06-21
Okay, I finally got it installed, but not without some help from a very generous and helpful fellow on #mythtv-users on freenode.

I'll attempt to go through what was done in order to get my card to work:

1. Remove all saa7134 drivers. Start with 
```
rmmod saa7134
```

If it gives you any errors such as "In use by xxx, xxx2" then remove those modules first, and then do saa7134.  My installation saa7134 was in use by saa7134-dvb and saa7134-alsa, so I rmmod'ed both of them and then could successfully rmmod saa7134 (in Ubuntu you need to use 
```
sudo rmmod saa7134
```

2. Ensure that you do not have any drivers blacklisted.  A few other tutorials had me edit the /etc/modprobe.d/blacklist.conf file where I blacklisted "saa7134".  I removed this line and saved the file.  By default I don't believe saa7134 is already there, so if you haven't explicitly added it yourself like I have, you won't have to remove anything here.

3. This is where it differs for me for my particular card: add back the saa7134 drivers by using modprobe: 
```
sudo modprobe saa7134 card=75
```
and
```
sudo modprobe saa7134-dvb
```

The parameter card=75 must specifically designate my exact card, so unless you have the same card I do, you may need to designate another card number here.

**Note: I removed the "card=75" parameter for saa7134-dvb, as I found that for some reason it did not work and resulted in an error in dmesg. card=75 is only needed for saa7134.

4. Check the directory /dev/dvb/: 
```
ls /dev/dvb
```

If the device "adapter0" is listed there, it has been successfully loaded.  If not, I suggest you seek further help in the IRC channel #mythtv-users.

5. In order to *attempt* to ensure these drivers remain loaded upon next startup, you must execute these following commands to enter a few lines into the modprobe.d options file: 
```
echo "options saa7134 card=75" >> /etc/modprobe.d/options.conf
``` 
and
```
echo "options saa7134-dvb" >> /etc/modprobe.d/options.conf
```

It must be done as root user (sudo won't work), and I did so by typing 

```
sudo su
```

then entering the two lines above, then typing "exit" to exit access as root user.

**Note: I fixed both commands. The first one wrote to "options" instead of "options.conf", and the second one also wrote to "options" instead of "options.conf", but I also removed the "card=75" parameter (see above)

6. Follow MythTV manual to then correctly add a capture card, then save channel lineups, etcetera.

Additionally, I have already downloaded the Nxt2004 firmware file (Nxt2004.fw) and placed it in /lib/firmware/.  The Perl script get_dvb_firmware needs updated (Avermedia changed its website so the URL for the nxt2004 portion is different), but that code can be [accessed here]("http://www.mjmwired.net/kernel/Documentation/dvb/get_dvb_firmware").  Search MythTV documentation for the updated URL, as that's where I found it.

I hope I provided enough detail for everyone to follow through, and I'd like to thank iamlindoro at #mythtv-users for all of his help in fixing my installation.  I would've never figured this out on my own.

---

