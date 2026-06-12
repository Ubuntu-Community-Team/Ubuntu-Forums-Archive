---
title: "Connecting GeForce 8600 GT 256mb to a 4k TV"
date: 2018-07-20
forum: Hardware
---

### Post by c@ssie on 2018-07-20
I just bought a used computer is running  Ubuntu_ mate 18.04.  It has an Nvidia GeForce 8600 GT 256MB DDR3 PCI-Express x16 Video Graphics Card, with 2 Dual-link DVI connectors. The previous owner had 4  1920x1080p monitors connected to it, but I want to connect a 4k (UHD) TV to it , which most likely won't have dvi ports. The reason I want to use a 43 inch TV is because it is half the price of a 32 inch 4k monitor.  Is there an adapter that will make this possible, and are there drivers to support it?

---

### Post by Frogs Hair on 2018-07-20
There are DVI to HDMI cables and converters available. I'm guessing it's a modern TV with HDMI slots. 

> DVI and HDMI use the same digital video format for the video. This means that if you are only using the video signal you can simply use an HDMI to DVI plug adapter or cable that simply changes the physical connections._ If you need to use the audio signal that’s on the HDMI connection you’ll need a fully active converter that can separate the video and audio signals apart, sending video over DVI and the audio over some other connection_. I use converter for my Raspberry Pi monitor.   [h=3][/h]

---

### Post by c@ssie on 2018-07-20
> **Frogs Hair said:**
> There are DVI to HDMI cables and converters available. I'm guessing it's a modern TV with HDMI slots. 

 I use converter for my Raspberry Pi monitor.   [h=3][/h]

I was hoping for more specific information.   The reason I'm asking here is that I already tried searching,and didn't  find an adapter cable that would work.  

Every TV I've  looked  at has HDMI, slots,  none had DVI.

---

### Post by Frogs Hair on 2018-07-20
Have you tried or considered something like the images ? You would need both the adapter and cable_ for video_ which are pretty easy to find. The first adapter connects to the graphics card and then connect the HDMI cable out to the TV. There are all in one cables available as well with DVI on one end and HDMI on the other end.

---

### Post by c@ssie on 2018-07-21
> **Frogs Hair said:**
> Have you tried or considered something like the images ? You would need both the adapter and cable_ for video_ which are pretty easy to find. The first adapter connects to the graphics card and then connect the HDMI cable out to the TV. There are all in one cables available as well with DVI on one end and HDMI on the other end..


 Yes, I have thought of that.  According to what I've read, that would get me only a 2560×1600 resolution.  I need something that would get me 4K (3820 x 2160).

---

### Post by oldfred on 2018-07-21
You cannot get more than card can output. And that is now an older card, probably before 4K existed.

[https://www.geforce.com/hardware/desktop-gpus/geforce-8600-gts/features](https://www.geforce.com/hardware/desktop-gpus/geforce-8600-gts/features)
> **Dual  Dual-link DVI Support: **
Able to drive the industry's  largest and highest resolution flat-panel  displays up to 2560x1600.  Available on select GeForce 8800 and 8600 GPUs. 

---

### Post by Frogs Hair on 2018-07-21
You can get a 4k graphics card with much more memory without spending a fortune. It might require using a proprietary driver for the Ubuntu repository.

---

### Post by c@ssie on 2018-07-21
> **Frogs Hair said:**
> You can get a 4k graphics card with much more memory without spending a fortune. It might require using a proprietary driver for the Ubuntu repository.
Any recommendations for a good, low cost card that will out perform my geforce 8600 GT?

---

### Post by Yellow Pasque on 2018-07-21
What is the refresh rate of your TV?
For 30Hz, you need a Geforce GT(X) 600 series or later or RadeonHD 7000 series or later, and ideally >=2GB VRAM.

---

### Post by c@ssie on 2018-07-22
> **Temüjin said:**
> What is the refresh rate of your TV?
For 30Hz, you need a Geforce GT(X) 600 series or later or RadeonHD 7000 series or later, and ideally >=2GB VRAM.
120 hz

---

### Post by Frogs Hair on 2018-07-22
120 HZ refresh rate may push you into a higher price range. I was about to recommend the card I use which will handle the resolution but not @ 120 HZ. Search for 4K graphics card and look at sites with detailed specifications, specifically max resolution.

Example only:

---

### Post by oldfred on 2018-07-22
Do you really need the 4K at 120hz?
Not much programming is 4K at all. Much of the hype on 4K tv's was to have something newer to sell as prices of standard HD 1080 TVs has plummeted. Note: I do have 4K tv, but cable currently only offers 1080. My Amazon account has a few 4K shows, but doubt if 120hz.

If you need a very high end video card, you will also need very high end system to support it.

I suggest you buy a low cost 1080p monitor for computer and use Netflix or Amazon as they are about the only 4K sources currently available. In future there will be more, but things may change by then and lower cost new system then will support TV.

---

### Post by Yellow Pasque on 2018-07-22
The TV may do 120Hz, but it probably won't accept any input above 60Hz from a PC.

If you want 4K@60Hz, you need a card with an HDMI 2.0 output and a capable cable: [https://en.wikipedia.org/wiki/HDMI#Cables](https://en.wikipedia.org/wiki/HDMI#Cables)
Or you would need a card with DisplayPort >= 1.3 output and use an adapter (and the correct HDMI cable).

I would be looking at cards like Geforce 1050 or Radeon Rx550 as modern versions of the card you have now.

---

