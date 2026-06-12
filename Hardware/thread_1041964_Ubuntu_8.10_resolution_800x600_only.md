---
title: "Ubuntu 8.10 resolution 800x600 only"
date: 2009-01-17
forum: Hardware
---

### Post by andrewchua on 2009-01-17
Hi, I recently removed my windows xp and clean installed ubuntu 8.10 on my desktop. but after installation, the maximum resolution is only 800x600 only. I have a samsung syncmaster monitor and nvidia geforce 4 mx 440 graphics card. I followed online recommendation and installed the restricted drivers which was the nvidia accelerated graphics 96 package. 
after installation of the driver, the problem was even worst, maximum resolution was only 640x480.

After that I removed the driver and I got back the maximum resolution of 800x600. I figured maybe it was a monitor driver problem but I can't find samsung monitor drivers for linux system.

I was wondering if you guys had any ideas in solving this problem. This 800x600 resolution is kinda irritating. I can view webpages properly. Any help is appreciated. Thanks

---

### Post by mikewhatever on 2009-01-17
Can you post the output of the following command from Applications->Accessories->Terminal.
sudo xrandr -q

What resolution should you be using?

---

### Post by andrewchua on 2009-01-17
hi mikewhatever, thanks for helping me.
here are the results as requested by you.

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  

i can't recall what were the resolution settings when this same CPU was installed with windows xp but it was definitely way more than 800x600. If my memory serves me correctly, I think it was 1280x something.

---

### Post by andrewchua on 2009-01-17
I tried reinstalling the nvidia accelerated graphics driver 96 and ran sudo xrandr -q again and here are the results

Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0

---

### Post by enderbalci on 2009-01-17
Hi, I have exactly the same problem. I appreciate receiving your help.

---

### Post by andrewchua on 2009-01-18
Hi, problem solved. check out this link and follow the instructions from the first post
[http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

remember to check for the vsync and hsync of your monitor and the resolutions supported by your monitor

---

### Post by enderbalci on 2009-01-23
I found out my problem as Ubuntu 8.10 do not have the driver for my old flat screen Compaq TFT5010i. I change the xorg.conf file as below;

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)"
Driver "intel"	Option		"UseFBDev"		"true"
EndSection


Section "Monitor"

        Identifier	"Generic Monitor"

        HorizSync	28-60

        VertRefresh	43-110

        Option		"DPMS"

EndSection


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)"
SubSection "Display"
Modes  "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection


Now my problem is solved because I need 1024X768 resolution.

Thank you for your time!

---

### Post by litlfrog on 2009-02-25
> **andrewchua said:**
> Hi, problem solved. check out this link and follow the instructions from the first post
[http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

remember to check for the vsync and hsync of your monitor and the resolutions supported by your monitor

Just wanted to say that I had the same problem and the instructions in the linked thread worked great.

---

### Post by Lake50 on 2009-03-03
The above solution worked for me too. The problem is the monitor not the card driver.

---

### Post by StefanoRMC on 2009-03-03
I have the same problem on an old Acer with an intel i810 integrated chip; can I use the same solution?
thanks
ciao
stefano

---

