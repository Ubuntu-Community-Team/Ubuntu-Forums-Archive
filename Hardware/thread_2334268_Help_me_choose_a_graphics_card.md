---
title: "Help me choose a graphics card"
date: 2016-08-17
forum: Hardware
---

### Post by james_beat on 2016-08-17
I recently started building a retro gaming console, which is nothing more than an old PC with Ubuntu running Retropie.

I actually put this together to test Retropie out before springing for a Raspberry Pi 3, but then I realized that it performed so much better than the Pi 3 that I would be better off not bothering with the Pi at all.

It's an HP 5800 small form factor desktop.
These machines came with an on-board GPU which is no longer supported, but it works great for everything except N64 games.
I borrowed a graphics card from another machine to see if that would help, and it worked perfectly.
Unfortunately, I can't keep this graphics card in the machine for two reasons; it doesn't belong to me, and it doesn't have the right outputs.

I'm hoping that I can get some suggestions for graphics cards that will give me similar performance, but with these features:

HDMI out, including audio.
This is important, because my TV can't accept a separate audio input when using HDMI.
The other video card that I tried had DVI output. I used a DVI to HDMI adapter, but could not get sound because the TV expects sound over HDMI.

Similar performance to the other card I tried.
It was a GEForce 9000 series.
I don't dare go lower than this for fear that it won't have enough grunt.

Cheap!
I want to pay as little as possible. I have $40 left in my budget after buying controllers etc, and I I still have to get a good Bluetooth dongle and a couple of other odds and ends.
I'd like to spend $25 or less if possible. There are loads of graphics cards that look like they might be suitable on eBay at around this price.

Plug and play.
The last card I tried just worked. I'd like this one to be the same. This is supposed to be a fun project, and I really don't want to have to mess around with drivers.
I'm concerned that getting audio over HDMI might need some sort of driver, but it's been a long time since I have done anything hardware related with Ubuntu.

Sorry for the long post, please help!

---

### Post by CatKiller on 2016-08-18
Since your budget is so tight, get the best NVidia card you can find second-hand that you can afford. Spec sheets are all over the Internet, so you'll be able to check that it has a HDMI port.

Sound is handled by a different system than the graphics system, so as long as you have the port you'll be able to route the audio through it.

Having said that, the Raspberry Pi 3 works out of the box with Linux, has Bluetooth and HDMI, and is probably cheaper than a second-hand graphics card and Bluetooth dongle. I've been very pleased with mine.

---

### Post by mastablasta on 2016-08-18
some older nvidia cards did not support sound via HDMI.

---

### Post by CatKiller on 2016-08-18
> **mastablasta said:**
> some older nvidia cards did not support sound via HDMI.

That's interesting; I didn't know that. Since HDMI is DVI video + audio + DRM, I'd assumed that anything that bothered to use an HDMI port rather than DVI would also support the audio routing.

To the OP: anything after about 2008, then, which is when the GPU makers started implementing HDMI properly. Since you'll be checking the specs anyway to check for ports, you'll be able to confirm the audio passthrough at the same time.

---

### Post by james_beat on 2016-08-18
I should have been more clear about the Pi - I actually have one on order (it's due to arrive today in fact) but after seeing its poor performance with N64 emulators, I'm going to return it.

Don't get me wrong, I love the Pi, in fact I own a couple of the earlier models, it just isn't capable of doing what I need it to do.

So do HDMI graphics cards output sound, (ie do they have built in audio hardware) or do I have to physically hook up my sound card to it?

As you can probably tell, I have very little experience with this aspect of hardware, onboard graphics have always been sufficient for my needs in the past.

Thinking about it now, I didn't install any drivers when I tried out this graphics card, I just plugged it in and it worked. 

Is it possible that it wasn't actually using any drivers?
If that is the case, why did it perform better than the onboard graphics?
Could it simply be because it had more memory?

---

### Post by CatKiller on 2016-08-18
If the Pi doesn't have the performance you need, then fair enough. One of mine is a Minecraft server and the other's a music server, so I've not played around with emulators on them.

The audio is all digital; it would be decoded by the receiving device - your TV in this case.

The reason the graphics card performed better was because it was better. It's only in the past few years that integrated graphics have approached the performance of discrete cards.

The open source driver is included and enabled by default. The Intel one works well because it's the only one available, the AMD one works moderately well since the proprietary one is a bit rubbish, and the NVidia one is merely functional because the proprietary driver is pretty good & everyone just uses that. Developer time and interest is a finite resource. But that's why you don't really need to do anything when you put the card in. People install different drivers for AMD and NVidia cards for more performance or different features.

---

### Post by james_beat on 2016-08-18
I think it's becoming clearer now, thanks.

So, in theory, as long as I make sure that I buy an Nvidis card that is capable of outputting audio over HDMI, I should just be able to plug it in and ubuntu will know what to do with it?

---

### Post by CatKiller on 2016-08-18
Yep. And if you find that you'd like more 3D performance, which you probably won't if you're just running emulators, the Additional Drivers tool will select the most appropriate proprietary driver and install it for you. For 2D stuff the open source driver is just as good.

---

### Post by james_beat on 2016-08-18
Yes, I don't think any of the emulators use 3D in any meaningful sense.
N64 and PSX games are in 3D, but I think it's all done by the CPU, I don't think the emulators are able to utilize the 3D features of graphics cards.

I ordered a GeForce 8400 GS, which does have audio, and appears to work ok with audio over HDMI from forum posts that I have found.

Now I just have to figure out how to get my controllers connected with Bluetooth....

Thanks guys :)

---

### Post by SeijiSensei on 2016-08-18
In my experience you'll need to use the proprietary driver for HDMI audio.

---

### Post by james_beat on 2016-08-18
That ok, as long as the proprietary drivers are easy to install. I believe they can just be downloaded and installed from a menu nowadays.
What I was afraid of was repeating my experience a few years ago when I had to use ndiswrapper to get a WiFi adapter working. It took forever to get the thing working, and it was really flakey even then.
That's the kind of 'driver dance' that I was hoping to avoid.

---

