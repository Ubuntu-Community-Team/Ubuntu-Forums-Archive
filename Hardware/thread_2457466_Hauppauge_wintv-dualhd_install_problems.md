---
title: "Hauppauge wintv-dualhd install problems"
date: 2021-02-02
forum: Hardware
---

### Post by rustytone on 2021-02-02
hello all, im new to linux, ubuntu is my first install, so i dont know any of the terminal commands etc, total linux noob
the system drivers installed fine, ive got a asus essence stx sound card and gtx 660 i3 8100 installed fine

the only thing that didnt install correctly was the hauppauge wintv-dualhd usb tv tuner

i have followed the steps on the offical tv tuner site ([https://hauppauge.com/pages/support/support_linux.html](https://hauppauge.com/pages/support/support_linux.html))

im running ubuntu lts 20 i think its hwe version so i installed that package for the tv tuner rebooted didnt work, so i installed the other package, rebooted and still nothing.

is there any extra steps required for the tv tuner to work? this is the only thing not working properly in my system so far.

overall very pleased with ubuntu so far, looking forward to speaking to you all and learning the coding language. thanks.

---

### Post by CelticWarrior on 2021-02-02
Welcome.

If you did exactly as instructed (except installing the non-HWE package, that was a mistake and probably better remove it before anything else) it should work.
How exactly have you determined it isn't working? With which software?

---

### Post by rustytone on 2021-02-02
hey thanks :)

how do i remove it? the incorrect software package.

software i tested it on jriver media centre (i use this on windows so know the setup) vlc and kaffene - none of them worked. its lighting up the leds so it kind of works but not properly.

thanks for the quick reply.

---

### Post by CelticWarrior on 2021-02-02
```
sudo apt remove <package>
```
to remove.

Have you installed the firmware as instructed? Basically you should have had installed two packages only: "[COLOR=#333333][FONT=roboto]*linux-hwe-mediatree" and "*[/FONT][/COLOR][COLOR=#333333][FONT=roboto][I]linux-firmware-hauppauge".

[/I][/FONT][/COLOR]If you did so, then removed the wrong package, rebooted and it's still the same please elaborate about "[COLOR=#000000]its lighting up the leds so it kind of works but not properly" ????
[/COLOR]First was "didn't work" then "it kind of works"... Please understand we can't see what you're seeing so, please, once and for all, describe what you're attempting, what is supposed to happen and what happens instead.

---

### Post by rustytone on 2021-02-02
thanks ive uninstalled the linux-mediatree ive installed the other two, the hwe and firmware, will reboot and get back to you.

as for leds etc - all i mean is that it is powering it up however nothing else. no live tv, doesnt show up on any media player etc.

---

### Post by CelticWarrior on 2021-02-02
Also disable Secure Boot in UEFI ("BIOS")...

---

### Post by rustytone on 2021-02-02
got it working following your advice, wasnt supported in jriver media centre on linux,vlc i didnt know how to set it up so went with kaffeine, its scanning the channels now :)
secure boot is disabled i believe i never enabled it.

thanks for the help.

---

