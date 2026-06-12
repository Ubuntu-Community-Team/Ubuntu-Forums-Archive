---
title: "Asus Xonar D2/PM supported?"
date: 2008-04-25
forum: Hardware
---

### Post by isecore on 2008-04-25
Due to the recent Creative/Soundblaster-debacle I'm considering tossing my Audigy2 ZS out the window. My onboard sound however isn't really up to what I want, so I'm looking for a replacement.

I found the [Asus Xonar D2/PM]("http://www.asus.com/products.aspx?l1=25&l2=144&l3=0&l4=0&model=1769&modelmenu=1") which seems to be a very capable card, and I'm wondering what kind of support it enjoys under Linux, in my case plain 64-bit Ubuntu. I've searched but haven't quite found anything definitive, so I figured I'd throw the question out here instead.

---

### Post by kpel on 2008-04-25
I don't know about that card, but I find that my Xonar DX doesn't work on a clean Hardy install.  I'm not surprised, given that Asus doesn't have Linux drivers out for the card and considering that it's only been out for a month or so.

I plan to spend this weekend trying to make it work, but I've never tried that sort of thing so I have no idea what kind of success I'll have (if any).

---

### Post by isecore on 2008-04-25
I'd appreciate any feedback from you. I want to ditch my Soundblaster-card and never buy another product from Creative again. The D2/PM seemed like a nice card, but it's useless if it doesn't work in Ubuntu.

---

### Post by alphomega on 2008-04-30
I dont know if this helps you but I can confirm the Xonar D2X works out of the box with Hardy

[http://www.asus.com/products.aspx?l1=25&l2=150&l3=0&l4=0&model=1989&modelmenu=1](http://www.asus.com/products.aspx?l1=25&l2=150&l3=0&l4=0&model=1989&modelmenu=1)

---

### Post by isecore on 2008-05-02
> **alphomega said:**
> I dont know if this helps you but I can confirm the Xonar D2X works out of the box with Hardy

[http://www.asus.com/products.aspx?l1=25&l2=150&l3=0&l4=0&model=1989&modelmenu=1](http://www.asus.com/products.aspx?l1=25&l2=150&l3=0&l4=0&model=1989&modelmenu=1)

Excellent. That's good to know. As far as I can tell the D2X and D2/PM are identical cards, except that the D2X uses the PCI-E 1x bus and D2/PM uses PCI.

---

### Post by Konikov on 2008-07-24
isecore, could you possibly tell me whether your Xonar really worked 'out of the box' or not? I'm going to sell my crappy Creative X-Fi and buy one of D2X.

---

### Post by isecore on 2008-07-24
> **Konikov said:**
> isecore, could you possibly tell me whether your Xonar really worked 'out of the box' or not? I'm going to sell my crappy Creative X-Fi and buy one of D2X.

I wish I could, I haven't actually bought one yet. Still using my Audigy2 ZS while waiting for my finances to improve enough so I can buy one.

---

### Post by MrHippocampus on 2008-07-24
I did an Audigy2 ZS to Xonar D2 upgrade a couple of months ago and I don't remember having any problems. Its well worth the upgrade too as the Xonar D2 sounds much better :).

---

### Post by Konikov on 2008-07-24
I.e. it worked 'out of box'? :) Do you use ALSA or OSS?

---

### Post by MrHippocampus on 2008-07-25
ALSA pretty much, although for hardy most stuff goes through pulseaudio so in theory it shouldn't matter.

---

### Post by Trollslayer on 2008-08-09
D2 analogue is working but not digital. This is with ALSA 1.0.17.

---

### Post by isecore on 2008-08-09
> **Trollslayer said:**
> D2 analogue is working but not digital. This is with ALSA 1.0.17.

Dang, I kinda need that to work.

---

### Post by d0b33 on 2008-08-19
> **Trollslayer said:**
> D2 analogue is working but not digital. This is with ALSA 1.0.17.

Digital works for me "out the box" using hardy.

Just go system > preferences > sound.  select digital for playback.

Coaxial BTW have not tested optical.

---

### Post by Konikov on 2008-08-19
I have Xonar DX and Ubuntu Server Edition 8.04 and it doesn't work despite of installing alsa 1.0.17...

---

### Post by MrHippocampus on 2008-08-19
> Digital works for me "out the box" using hardy.

Just go system > preferences > sound. select digital for playback.

Coaxial BTW have not tested optical.
Optical works fine for me out of the box, (and this is without needing to install a new ALSA btw).

---

### Post by d0b33 on 2008-08-19
> **MrHippocampus said:**
> Optical works fine for me out of the box, (and this is without needing to install a new ALSA btw).

Good to know :guitar:

I'm using the D2/pm so I can confirm that sound works with this card.

---

### Post by d0b33 on 2008-08-22
After taking a closer look it seems that the card does not always function on optical or coaxial digital for me, some applications don't recognize the card in digital mode but it works 100% using analogue mode.

Hope to see a fix soon.

---

### Post by aleb on 2008-11-24
I understand the Asus Xonar D2 card is supported, at least by ALSA:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)

I'm looking at the Xonar D2X specifications, Driver Features:
[http://www.asus.com/products.aspx?modelmenu=2&model=1989&l1=25&l2=150&l3=0&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=1989&l1=25&l2=150&l3=0&l4=0)
It seems like most of those are lost on Linux.

Do you know if there is any OpenAL library which can use this card? ..efficiently?

Thanks!

---

### Post by Konikov on 2008-11-25
D2X is supported, but, as far as I know, Linux driver doesn't give you all of those options that has windows driver. I've seen only such options: "Mic boost", "Stereo Upmixing", "IEC958", etc.

---

### Post by aleb on 2008-11-26
> **Konikov said:**
> but, as far as I know, Linux driver doesn't give you all of those options that has windows driver. I've seen only such options: "Mic boost", "Stereo Upmixing", "IEC958", etc.

etc?

Xonar D2 and most of the new soundcards have very powerful chips. I want to know how well those are used in Linux. To generalize the question, is there any "new" soundcard which can be fully used by a Linux system? I'm mostly interested whether all that power can be used for 3D sound, OpenAL..

---

### Post by Konikov on 2008-11-27
> **aleb said:**
> is there any "new" soundcard which can be fully used by a Linux system?

The answer is simple: "no". Drivers for your Xonar don't support any presets, effects... You have only stereo, no EAX or something like that. So it is only good for listening to the music on your hi-fi.

---

