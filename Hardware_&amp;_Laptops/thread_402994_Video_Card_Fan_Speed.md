---
title: "Video Card Fan Speed"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by Megatog615 on 2007-04-06
Is there an application for Linux that can control fan speeds for video cards, much like RivaTuner for Windows?
In RivaTuner there are three options for selecting fan speeds depending on the video card's usage. There's 2D, Performance 3D, and Full 3D modes. Is it possible to set options like these in Linux?

---

### Post by marcantonio on 2007-04-06
What kind of video card do you have?  Some drivers allow you to set the power level of the card to different levels.  For example, the 'official' drivers for ATI allow you to set one of three levels:

```
$ aticonfig --lsp
    core/mem      [flags]
-----------------
* 1: 209/135 MHz  [low voltage]
  2: 392/252 MHz  [default state]
  3: 425/378 MHz  [performance mode]

```

Running ```
$ aticonfig --set-powerstate=1
``` slows the fan greatly and improved battery time.

HTH
Marc

---

### Post by Megatog615 on 2007-04-07
I have an NVIDIA Geforce 7800GT.

---

### Post by marcantonio on 2007-04-07
> **Megatog615 said:**
> I have an NVIDIA Geforce 7800GT.

I seem to remember a program called [nvclock]("http://www.linuxhardware.org/nvclock/").  I don't have an NVIDIA card at present so somebody else could probably answer this better than me.

---

### Post by xjgnsdof on 2008-04-04
I have an 8800GTS 512 and would also like to control video card fan speeds. Specifically, I would like my fans to spin up automatically upon booting into Ubuntu. Unfortunately, I haven't gotten NVClock to do that...

---

### Post by xjgnsdof on 2008-04-05
I've figured out how to set the graphics card fan speed to run at startup using NVClock (which allows for overclocking as well):

1)Download NVClock from [http://www.linuxhardware.org/nvclock/#download](http://www.linuxhardware.org/nvclock/#download)
2) Extract the package to home folder
3) cd nvclock0.8b2
4) ./configure
5) make
6) sudo make install
7)To set video card fan speed to run at startup, input nvclock -f -F X into “Sessions,” where X = % maximum fan speed (I set it to 75, or 75% maximum fan speed, because I don't mind the extra noise in exchange for added stability)

---

