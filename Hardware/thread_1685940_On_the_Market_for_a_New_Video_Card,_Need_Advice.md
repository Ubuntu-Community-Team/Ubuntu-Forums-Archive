---
title: "On the Market for a New Video Card, Need Advice"
date: 2011-02-11
forum: Hardware
---

### Post by marenum on 2011-02-11
My video card died on me yesterday, so naturally I am looking to replace it in the next few days. I'm not really confident enough to pick one myself; a friend helped me build the computer originally.

One of my issues is that I'm not sure which chipset I have. I'm pretty sure I have Nvidia, my old card was an Nvidia GeForce 8600 GT, but I have an AMD processor so I wanted to be sure. 

I'm also not sure which cards are good (brands, models, etc.) I don't do a whole lot of gaming on my PC, but I like to use a few desktop effects, and I like hooking up my Sony Bravia via DVI or HDMI. I watch a lot of HD video, my old card could only handle 720p, but I'd like one that can do 1080p. 

If anyone has a moment and could steer me in the right direction, I'd be quite grateful. Thanks.

---

### Post by marenum on 2011-02-11
Any input is appreciated.

---

### Post by jerrrys on 2011-02-11
i don't think that video cards a a big issue anymore.  make sure you get the right kind like PCI or PCI-X.

here's a site that may help
[U][http://www.linuxquestions.org/hcl/]("http://www.linuxcompatible.org/compatibility.html")

this link will not post for some reason' sorry
[/U]

---

### Post by marenum on 2011-02-11
I'm more concerned with what will work with my chipset, does anyone know?

---

### Post by P4man on 2011-02-11
For linux, and especially to play HD movies, you want an nvidia card. If your requirements end there (you dont mention gaming), then any nvidia card on the market will be plenty. In fact your old 8600 should have been plenty to play 1080 video's, provided you install VDPAU and use a videoplayer that leverages it (smplayer, vlc, xbmc,..) and you configure it to use it. My HTPC has an nvidia 8400 with an old single core A64 and it decodes 1080p h264 with ease, the cpu is barely used.

Your only concerns ought to be: slot type. Do you have AGP or PCI-E slot? If its AGP, it might be tricky to find something. And possibly, power consumption/connector, if you have a weak powersupply and/or if you dont have PCI-E 6 pin connectors, then you need a  a card that doesnt need them (which is the case for most lowend cards).

edit: oh, and get something with HDMI out for convenience.

---

### Post by marenum on 2011-02-11
Thanks for the reply. I do have PCI-E. I was unable to play 1080p with the 8600 gt, but I don't think I had VDPAU installed. I do a small amount of gaming, but nothing my old card couldn't handle. I'll look at some other NVIDIA cards.

---

### Post by cascade9 on 2011-02-12
> **marenum said:**
> Thanks for the reply. I do have PCI-E. I was unable to play 1080p with the 8600 gt, but I don't think I had VDPAU installed. I do a small amount of gaming, but nothing my old card couldn't handle. I'll look at some other NVIDIA cards.

If you wee happy with the 8600GT, then a GT220 or GT430 would be the best replacement card. 

They should be at least as fast as the 8600GT, run cooler, use less power and have good linux support. They also have good VDPAU support as well. (+1 to P4man on VDPAU BTW).

---

