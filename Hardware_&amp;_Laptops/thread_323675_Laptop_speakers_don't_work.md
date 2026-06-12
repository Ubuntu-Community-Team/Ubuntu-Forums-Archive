---
title: "Laptop speakers don't work"
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by sparrowkc on 2006-12-22
I seem to have a problem with my soundcard.  If I plug headphones into my laptop, I can hear sound just fine, but I cannot get the speakers on my laptop to work. 

lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev 25)
00:02.1 Class ffff: Illegal Vendor ID Unknown device ffff (rev ff)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
```

I have an Emachines M5405 laptop.


 I have my mind set on switching from windows to ubuntu, and this is the last problem I need to resolve before I can take the plunge!

---

### Post by NeoLithium on 2006-12-22
In a terminal, try typing: ```
alsamixer
``` And increase the volume to max on each of the options, it's what I had to do on my laptop, to get the sound going :)

Hope it helps!

---

### Post by sparrowkc on 2006-12-22
Thanks so much! I have been trying to get this fixed for so long!


I love community support...

---

### Post by NeoLithium on 2006-12-22
No problem, glad it worked :)

---

### Post by lamy on 2007-01-29
If the above solution did not work on your m5405.  

Here is what worked for me:

1. Double click on the speaker volume Icon. 
2. Goto: File --> Change device, and make sure that "0: SI7012 (Alsa Mixer) is selected.
3. Click on the "Switches" tab.
4. Uncheck "External Amplifier"

If it still doesn't work, max out all of the volume levels. 

Hope it helps,

lamy

---

### Post by cuppdiane on 2007-02-25
> **NeoLithium said:**
> In a terminal, try typing: ```
alsamixer
``` And increase the volume to max on each of the options, it's what I had to do on my laptop, to get the sound going :)

Hope it helps!

What is a terminal???where do I find this

---

### Post by cuppdiane on 2007-02-28
I have the same problem sound on headphones but no sound from speakers--where is the terminal and what should I type in

---

### Post by Kevkill on 2007-02-28
The terminal is located under Applications - Accessories - Terminal.

---

### Post by strabes on 2007-02-28
I had this same problem but it was because my motherboard was bad lol. Thank God for Dell's warranty that I bought.

---

### Post by srt5 on 2007-03-01
I have the same problem as mentioned above. The sound is working through the headphone socket but not the laptop speakers. When I try executing alsamixer in terminal i get:

```
alsamixer: function snd_mixer_load failed: Invalid argument
```

I've read around and I think it's a driver issue, but I'm not sure how to fix it.

Can anyone help? Has anyone had the same problem.

I have an Acer 5051AWXMi laptop.

Thanks :)

---

### Post by tonywhelan on 2007-03-06
See solution posted above: [http://ubuntuforums.org/showthread.php?t=323675&highlight=speakers+acer+laptop](http://ubuntuforums.org/showthread.php?t=323675&highlight=speakers+acer+laptop)

I had same problem with Acer laptop 3680 - headphones ok, speakers dead.

1. Did the full procedure set out in the above thread (takes a while) but still no joy.

2. Then in a terminal window I ran "alsamixer" which brings up a graphical mixer window. Alll my speaker values were set off ("MM") and once i figure out how to set them, on, all was good. Use the cursor arrow to move to the desired 'column' and then press the "M" on your keyboard to toggle that column on or off. MM is off, 00 is on. Then use up arrow to raise volume to desired level.

I am not sure if Step 2 would have worked without Step 1. So if you are still having this problem, try step 2 first, and if no joy try doing both.

---

### Post by srt5 on 2007-03-06
I managed to get my sound working :D I followed this tutorial: 

[http://uk.blog.360.yahoo.com/blog-kLgobDE_cqVv1JH8Yrs5u0AOygiyr1iiv0erhcaU_BKG?p=5](http://uk.blog.360.yahoo.com/blog-kLgobDE_cqVv1JH8Yrs5u0AOygiyr1iiv0erhcaU_BKG?p=5)

it just involved installing realtek linux drivers from their website, i'm not sure if this will solve all of the problems reported for acer laptops in this thread - but it worked for me :)

hope this helps

---

### Post by fulv on 2007-03-06
alsamixer fixed my problem, so I'm very happy I found this thread right away.

However, I still wonder what happened.  I had been using the Dapper for almost three months, without any audio problem (well except below).  Then yesterday, all of a sudden, my laptop did not come out of suspend and I had to reboot it.  After rebooting, the sound didn't work at all, neither speakers, nor jack.  Rebooted a couple of times since, no luck.  Then, when I tried alsamixer, I saw that the PCM bar was set to 0.  Increasing that fixed my problem.  What is PCM anyway?  And why did it get set to 0?  Where would I look in the logs to see what happened?

The other audio problem I have occasionally is that when I hibernate, the audio jack gets disabled after I resume from hibernation.  I get sound only from the speakers, plugging a jack into the audio out makes no difference.  Why is that, and how do I fix it?

---

### Post by lyve on 2007-04-28
> **lamy said:**
> If the above solution did not work on your m5405.  

Here is what worked for me:

1. Double click on the speaker volume Icon. 
2. Goto: File --> Change device, and make sure that "0: SI7012 (Alsa Mixer) is selected.
3. Click on the "Switches" tab.
4. Uncheck "External Amplifier"

If it still doesn't work, max out all of the volume levels. 

Hope it helps,

lamy

I was having the problem of sound via headphones but not speaker on my Acer 5050.  Double clicked on speaker volume icon.  Right device was selected but I didn't have an "External Amplifier" option on my "Switches" tab.  What I did though is click Edit->Properties.  I then added "Surround" as a track to be visible.  Once I activated that, I had sound.

Good luck!

---

