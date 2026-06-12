---
title: "HP OmniBook XE3 1Ghz"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by stuartc1 on 2006-06-19
Hi,

Yes, I'm new here - hello guys :)

I've recently installed Dapper Drake 6.06 on my HP OmniBook XE3 laptop - the system has 1Ghz Processor with 2GB HD... this is all I know of the spec as I just bought it secondhand.

So far everything works as expected - the problem I have it how to identify the videocard? I want to instal the XGL cube desktop, but it looks like the installs are based on graphic/video cards. Can anyone give some advise on how to go about getting XGL running? I've heard that it should work OK on systems with 1Ghz processors (Intel).

Many Thanks,
Stuart

---

### Post by K.Mandla on 2006-06-19
Try typing this into a terminal:

```
lspci
```
It should spit out a list, and one of those things should be a graphics card.

XGL is all about the video card, by the way. The slowest machine I ever put it on was a 1Ghz P3 with a 64Mb Nvidia GeForce 440 in it. It worked fine, but less video memory would probably make it a no-go.

---

### Post by mitchell7 on 2006-11-25
Hmmm... It seems strange to me that you only have a 2G Hard Drive in that laptop. I think that if you got it used, someone replaced the drive on you. I have an Omnibook XE3 GF (1.06Ghz CPU), and the stock drive in mine was 30G.
Anyway, that's neither here nor there. To address your questions (if you don't already have the answers, that is...) : The video chipset used by the XE3 is the Intel 830M chip. It's okay, I guess, but there are a whole lot of apps that don't get along with it. Correction-- WINDOWS apps. It's part of the reason that I switched to Ubuntu. The only real issue that I can trace to the chip itself is that Ubuntu can't get the basic resolutions from the chip (or the BIOS) on startup. So the only resolution I get is 1280 X 1024 at 60 Hz, after I got used to much higher. So now I have to get used to not using all of my display. (I've tried everything I've been advised, and nothing changes, by the way) But other than that, I've been really happy with the OS. everything else worked, right out of the gate. A couple of days after its release, I upgraded to Edgy, and it runs like a charm. So have fun, and don't be afraid to pack all the stuff you want onto your system!

---

