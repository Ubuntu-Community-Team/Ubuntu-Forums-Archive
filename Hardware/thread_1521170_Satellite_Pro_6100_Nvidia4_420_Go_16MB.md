---
title: "Satellite Pro 6100 Nvidia4 420 Go 16MB"
date: 2010-06-30
forum: Hardware
---

### Post by cheapytech on 2010-06-30
OK here is the deal, I have a 9 year old Toshiba Satellite Pro with 1.6 GH P4. I am running Ubuntu 10.04. The Toshiba has a built in Nvidia4 420 Go video card. After selecting Hardware drivers Ubuntu chose a Nvidia driver and installed it. After a lot of searching on the Internet and trial and error I came up with the below Xorg.conf that worked. My screen display starts the way I want it to and I can access the Nvidia display config screen.

Now here is the problem. 3D games will run but just barely, It's like 1 frame per second. I have to wait to be able to get the exit button to get out of games. The funny thing is I can go to a web site like Miniclip.com and play games with no problem at all.

So what do I have to do to fix this. I don't understand why this has to be such a pain to make work. :confused:

Xorg.conf is below:

Section "Screen"
        Option "UseDisplayDevice" "DFP"
        identifier "Screen0"
        Device "Device0"
        Monitor "Monitor0"
        DefaultDepth 24
        Option "AddARGBGLXVisuals" "True" 
   SubSection "Display"
           Depth 24
           Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
   EndSubSection
EndSection

---

### Post by cheapytech on 2010-07-03
I'm just wondering why nobody has made any comments at all on this. It would be great to have games working correctly on this laptop.

---

### Post by khelben1979 on 2010-07-03
First off I want to tell you that playing heavy 3D games with a graphic chipset which only has 16MB of graphics memory is not very powerful if you decide to go for newer games which probably is part of Ubuntu Lucid. Have you tried older games, and... I do mean very old 3D games like Quake 2 or similiar?

Also, the reason to why the speed on the games is faster on the web is probably because they are based on java or flash. Those technologies uses the CPU much more than the graphics chipset, also, the graphics is usually not as advanced and heavy as in big 3D game titles.

There is a possibility that your system is lacking a proper OpenGL installation or that this specific graphics driver is not optimal for your system, for instance, free nVidia drivers are usually slower than the prop. ones which can be downloaded from nVidia.com, that is if they still support your old graphics chipset together with the new version of your present X server. Not all versions of the X server supports needed graphics drivers which have caused some people to use an older version of Ubuntu, just to get faster 3D graphics performance.

So a short answer: even though that OpenGL should be part of the nVidia driver package, you can just take a look in Synaptic Package Manager to see what OpenGL packages you have installed in there, it might be interesting to have a look even though it does not neccesarily solve the problem.

You need a faster GPU and more graphics memory for graphics intense gaming than what you currently have for your Ubuntu system.

---

### Post by cheapytech on 2010-07-03
Thanks for the reply!

I'm not trying to run something like quake. I'm talking about simple 3D game like chess with 3D. Here is the driver I have installed nvidia-96 96.43.17-oubuntu1 

I am able to run a game like Microsoft Freelancer in Windows XP with this video card so there is something not right with my installation.

---

### Post by khelben1979 on 2010-07-05
How did you install that driver?

---

### Post by cheapytech on 2010-07-05
I installed it by selecting System, Administration, Hardware drivers. Ubuntu 10.04 search for drivers found this one and then I allowed it to be installed. Then I had to edit my Xorg.conf to get everything to work.

---

### Post by khelben1979 on 2010-07-08
> **cheapytech said:**
> I installed it by selecting System, Administration, Hardware drivers. Ubuntu 10.04 search for drivers found this one and then I allowed it to be installed. Then I had to edit my Xorg.conf to get everything to work.

Looks good.

The only other alternative as I see it, is that you try different versions of nVidia drivers and experimenting, but I don't think it's worth the hassle if anything goes wrong.

---

