---
title: "My machine &amp; Feisty"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by Yoeri on 2007-04-23
Just a little post to tell my frustrations with Ubuntu (Linux in general).

I have an ASUS A4K laptop AMD64 3200+ with an ATI Radeon 9700 Mobility. I run Edgy for about two months now and I like the environment in a way that I only use windows to draw something in Visio. I have a windows server so with Feisty I can completely switch my laptop and use virtualisation to run Visio.

Some general thoughts ...
[LIST]
[*] Networking evolved since Edgy, I can now see my wireless adapter (ZD1211) in networkmanager, however I cannot connect to a network. This seems to be a general problem (see posts in the wireless section of this forum). Solution?? I don't know, but am planning to recompile the kernel with the drivers I used on edgy.
[*] Video card... disaster as always. This is not the fault of the ubuntu team since the problem lies within the kernel (see [http://bugzilla.kernel.org/show_bug.cgi?id=6350)](http://bugzilla.kernel.org/show_bug.cgi?id=6350)). There are two problems with the video card:
[LIST=1]
[*] When using the non-proprietary drivers, everything works like a charm except the fact that the card cooler is constantly on wich drains my battery. So this is unacceptable.
[*] When using the proprietary drivers, the fan only works when nessecary. BUT 3d accelleration is a no-go (kernel-bug) and I often have artifacts. Sometimes the artifacts are that bad that I can't read some text on the screen.
[/LIST]
[/LIST]

The strangest of all is that the video card works as expected when booting the live-cd. It uses the non-proprietary drivers and the fan is quiet. 3D works not hardware-accellerated.

Hope for solutions soon ... in the mean-time, I can live with the artifacts ... in my opinion, Linux not ready for mass-desktop usage ...

---

### Post by tact on 2007-04-23
I gotta say that a different person on a different laptop can easily have a totally different point of view.  (I will open a different thread on this as its technically off topic here) -  but just to give a different perspective ....first Edgy and later Fiesty both found and worked fine with all the hardware in my company issued Dell D410 laptop.  Not a single issue even running Beryl every day productively on a corporate world business laptop.   (I truly find Beryl a definite productivity aid, seeing all open windows and flicking between then while in heavy cut/paste master document creation mode....hhehehe)

And as a result I'd be saying its definitely ready for the mass desktop useage.  Corporate world even.  :)

---

### Post by Yoeri on 2007-04-23
I know, it depends completely on the first impression. I've always been a Windows user at home and at work. Since I am sick and tired of constantly searching for cracks and avoiding software protection schemes for occasional use I switched to Linux and I like it. I am a developer, so I am not afraid of recompiling the kernel with other drivers ... just the fact that I have to do it means that there is something fundamentally wrong. Look at the threads about the wireless problems in Feisty, it is not only my hardware, a lot of people are suffering the same problem while Feisty is touted to have good wireless support. Good is not good enough ...

I don't want to criticize anything but seamless support for wireless should not result in a manual kernel-recompile....

Oh, Beryl looks very nice ... on YouTube, not on my machine ... although only the bios/hardware vendors are to blame for their windows-friendly business...

If I knew this, I would have bought other hardware ...

---

### Post by mxt on 2007-04-28
I have an a4k and the fglrx drivers work without problems.. 
Try to remove the package xserver-xorg-video-ati, and reboot. I hope it helps..

---

### Post by Yoeri on 2007-04-29
I finally got everything working ... back on Edgy ...

FGRLX works for the first time in my Linux history (almost 2 years!!!!)
I never tried the mtrr-fix for getting 3D acceleration ... tried it now and it just works.

I love the UI with beryl enabled, just gives a far nicer experience...

If I could only get my wireless working with feisty ...

Why can't they include the mtrr-fix automatically (via an option)... there are a lot of people suffering from this bug

---

