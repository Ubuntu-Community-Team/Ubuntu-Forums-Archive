---
title: "Kernel framebuffer vga= parameter"
date: 2008-08-26
forum: General Help
---

### Post by uid313 on 2008-08-26
If you do not specify any vga= parameter, then what is the default value it uses?

What is the value for 1920x1200?

---

### Post by Vivaldi Gloria on 2008-08-26
> **uid313 said:**
> What is the value for 1920x1200?

From

[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

You can use the modes you see in

```
sudo hwinfo --framebuffer | grep Mode
```

---

### Post by uid313 on 2008-08-26
Just tried that.
I completely lost all my terminals then.
Had to edit menu.lst and change it back.

---

### Post by Vivaldi Gloria on 2008-08-26
> **uid313 said:**
> Just tried that.
I completely lost all my terminals then.
Had to edit menu.lst and change it back.

What is the vga=? line you tried? Also, what is the corresponding line from the output of "sudo hwinfo --framebuffer | grep Mode" ?

---

### Post by kerry_s on 2008-08-26
> **uid313 said:**
> If you do not specify any vga= parameter, then what is the default value it uses?

What is the value for 1920x1200?

default is vga=normal

it does not go that high:

```
Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795

```

---

### Post by uid313 on 2008-08-27
> **Vivaldi Gloria said:**
> What is the vga=? line you tried? Also, what is the corresponding line from the output of "sudo hwinfo --framebuffer | grep Mode" ?

```

$ sudo hwinfo --framebuffer | grep Mode
  Model: "NVIDIA GW-P/N@PM898486GTQ14P:0"
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits

```
I tried vga=794 and vga=0x037d.
Someone in #ubuntu-dev told me that uvesafb was buggy in Intrepid Ibex (which is what I use).

---

### Post by uid313 on 2008-08-27
> **kerry_s said:**
> default is vga=normal

it does not go that high:

```
Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795

```
What does 'normal' equal to?
Is it 769? (256 (8bit) 640x480))

---

### Post by kerry_s on 2008-08-27
> **uid313 said:**
> What does 'normal' equal to?
Is it 769? (256 (8bit) 640x480))

i have no idea what it actually runs at with "normal", i tried looking it up 1 time but got nowhere. to me it looks like it's running at 800x600@16, but i could be wrong.

---

### Post by uid313 on 2008-08-29
I tried vga=795 but it doesn't work.

I loose all my terminals.
The only thing I see is a little whtie blinking underscore _ that blinks on my black backgroudn. And it is like normal low-res resolution.

---

### Post by unutbu on 2008-08-29
Have you tried "vga=ask" ? Using that option, a menu should come up showing you all the options available to you.

---

### Post by uid313 on 2008-08-30
Perhaps this is a bug with vesafb / uvesafb and v86d.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269)

---

