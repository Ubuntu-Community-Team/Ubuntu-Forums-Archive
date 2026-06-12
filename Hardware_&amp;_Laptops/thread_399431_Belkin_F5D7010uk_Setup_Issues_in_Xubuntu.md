---
title: "Belkin F5D7010uk Setup Issues in Xubuntu"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by regomodo on 2007-04-02
I managed to get xubuntu to work on a IBM thinkpad 570e. Apart from lack of sound, poor graphics handling and no battery monitoring i thought i'd try and get my wireless card to work.

I ran libspci (i may have that wrong but you know what i mean) and i found out that this card is a Ralink rt2561/rt61

I've searched here and follow the guides but the install gives up after the rt61sta.dat config stage.

I tried following the steps in the readme file in the tar but that also gave up at 

$dos2unix rt61sta.dat

saying that it has no idea what dos2unix means

has anyone got this card to work with wpa that doesn't require you to edit the rt61sta.dat's SSID everytime you enter a new network?

Geez, i'm liking windows more and more. Things actually work there despite the bloat.

---

### Post by regomodo on 2007-04-03
no one??!!

---

### Post by dolphin_oracle on 2007-04-03
I am currently running xubuntu on a sony vaio fxa-32 (900mhz duron, 128mb ram).  I couldn't find a reliable method for what you suggest without editing rt61sta.dat.  My work around is to have more than one rt61sta.dat, one for each SECURED network i'm using.  I also have one that is blank.  I then can copy the appropriate .dat file to rt61sta.dat then do a network restart.  You will have to find the ESSID with iwlist ra0 and set the ESSID with sudo iwconfig ra0 essid ESSID (the caps version being the actual ESSID of the desired network).  

This setup worked fine for my home network (WPA secured), and then a public rt61sta.dat for my traveling last week (airports, motels).  I particularly have my files named rt61sta.dat.home and .public, and always copy (cp) them to rt61sta.dat so that I don't override my configurations files.

---

### Post by regomodo on 2007-04-04
Doh, didn't think to use ndiswrapper.

Thin i got my card working in Mandriva using the windows driver cd. It detected the local networks and the light blinks every now and then. I like the look of it but i think it's a touch too demanding on my 570e despite 320mb or RAM. Just not enough graphics power

Thanks anyway

---

### Post by regomodo on 2007-04-04
Wait, ndiswraper isn't installed with Xubuntu automatically. Hmm

---

### Post by regomodo on 2007-04-04
Update. Ndiswrapper initally worked with Mandriva using the .inf files supplied with the card (it found all my local wireless networks) then gave up and kept blinking at me in a set pattern (1 led stayed constant but went off once the 2nd led had flashed 5times. Restarted the cycle on the next flash)

Meh, i've given up entirely with Linux regarding wifi. A Prism and Ralink chipset card, several linux distros,  and all the guides in the world hasn't helped. Must be my old thinkpad 570e or my bad luck. Hell, it only took me 30mins to use wpa on win98, not over 2months with linux and nothing to show for it.

Let me know when wifi works in linux

---

### Post by Achetar on 2007-12-03
> **regomodo said:**
> Update. Ndiswrapper initally worked with Mandriva using the .inf files supplied with the card (it found all my local wireless networks) then gave up and kept blinking at me in a set pattern (1 led stayed constant but went off once the 2nd led had flashed 5times. Restarted the cycle on the next flash)

Meh, i've given up entirely with Linux regarding wifi. A Prism and Ralink chipset card, several linux distros,  and all the guides in the world hasn't helped. Must be my old thinkpad 570e or my bad luck. Hell, it only took me 30mins to use wpa on win98, not over 2months with linux and nothing to show for it.

Let me know when wifi works in linux

I got my Linksys WPC54Gv3 card to work (search for it, it's a problem...) after about 1 week (and after following countless guides). There is hope for it!

---

