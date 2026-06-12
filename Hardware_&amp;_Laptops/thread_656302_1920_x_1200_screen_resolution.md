---
title: "1920 x 1200 screen resolution"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by ogden-quin on 2008-01-02
Hello all,
firstly i'm very new to all this... linux thing!
My laptop runs windows vista @ screen res of 1920 x 1200.
after installing the feisty fawn 7.04 with updates the max screen res I can acheive is 1024 x 768.
I have a NVidia Graf card 512mb I think it's a 950 or 750 somthing or other.
I have installed the ristricted drivers.

Is this realy the best screen res I can look forward too?

I'm an artist so screen quality is everything, I would hate to have to halt my Linux foray right here at the start!

Please help!

---

### Post by jespdj on 2008-01-02
First, find out exactly what kind of video card you have. Open a terminal window (Applications / Accessories / Terminal) and type in the command:
```
lspci | grep VGA
```
Then check the hardware compatibility lists to see if that video card is supported or not. If it's indeed an nVidia card and it's not a really old model, then it should be supported.

Post the output of the command here, maybe there are people who have the same video card who can provide more information on how to get it working.

---

### Post by ogden-quin on 2008-01-02
OK here goes...

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0297 (rev a1)

Hows that

---

### Post by timcredible on 2008-01-02
my laptop runs 1920x1200 right after installing ati drivers.  but i'm running 7.10, maybe you should upgrade

---

### Post by jespdj on 2008-01-02
Hmm, it looks like the driver you are using does not recognise the video card properly...

According to [this list]("http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/appendix-a.html"), your card is an nVidia GeForce Go 7950 GTX.

You can probably get it working by installing a newer nVidia video card driver. Installing a new driver can be a bit difficult, especially if you're totally new to Ubuntu and Linux... Probably the easiest way to do it is by using [envy]("http://albertomilone.com/nvidia_scripts1.html"), a tool to automatically detect and install video drivers for Ubuntu (I have never used envy myself, so I can't tell you exactly how to use it).

---

