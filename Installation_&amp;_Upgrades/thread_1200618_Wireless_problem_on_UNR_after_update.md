---
title: "Wireless problem on UNR after update"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by c.t.mitchell on 2009-06-30
Hi!

I have run UNR on my AA1 successfully for some time now and love it to say the least - especially after Mandrive proved a great disappointment. I have run the updates yesterday and since then my WLAN will no longer be detected. Before I had a list of WLAN's visible when clicking the Wireless icon in the top right, now nothing appears. I have tried to add the network as a hidden one, it tries to connect and then prompts me for the Network Key, which is entered and correct. 

I have also added the network manually under edit networks, wireless networks, again, no connection. 

I can connect through my 3G card and LAN. 

Any help would be much appreciated as I really don't want to start again from scratch. 

Many thanks!

Chris.

---

### Post by sharkyZA on 2009-07-01
Same problem on my side... Got an Aspire 1 from incrediblecorruption with Linpus on it - buegh!! Installed 9.04 UNR on it and wow! What a difference, and usefull too. The wireless worked with a 'hidden' access point, all was well. UNTIL I ran the updater... Hmm, how to reverse the updates? More reading.
Seriously, can 'see' the wireless access point SSID when activated, can ask it to connect, but there is no connnection - is it something to do with the Atheros wireless card in the netbook, or it's driver?

Oh well -> keep rocking Ubuntu guys & gals  :guitar:

NEW INFO: [https://help.ubuntu.com/community/AA1/Fixes](https://help.ubuntu.com/community/AA1/Fixes) -> Check it out, the wireless fix seems to be either madwifi-hal drivers or windows drivers using ndiswrapper.

Going to try it now myself, will let you know if it works/not

---

### Post by sharkyZA on 2009-07-01
OK, the fixes page helped a lot, it is working. the LEDS don't work, might have done something wrong somewhere... Also, had to sudo a few sudo-less commands , else they wouldn't work. So using the madwifi-hal driver seems to work, so far.
Haven't tried large file transfers, need to sleep some first...

Cheerio  ):P

---

### Post by sharkyZA on 2009-07-03
](*,) It wasn't meant to be... The wireless connection can't be established anymore. Fell over the next morning and couldn't get it working since. Even a fresh Ubuntu 9.04 UNR install without driver updates could bring it back from the dead. 
Can anyone else help??

---

### Post by celticbhoy on 2009-07-06
Also having the same problem, worked till I updated on Friday. The hardware works fine, as my Karmic install connects as it should. If I get an answer I will let you know.

---

### Post by celticbhoy on 2009-07-06
What updated before wireless went down:-

Upgraded the following packages:
cairo-dock (2.0.6) to 2.0.7
cairo-dock-plug-ins (2.0.6) to 2.0.7
chromium-browser (3.0.191.0~svn20090630r19587-0ubuntu1~ucd1~jaunty) to 3.0.192.0~svn20090703r19907-0ubuntu1~ucd1~jaunty
libcompress-raw-zlib-perl (2.015-1) to 2.015-1ubuntu0.1
libperl5.10 (5.10.0-19ubuntu1) to 5.10.0-19ubuntu1.1
linux-headers-2.6.28-13 (2.6.28-13.44) to 2.6.28-13.45
linux-headers-2.6.28-13-generic (2.6.28-13.44) to 2.6.28-13.45
linux-image-2.6.28-13-generic (2.6.28-13.44) to 2.6.28-13.45
linux-libc-dev (2.6.28-13.44) to 2.6.28-13.45
perl (5.10.0-19ubuntu1) to 5.10.0-19ubuntu1.1
perl-base (5.10.0-19ubuntu1) to 5.10.0-19ubuntu1.1
perl-modules (5.10.0-19ubuntu1) to 5.10.0-19ubuntu1.1
playonlinux (3.5) to 3.6
sun-java6-bin (6-13-1) to 6-14-0ubuntu1.9.04
sun-java6-fonts (6-13-1) to 6-14-0ubuntu1.9.04
sun-java6-jre (6-13-1) to 6-14-0ubuntu1.9.04
sun-java6-plugin (6-13-1) to 6-14-0ubuntu1.9.04

My guess would be to do with the kernel. Could you check against my list and post any duplicates.

---

### Post by sharkyZA on 2009-07-07
Happiness! Got wireless running again and tested with >100Mb updates after sorting.
1) Totally reinstalled Ubuntu 9.04 UNR -> Wireless still did not work.
2) Fiddled, tickled and got 'moedeloos'
3) Read the [https://help.ubuntu.com/community/AA1/Fixes](https://help.ubuntu.com/community/AA1/Fixes) page again.
4) The Blacklist of divers comments interested me.
5)  In /etc/modprobe.d/blacklist-ath_pci.conf the last line is 'blacklist ath_pci' -> made this a comment  by puting '#' in front.
6) After reboot the AA1 could connect to my wireless router, 1st on open security settings, 2nd with security.

:-)

---

### Post by JGUTCHES on 2009-07-11
Had same problem with wife's Aspire One after an update.  Followed SharkyAZ's post:
Sudo gedit '/etc/modprobe.d/blacklist-ath_pci.conf'
and changed last line as outlined:
# blacklist ath_pci   
saved and rebooted.  All is back to normal.  Thanks for the help.

---

### Post by sharkyZA on 2009-07-16
Seems there is a hiccup again... My wireless card doesn't work anymore. Can't really think that I broke it, anyway, I don't really want to reinstall 9.04 UNR to get it going again.
So there must be something somewhere that, over time and use, gets corrupted or self-adjusted wrong setting or the like.
Anyone with any ideas?

---

### Post by celticbhoy on 2009-07-16
Are you using the madwifi driver?
If so you will have to recompile after the last kernel update.

---

### Post by sharkyZA on 2009-07-16
Hi Celtichboy

No, using ath_pci that runs standard on UNR 9.04. After fiddling with madwifi last time, it also only working for a day or two, I reinstalled and only uncommented the blacklist thingie to get wireless working.
Now after many days of wireless happiness things have gone south again, without warning and preperation... :confused:

Thoought this might shed some light: (to someone who has a little more insight than I)
```
 dmesg|grep ath
[    3.140789] device-mapper: multipath: version 1.0.5 loaded
[    3.140795] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.987023] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.987057] ath5k_pci 0000:03:00.0: setting latency timer to 64
[    6.987176] ath5k_pci 0000:03:00.0: registered as 'phy0'
[    7.183531] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[    7.185254] ath_hal: module license 'Proprietary' taints kernel.
[    7.189896] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[    7.304934] ath_pci: 0.9.4
[  162.986424] ath5k phy0: unsupported jumbo
[  640.195496] ath5k phy0: unsupported jumbo
[  942.840962] ath5k phy0: unsupported jumbo
[ 1013.312626] ath5k_pci 0000:03:00.0: PCI INT A disabled
[ 1014.320790] ath5k_pci 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1014.320835] ath5k_pci 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x75200004)
[ 1014.320847] ath5k_pci 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x20)
[ 1014.320862] ath5k_pci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1014.336159] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
```

---

### Post by heine on 2009-07-22
[COLOR=black][FONT=Verdana]Hi.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I'm not an expert in neither Linux nor Ubuntu (yet :biggrin:) but I have read somewhere about Wi-Fi issues on the AA1 and the trick was to flash the Bios to a newer version. I myself run UNR on a Bios version 3309 and my Wi-Fi works great out of the box. When I flashed my Bios I followed the guide on macles blogspot.[/FONT][/COLOR]

---

### Post by sharkyZA on 2009-07-23
I have flashed the BIOS recently with 3309 to get the fan mod to work with lower settings, unfortunately my wireless still goes out the window every day or two. But I'm glad to note that your solution will work with a fresh install. I'm not very eager to re-install though. It took a lot of tweaking to get everything setup like I want and a lot of bandwidth to download all the extra stuff that is not in the distro.

What is happening here since I last posted: The wireless packs up. Then I run ```
sudo modprobe -r ath5k acer_wmi 
sudo modprobe ath5k
```Read that someone else does this, and voila! Wireless running again. Undetermined period goes by, wireless packs up again... we enter the modprobe commands and happiness returns.

I don't know if the wireless packing up is based on elapsed time, or data throughput or other rather special autoset parameters, but it is slightly annoying. But at least, being able to 'reset' it is a bit less annoying than not being able to use it at all.

---

