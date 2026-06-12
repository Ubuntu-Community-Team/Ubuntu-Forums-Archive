---
title: "asus m4a88t-m hdmi output?"
date: 2014-03-30
forum: Hardware
---

### Post by metroedged on 2014-03-30
I just received a samsung HDTV and it's not working with the DVI to HDMI adapter, so I'm wondering if I would have a better chance with onboard HDMI output on the motherboard. 

I can see the TV name in the display options, but it simply won't show anything on the TV.

12.04 lts, asus m4a88t-m

---

### Post by pqwoerituytrueiwoq on 2014-03-30
what gpu are you using? i know that motherboard has a HD 4250 GPU, but you implied you have a gpu insalled

---

### Post by metroedged on 2014-03-30
GTX 260.

With the dvi to hdmi, ubuntu detects the TV, but does not show any signal on the TV.

With the HDMI on the motherboard, I got the tV working 100% but there are LOTS of artifacts and the screen keeps flashing off and on. It goes blank if I full screen a video with VLC and keeps giving me "monitor does not suport GLX" or something error. I am assuming it's either the HDMI on the motherboard or ubuntu drivers that are causing this. The HDMI cable was used on a 55" TV and worked fine. I also used my netbook with the HDMI output and it also worked fine.

[IMG]http://i.imgur.com/rvpBqHw.jpg[/IMG]

[IMG]http://i.imgur.com/nlbTwad.jpg[/IMG]

---

### Post by pqwoerituytrueiwoq on 2014-03-30
what is the cable length, hdmi cables can be very picky at certain lengths

---

### Post by Yellow Pasque on 2014-03-31
> **metroedged said:**
> It goes blank if I full screen a video with VLC and keeps giving me "monitor does not suport GLX" or something error. I am assuming it's either the HDMI on the motherboard or ubuntu drivers that are causing this.

If you have the Nvidia drivers present, they will interfere with 3D on devices using open-source video drivers.

---

### Post by metroedged on 2014-03-31
> **pqwoerituytrueiwoq said:**
> what is the cable length, hdmi cables can be very picky at certain lengths

The cable is 10', but is working fine with my netbook and windows 7, as well as our cable box to 55" TV. For these reasons, I am fairly sure it's not the cable.

> **Temüjin said:**
> If you have the Nvidia drivers present, they will interfere with 3D on devices using open-source video drivers.

So are you saying that having the pci-e card's drivers installed will cause the onboard HDMI port to malfunction like this? 

What about this DVI to HDMI adapter It seems to allow the tv to be detected, but it won't show anything on the TV itself.

---

### Post by Yellow Pasque on 2014-03-31
> **metroedged said:**
> So are you saying that having the pci-e card's drivers installed will cause the onboard HDMI port to malfunction like this?

The port itself is not malfunctioning. It's a software issue with conflicting 3D drivers (specifically, nvidia proprietary drivers use a custom libglx.so).

---

### Post by metroedged on 2014-03-31
> **Temüjin said:**
> The port itself is not malfunctioning. It's a software issue with conflicting 3D drivers (specifically, nvidia proprietary drivers use a custom libglx.so).

Does that mean I can't use the oboard HDMI for secodary use and still use the graphics card for gaming?

---

### Post by Yellow Pasque on 2014-03-31
Off the top of my head, I don't know of a way to make them play nicely.

---

### Post by metroedged on 2014-03-31
Do you know of any way to get this TV to work in ubuntu?

Is there a DVI to RGB or coax converter that wouldn't ruin the clarity? Or even USB to USB?

Any idea why the DVI to HDMI adapter doesn't work correctly? Is there a way to figure out why it's just a blank screen?

---

### Post by Yellow Pasque on 2014-03-31
Maybe you have a faulty DVI to HDMI adapter? I know there are a lot of cheaper ones of varying quality floating around out there...

---

### Post by metroedged on 2014-04-01
> **Temüjin said:**
> Maybe you have a faulty DVI to HDMI adapter? I know there are a lot of cheaper ones of varying quality floating around out there...

It says ATI on it. I think it was from my 5770 a few years back. I'll try ordering another one and see if it changes anything. I just thought it was odd how ubuntu detects it but nothing shows up on the TV itself.

---

### Post by metroedged on 2014-04-01
I tried the onboard hdmi port with the 331 drivers uninstalled and it still looked like crap and seemed to black out the TV whenever I did anything remotely related to graphics...

---

### Post by metroedged on 2014-04-01
I bought a DVI to RGB 6' from ebay for $4. I'm hoping this works, otherwise I will just try and trade the TV for something with a VGA port.

---

