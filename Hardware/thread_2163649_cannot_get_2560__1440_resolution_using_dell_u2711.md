---
title: "cannot get 2560 * 1440 resolution using dell u2711"
date: 2013-07-19
forum: Hardware
---

### Post by pearlygate on 2013-07-19
Hi,

I just got a dell u2711 which can handle a max of 2560 * 1440 resolution. My graphic card is Geforce 7600GT which supports dual DVI and up to 2560 * 1600 pixels. When I plugged my monitor, the max resolution I can have is 1680 * something pixel.

Anyway I've done some google search and people said basically I need:
1.) Supporting graphic card (check)
2.) Use dual link DVI cable (check)
3.) install the current driver, I did this using the driver update (check)

I'm using ubuntu 12.04 LTS and I updated all my software.

Is there anything else I should do to get the max resolution to be 2560 * 1440. Do I need to edit xorg.conf and add 2560 * 1440 resolution manually?
Would that make the performance go slower? or is it supported natively?

---

### Post by dino99 on 2013-07-19
which driver is installed and activated ?  nvidia-173 might be the one you need.
then you can check the hardware limit : [http://www.arachnoid.com/modelines/](http://www.arachnoid.com/modelines/)
and also playing with xrandr : [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by jp734 on 2013-07-19
Most of the time, for something like this you need to tell the system specifically your monitors horizontal and vertical refresh rates. Add them to your xorg.conf "section monitor"

 HorizSync. ##.#-##.#
VertRefresh ##.#-##.#

---

### Post by pearlygate on 2013-07-19
Cool, I think my driver is 173 (it's the recommended current version according to the driver software). 
I'll double check when I got home. 

Btw for the modeline, do I just need to copy this:
> 
# 2560x1440 @ 60.00 Hz (GTF) hsync: 89.40 kHz; pclk: 311.83 MHz
Modeline "2560x1440_60.00" 311.83 2560 2744 3024 3488 1440 1441 1444 1490 -HSync +Vsync

into xorg.conf in the monitor section

---

