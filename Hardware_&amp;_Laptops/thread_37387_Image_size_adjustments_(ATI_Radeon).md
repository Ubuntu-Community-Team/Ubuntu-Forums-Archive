---
title: "Image size adjustments (ATI Radeon)"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by Zunino on 2005-05-27
Hello.

Newbie here, so please, bear with me.

I have a Radeon 9500 PRO on my system which, upon a fresh installation of Hoary, was properly detected and set to work at 1600x1200@85Hz. Pretty good, but I would really like to use the same resolution as I do in Windows, namely, 1792x1344@75Hz. I then found a "howto" which explained how one should install the binary driver for ATI. I followed it and noticed an improvement: 3D acceleration entered the scene. But as for the resolution issue, I found out that I'd have to run fglrxconfig in order to include my desired 1792x1344 mode. I did so and was happy to see it come alive and at the 75Hz also desired.

All nice and cool... Well, almost. Here is where something weird began to happen. What I have is an image which does not completely fill the available monitor's width. That would probably just be a normal consequence of choosing a certain resolution + refresh rate combination. However, I don't see the same problem in Windows, using the same settings. Pressing the "menu" button of my monitor, allows me to see the active Vertical and Horizontal rates. I checked the values while running Windows and then Linux and found out they are the same. How come? Same resolution with same refresh rate values should end up in the same monitor configuration.

Given that, I can only think the difference lies in the fact that, in Windows, the driver allows the user to make image adjustments, e.g. change width or height, etc.. Searching for information on something similar in Linux, I found a mention of a small utility which would supposedly let you alter the dimensions of the image (don't remember its name). I tried it, but it did not work. Does anyone know a solution to this problem? It is really disturbing to have my desktop the way it is now and if I find no satisfying solution, I will have to revert to 1600x1200. But I'd really like to be able to use my desired settings.

Thank you,

-- 
Ney André de Mello Zunino

---

### Post by kb00heda on 2005-05-27
Correct me if I'm wrong here, but you have your desired resolution, i.e., 1792x1344, the problem is that the picture doesn't fill the whole monitor. You have a black frame surrouding your desktop.

Is it not possible to adjust the size of the picture on your monitor panel directly? I know I can on my Samsung monitor at home. There usually are some buttons for changing things like color and such. One of them ought to bring down a "control panel" for the monitor.

If this is the case there is no need to change any configuration in Ubuntu.

---

### Post by Zunino on 2005-05-27
[QUOTE=kb00heda]Correct me if I'm wrong here, but you have your desired resolution, i.e., 1792x1344, the problem is that the picture doesn't fill the whole monitor. You have a black frame surrouding your desktop.[/QUOTE]That's right.

[quote="kb00heda]
Is it not possible to adjust the size of the picture on your monitor panel directly? I know I can on my Samsung monitor at home. There usually are some buttons for changing things like color and such. One of them ought to bring down a "control panel" for the monitor.

If this is the case there is no need to change any configuration in Ubuntu.[/QUOTE]Yes, I am aware of the hardware controls for adjusting the image in a certain configuration. However, there is only so much you can do with them. IOW, under certain resolution/refresh rate combinations (such as the one I am targetting), the monitor controls will only allow you to stretch the image to a certain extent. From that point on, you have to rely on the driver-provided adjustment controls to complete the tuning. That's how I can get the image to fill the whole monitor on Windows.

In case there is no solution for this on Linux, I will have to do one of two things: revert to 1600x1200 or use only the hardware controls to adjust the image under my desired resolution/refresh rate. Unfortunately, this last option will leave me with a black frame on both platforms.  :-? 

Regards,

-- 
Ney André de Mello Zunino

---

