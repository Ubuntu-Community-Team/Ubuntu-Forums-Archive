---
title: "DELL Studio 1535 and Ubuntu 8.04"
date: 2008-08-22
forum: Hardware
---

### Post by Skelas on 2008-08-22
Any experience using DELL Studio 1535 with Ubuntu? 
(Notebook DELL Studio 1535 15.4" LED Backlight (1440x900) TFT, Core™2 Duo Mobile T9300 25GHz /800MHz, Intel PM965 Express, DVD±RW, LAN, Bluetooth /Gigabit Ethernet / /Wi-FiConsumer IR, ATI Mobility Radeon HD 3450 256MB, RAM 4096MB DDRII 667MHz(PC2-5300))

Especially comments on ATI Mobility Radeon HD 3450 compatibility with Ubuntu would be very appreciated.

Thanks

---

### Post by minni on 2008-08-26
Dell Studio works great with Ubuntu 8.04 32bit

- Network with LAN and WLAN 
- ATI Graphics Card including compiz and 3D
  (Dual-Screen with HDMI)
- Bluetooth
- DVD burning
- Sound Card

The only thing I had no luck with until now is the IR remote.

---

### Post by heimo11656 on 2008-08-30
I had a bit of trouble with my ATI gfx card, but that was resolved.


What I'm really having trouble with is WiFi. I've been working on it (I'm a noob) for about 5 hours now. So far it just lights up and shows me the network, but it doesn't connect.

---

### Post by pelle.k on 2008-08-31
Compiz working without any problems at all?! really? You can play videos and such without any workarounds etc?
Also, how about suspend/hibernate functionality? Does it resume cleanly every single time?
Oh, and what about media/Fn buttons? Do they all work, and if not, are they at least sending scancodes to the kernel?

Thankyou very much in advance for answering, because i'm really interested in these notebooks, but i'm sick and tired of paying in time to get everything working.

---

### Post by mrstimpson on 2008-09-21
how did you get the graphics card and wireless to work...?

please share

---

### Post by pah99 on 2008-09-23
I have a Dell Studio 1535. I haven't installed Ubuntu yet, however I did try a live CD of Ultimate Edition. When using it, the video card worked fine (ATI 3450), however, Ubuntu couldn't recognize my wireless (Dell 1510 Mini N). Sound worked fine, and pretty much everything else including the back lit keyboard (god I love that). So yeah. Hope that was of some help.

---

### Post by marioquark on 2008-10-11
hi,
i use ubuntu intrepid and wireless works like a charm...
ati card will be fully functioning with the next proprietary driver release that supports Xorg 7.4... i'm waiting.

---

### Post by pah99 on 2008-10-12
> **marioquark said:**
> hi,
i use ubuntu intrepid and wireless works like a charm...
ati card will be fully functioning with the next proprietary driver release that supports Xorg 7.4... i'm waiting.

I just wanted to confirm this also. I have the Dell Mini-N 1510 card, and it works out of the box with Intrepid Ibex.

---

### Post by Kulgan on 2008-11-14
Time to update this thread to 8.10?

I'm on a Dell Studio 1535 running 64-bit Ubuntu 8.10. Problems encountered so far:
- Speakers don't mute when headphones are plugged in. Probably the biggest problem, for me. Only one of two headphone jacks works. 

- Turning up and down the brightness manually looses most keyboard functionality. I believe this is common to 8.10, as it also happened on my old laptop after upgrade. 

- Fingerprint scanner and infrared remote not working OTB. (And I haven't yet figured how to get either to work.)

On the good side, however:
- The media buttons all work; just not the ones on the remote. 

- Wireless works OTB (though I had to install the drivers from the proprietary drivers installer to fix some shaky connections). 

- ATI drivers work well after installing drivers from said installer. (even before doing so, screen was full res.) if you don't need compiz, you're fine without the driver, if you do... it's awesome. (Still need to change the default output plugin to "No XV" in gstreamer-properties to avoid blinking movies, though). 

- Bluetooth is correctly recognised, though I have not yet tested it with an actual device. 

Have yet to test standby and hibernate. Don't want to screw anything up. 

Another problem possibly related to the upgrade to Ibex is that partitions related to Ibex don't seem to mount correctly from Windows using fs-driver. (Thread on that [here]("http://ubuntuforums.org/showthread.php?p=6177676"))

Would be interesting to hear what someone on a 32-bit install had to say about it, especially in regard to the speaker-mute issue. Everything seemed to work fine on the LiveCD.

---

### Post by pah99 on 2008-11-14
Have yet to test standby and hibernate. Don't want to screw anything up. 

Would be interesting to hear what someone on a 32-bit install had to say about it, especially in regard to the speaker-mute issue. Everything seemed to work fine on the LiveCD.[/QUOTE]

Hey first off I would like to say thanks for the fix on the blinking video. That was a big pain.

Secondly, I too use 64 bit Ubuntu and experience all of the same problems. You were wondering about the 32 bit.. I had that installed first and it also had the same problems in relation to sound. I have noticed one thing though, the sound issue is a problem only in 8.10. 8.04 did not have the sound problem. Hope that helps.

---

### Post by Kulgan on 2008-11-14
You're welcome for the gstreamer fix. From what I understand, it shifts video processing from the video card to the cpu. Ironic, really...

As for the rest, we've got a dev on the case at [http://ubuntuforums.org/showthread.php?p=6180295](http://ubuntuforums.org/showthread.php?p=6180295). Apparently there are changes in intrepid proposed that are working towards the issue - they haven't made any significant impact for me, though.

---

