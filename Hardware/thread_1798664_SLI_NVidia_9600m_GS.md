---
title: "SLI NVidia 9600m GS"
date: 2011-07-06
forum: Hardware
---

### Post by LifeOfRyan on 2011-07-06
HI guys wondered if i could have a little help here regarding settting up my HDMI dual screen. 
In my X server settings panel both of my displays are listed under GPU0 which is the less powerful 9100m G, but obviously i would prefer to use the more powerful 9600m GS which i think would usually run the HDMI output? any input here would be much appreciated.

running 10.04 lucid

thanks, ryan

---

### Post by CMOS4081 on 2011-07-06
First, are you running 2 video cards or just one?
SLI means you are running 2 video cards of the same type.
From the text in the post it seems you just have one card, am I correct?

You can run 2 monitors of any Nvidia graphics card as they come will multiple outputs. 

Whatever your setup is, you should remove the nouveau driver and isntall the nvidia driver. 

Using the nvidia-settings with sudo you can configure everything as it works very similar to the nvidia control panel in windowz.

---

### Post by LifeOfRyan on 2011-07-07
Sorry perhaps i didnt explain this so well, I have 2 video cards the laptop is an acer aspire 7530g running NVIDIA hybrid SLI graphics, the nvidia control panel is set up and running well in ubuntu apart from dual monitors. GPU-0 which is the 9100m G card, has detected the additional HDMI screen but GPU1 (9600M GS) has no displays assigned to it. so im thinking do i need to assign my hdmi monitor to GPU1 in order to use the dual screens? How do i go about doing this?

---

### Post by LifeOfRyan on 2011-07-12
No one knows nothing about this?

---

