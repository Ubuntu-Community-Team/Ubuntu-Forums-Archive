---
title: "x server wont start on acer aspire 1510"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by Razvan on 2004-11-06
Hello,

i have an Acer Aspire 1510 /w AMD64 on NForce3 with Nvidia 420 go gfxcard.

i installed ubuntu 64 bit quite good with german keyboard layout

when it tried to start gdm first time, it crashed and displayed something with iso 98....... thats why i believe its something with the keymap...i changed the keyboardlayout in my XF86config-4 from "de" to "en" 

now it only switches from blank black to the console view and after a few times says xserver is misconfigured and asks if i want to see output

any ideas?

PS: thats another issue...the output of the xserver in thet window when it crashes cant be scrolled or something...so its not very userfull :-) is there any other place to find the logfile?

soory for my english and thanks in advance , Martin

---

### Post by humberto on 2004-11-07
[QUOTE=Razvan]
i have an Acer Aspire 1510 /w AMD64 on NForce3 with Nvidia 420 go gfxcard.

PS: thats another issue...the output of the xserver in thet window when it crashes cant be scrolled or something...so its not very userfull :-) is there any other place to find the logfile?

[/QUOTE]

The logfile should be in /var/log/XFree86.0.log

I've had problems with NVidia cards in laptops. You may be able to get X to work at a very low resolution only. After you install the proprietary NVidia drivers then you can raise the resolution.

---

### Post by Razvan on 2004-11-07
thanks for the reply!

i have tried to set the resolution down and installed the nvidia-drivers via apt-get

...didnt help  :-( 

and I believe, its because the ones in the apt-repositories are for 32 bit...

anyway...i downloaded the original .run file from nvidia and it even compiled nicely  :-D 

but when its done with compiling the kernel module it wants to copy some files and claims not to be able to write files to /usr/lib and /usr/lib64 and /usr/X11R6/lib/modules/extenions because they allready existed...i deleted them and retried but with no effect

any ideas, how to get the installer to write files anyway?

thank, Martin

---

### Post by anklator on 2004-11-07
you can provisionally use the VESA driver, its what i do, cuz i dont feel like using unichrome drivers dfor my VIA card

---

