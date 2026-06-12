---
title: "cant install 22.04 but 20.04 is ok"
date: 2024-02-12
forum: Hardware
---

### Post by vasso2112 on 2024-02-12
I have a several supermicro servers and Im trying to install ubuntu server on it from usb. after switching on a server I got welcome page to install ubuntu then press it and stuck on black screen.
If I perform the same actions with ubuntu server 20.04 it works fine.
I checked different usb stick and downloaded image several time and check it's hash.
I guess support of some hardware was removed from the image but how can I prove it and solve. what was removed exactly and why?

---

### Post by MAFoElffen on 2024-02-13
I have 2 SuperMicro Server Boards. Both of mine use Matrox Marvel MGA-G200 iGPU. For mine, even when installing from the Server Edition ISO, I add this boot paramter to the Grub2 'linux' boot line as a parameter:
```

video=uvesa:1920x1080-32@60,mtrr:3,ywrap,noblank

```
But I really have to check the 'videoinfo' results from the Grub prompt to match what is seen by Grub2 and the BIOS/Display combination. My experience with Matrox VGA is that it is challenged by acquiring the Display's EDID, so you have to help it along, by setting the resolution manually.

Yes, that is a framebuffer driver, and the Server graphics is a VGA graphics layer in console unless you set it to strict 'init 3' (text only), by passing the boot parameter '3'.

They both run the Server LiveInstaller, which started with that flavor of the installer in 20.04, with more changes with 22.04... But I know the quarks of my MB's so I always used those boot paramters with them.

---

