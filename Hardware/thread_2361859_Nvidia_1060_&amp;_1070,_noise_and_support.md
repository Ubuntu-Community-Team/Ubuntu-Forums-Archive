---
title: "Nvidia 1060 &amp; 1070, noise and support"
date: 2017-05-21
forum: Hardware
---

### Post by nigro.orlando on 2017-05-21
Hi!
I was thinking about getting one of this two cards. 

I use windows for gaming and I what I expect from the GPU in linux is good and simple performance for video editing and watching movies. Beside that is very important for me that when the card is on idle the fans are quiet with 0 noise.  
Many cards have this functionality but my experience in this regard is been disappointing on linux.
Before buying I want to be sure that I can get this for me very important characteristic.

Does anyone who have on these two cards confirm that they work well on linux and the fans are still, =no noise when the card is not under load?

---

### Post by Bucky Ball on 2017-05-21
I don't own either, but can confirm that the 1060 works fine in Ubuntu from what I have read here. The driver is in 'Additional Drivers' so easy.

I do own the GTX 970, their slightly older sibling, and the only time I have ever hear that is when I'm rendering HD in Blender, and it is certainly not annoyingly loud, or even that loud. In fact, it is a warm hum that gives me a nice feeling (because I know it is busily working for me :)).

Be aware that the NVidia GTX 1060, or the other, are the generic NVidia devices. NVidia's product is then incorporated by various manufacturers in their devices and designs; for instance, my card is actually an ASUS Strix GTX 970 (read NVidia GTX 970 badged up by ASUS and sold with their own tweakage and hardware additions). In other words, the GTX 1060 will make different amounts of noise depending on which manufacturer has decided to use it and how they've done that. 

My Strix is supposed to be one of the noisier ones. Could have fooled me.

Something to look out for as there will be many versions of the 1060, is that different manufacturers offer different display outputs. For instance, mine has a display port, a HDMI port, a DVI port and another older style port. I could have gone for something with a different configuration of ports, for instance two HDMI ports. Make sure you go for what suits your requirements.

I come from the world of pro-audio and my AV machine is used mainly for audio editing, so quiet is essential. I don't want the machine louder than the violins I'm trying to compose with or arrange or anything else! I am also extremely susceptible to louder noises and find it impossible to concentrate with too much loud whirring right next to me (or the guy across the road mowing his lawn). I haven't had problems with the GTX 970 and imagining the GTX 1060 might be a similar non-issue, but sure others will confirm.

Hope that is of some help.

---

### Post by nigro.orlando on 2017-05-21
thank you for the answer, it was very helpful information and I totally understand your need for a quiet machine. I for instance have a projector for watching movies that sometimes I need to connect to the computer, in this case I don't want the computer to be loud since the projector makes little noise already.  

I was thinking about a Asus Strix or a MSI gaming but I haven't decided yet. They both have technology that keeps the fans from spinning under 50/60 degrees and if this technology is supported by the linux driver I will be more then happy to take one of them. 
If your 970 is silent when on idle I guess it's because it also has a similar technology that seems to work with the additional driver, could it be so?

If this is your card it looks like it also says the fans to stop below a certain temperature:
[https://www.asus.com/us/Graphics-Cards/STRIXGTX970DC2OC4GD5/](https://www.asus.com/us/Graphics-Cards/STRIXGTX970DC2OC4GD5/)

---

### Post by Bucky Ball on 2017-05-21
Not a Linux driver. It is an NVidia driver that is in the Canonical Partners repository and you will find it in 'Additional Drivers'. Just type 'Additional Drivers' in the 'Dash' when you've installed Ubuntu and updated and you will find the NVidia recommended driver right there. Just click it to enable it and restart. :)

(PS: You may need to go into 'Software and Updates' and enable the Canonical Partners repo prior to update, can't remember.)

(PPS: Yep, that's a my card!)

---

### Post by nigro.orlando on 2017-05-22
Yes of course, I meant the linux proprietary driver that is easily installed in additional drivers. I have had Nvidia cards in the past :). 

What about the open source one? Is it ok? Because if the open source also support the silent technology I might stick to it instead of the proprietary

---

### Post by Yellow Pasque on 2017-05-22
The open source nvidia driver ("nouveau") is practically unusable for GTX 900/1000 cards. It is stuck at minimum clocks because Nvidia has not released the necessary signed firmware blobs for the nouveau devs to use.

---

### Post by efflandt on 2017-05-22
I have a 3 GB GTX 1060 (Asus Dual OC) and it works great with nvidia drivers for Steam gaming on my 32" 1080p HDTV. The OEM PSU on my old Dell only has (1) 6-pin connector (some GTX 1060's use 8-pin). I am currently using nvidia-378 drivers, but the graphics-drivers ppa also has nvida-381 package. The twin fans on the card barely silently spin up a few % from their 33% minimum during graphics benchmarks.

---

### Post by nigro.orlando on 2017-05-24
I took the card and I can confirm that the particular technology I was looking for is supported both by nouveau and the proprietary driver! 
This MSI 1070 is completelly silent as I wanted it.

---

