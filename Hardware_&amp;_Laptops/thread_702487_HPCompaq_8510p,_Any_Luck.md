---
title: "HP/Compaq 8510p, Any Luck?"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by quietas on 2008-02-20
OK, heres the deal. I've got computers at work with Linux, Debian 4 to be precise, an older Thinkpad T22 at home running Ubuntu 7.10, and I've used almost everything over the years. Now I have a Compaq 8510p; great laptop with XP, somewhat shoddy with the Vista Ultimate 64bit or even worse with 32bit.

The goal would be to dual boot XP and run Ubuntu with full 3d support for Compiz and gaming. I need to be able to play the occasional game of WoW. Hell, if possible swapping to Linux entirely would be nice, but honestly that will never happen entirely due to software/hardware companies not supporting Linux. But that's a whole separate thread/rant.

I've seen a few threads about HP's, the 8510p, and/or ATi graphics, but what is the actual supported state of these devices? Do HP laptops really effect Linux badly enough to deserve their own sticky and why? Does the 8510p or the Compaq (HP) business line work better/worse than the consumer versions with Ubuntu? ATI, wtf is with driver support? I see several version of ATi drivers, closed and open source, what works?

One thing more: 7.04, 7.10, 8.04 Alpha, which to install if at all?

Here's my specs if anyone sees any glaring "Hell No" options:

    * Operating System: Microsoft Windows XP Professional
    * Processor: Intel Core 2 Duo processor T7300 2GHz 4MB L2 cache 800MHz front side bus
    * Chipset: Mobile Intel PM965
    * Memory: 4GB 667MHz DDR2 SDRAM
    * Hard drive: SATA 160GB 5400rpm, HP 3D DriveGuard
    * Removable media: DVD+/-RW
    * Display: 15.4" in WSXGA+
    * Graphics: ATI Mobility Radeon HD 2600, 256MB of video memory (512MB Hypermemory)
    * Audio: High Definition Audio, stereo speakers, stereo headphone/line out, stereo microphone in, integrated microphone
    * Wireless: Intel 802.11a/b/g (4965AG), Bluetooth 2.0
    * Communications: Intel Gigabit Network Connection (10/100/1000 NIC),9 56K v.92 modem


~ Quietas

---

### Post by quietas on 2008-02-20
No ideas? No opinions?

---

### Post by Yellow Pasque on 2008-02-21
Networking - Intel chips generally have good Linux support

Audio - You may need to update to the latest ALSA to get your sound to work. Do you know what chipset it uses (e.g. Realtek ALC268)? Here's a script to make upgrading easy in case you need it [http://ubuntuforums.org/showpost.php?p=4360698&postcount=6](http://ubuntuforums.org/showpost.php?p=4360698&postcount=6)

ATI driver- as long as your card isn't AGP, you can use the Catalyst 8-02 drivers. Otherwise, you're stuck with the open-source radeonHD driver, which doesn't have 3D acceleration (but is a damn good 2D driver). FWIW, the vintage "radeon" driver has 2D R6xx support nowadays as well, but I don't think the latest version is in the Ubuntu repo yet.

Ubuntu version - I don't see any glaring reason to go with 8.04, unless you fear the text-based alternate install CD (which is probably what you'll have to use because of your video) Definitely use 64-bit to take advantage of your 4GB RAM.

---

### Post by bartenst on 2008-02-26
I am owner of a HP8510p notebook and currently I am running Ubuntu 7.10_64 (with KDE 4.0.1). Most drivers such as WLAN work like a charm!

Envy:
Use Envy to install the proprietary ATI driver, which almost works perfectly:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
+ 3D-support
+ energy-saving option (PowerPlay) which reduces heat emission of GPU

Sound:
You have to install the newest ALSA drivers by installing the linux-backports-modules package.

Do not hesitate to ask further questions. 

Dominik

p.s. Also having problems with noise? [http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1204029250894+28353475&threadId=1168521](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1204029250894+28353475&threadId=1168521)

---

### Post by saythein on 2008-03-06
I have used this forum to solve many dilemma during my on going bout with Linux but this thread was the one to make me finally register and post.  

bartenst, buddy you have no idea of how much you just saved me ***. I owe you dinner and some cold ones. I always push my department to shop Nvidia, but they just never listen. I came here searching for the right driver version formy 8510p. bartenst, the Envy tool fixed all of the errors I was having with my thin-client student station test clusters. I don't know why or how it really does anything different than installing the old fashion way but it really kept me from having to go to plan B. Thank you so much

Now I've given the proper applause, I have to ask you guys, do you use the finger print scanner on your machines? If so what prog are you using with it? It seems like it's a little bit wasted maybe I'm just a nerd but I'd like to use it just because it's there to be used. It's not really useful unless there is a way to integrate it with the login screen and I have yet to look into doing that. 

Also, has anyone ever tried to use the HDMI port? Will it display as secondary and carry audio also? I need to buy a cable before I can use it but if it doesn't work I'll just keep my $$$ in my pocket. 

One more then I'll leave. Is there a way to assign different functions to the touch buttons in the same row as the volume and power? The circled i brings up the Ubuntu Help window, my wireless button works, the presentation button doesn't seem to do anything, volume and sound in general works great. 

Thanks in advance to everyone willing to share what they know about this and thank you bartenst again I owe you food and booze or something else if booze isn't your thing.
:guitar:

---

### Post by bartenst on 2008-03-20
Dear saythein,

nice to hear that my post helped you. :) And I am also looking forward to consuming that booze. So far I have not tried the fingerprint scanner nor the HDMI port. 

What about the 8510p's fan? Does it also run constantly? Could you please also post the output of 'acpi -t'? Thanks a lot!
     Battery 1: discharging, 64%, 01:47:32 remaining
     Thermal 1: active[5], 40.0 degrees C
     Thermal 2: active[3], 55.0 degrees C
     Thermal 3: ok, 44.0 degrees C
     Thermal 4: ok, 44.0 degrees C
     Thermal 5: ok, 34.0 degrees C
     Thermal 6: ok, 50.0 degrees C

Greetings,
Dominik

---

### Post by kini'mond on 2008-03-20
download envy graphics driver package for ati and nvidia hardware, at google.com..

i'm also using a hp 8510p with same specs as yours (:

it works fine for me :b

---

### Post by bartenst on 2008-03-22
I am not having any problems with the ATI drivers! Envy is a great tool!

Still, i would be interested in hearing about your CPU-, GPU-temperatures etc. (Linux command: 'acpi -t') as many users have complained about a constantly running fan: [http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1206188548632+28353475&threadId=1168521](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1206188548632+28353475&threadId=1168521)

Greetings,
Dominik

---

### Post by saythein on 2008-04-15
Sorry for the delayed response. Here is what i get from acpi -t
Battery 1: discharging, 67%, 01:29:43 remaining
     Thermal 1: active[5], 41.0 degrees C
     Thermal 2: active[3], 55.0 degrees C
     Thermal 3: ok, 47.0 degrees C
     Thermal 4: ok, 42.0 degrees C
     Thermal 5: ok, 29.0 degrees C
     Thermal 6: ok, 50.0 degrees C

My fan runs a lot but mostly just when I'm playing games. I've found that if you prop it up a little bit and let some of the hot air out from underneath the machine it runs less. In Vista it runs a lot more often and for longer periods of time. It has a fairly nice video card in it so I guess it just runs hot. The fans on my 8800gts are insane and the room where they run stays about 6 degrees warmer than the rest of the house. This card isn't that robust but I can see how it would stay hot when under pressure. When I'm not doing something graphically intensive it usually runs pretty quite. 

I tried to install a couple of things for the finger print scanner but I kept getting library this and backport that during the install so I decided it wasn't worth it :) The HDMI however works great. I get audio and crystal clear video and when attached the f4 key will switch between video modes. 

If you do happen to look into the finger print thing please post what you used. All I could find were abandoned projects at sourceforge.

---

