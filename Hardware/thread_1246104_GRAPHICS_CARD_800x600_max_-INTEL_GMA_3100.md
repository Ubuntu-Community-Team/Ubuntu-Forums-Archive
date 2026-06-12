---
title: "GRAPHICS CARD 800x600 max -INTEL GMA 3100"
date: 2009-08-21
forum: Hardware
---

### Post by LineAxe on 2009-08-21
Been digging on the internet for a "fast" ? way to get my Onboard Graphics card going . Its an Intel GMA 3100. I have heard that it will work ok ,but so far everywhere I have looked , I can't seem to find the right information to put in the xorg.conf file .. And it seems there are a few xorg.conf files that could be modified , one in etc/X11 has been pointed out to me as the one that needs to have the driver info modified. Can anyone help me find the right info? 
                [CENTER] Stuck as always[/CENTER], 
[CENTER]LineAxe
:-({|=[/CENTER]

---

### Post by mdmarmer on 2009-08-21
Are you using the intel driver?
Is this a desktop or laptop?
What's the resolution of your monitor?
If it's a laptop, what make and model?

Mike

---

### Post by LineAxe on 2009-08-21
My computer is a desktop with an Asus motherboard in it .
I have looked at the xorg.conf file and found it was running [COLOR="Red"]vesa[/COLOR], so I tried a tutorial that switched it to    [COLOR="Red"]intel[/COLOR] with a few other lines of code that set up various screen resolutions. When I tried this the video crashed ( and that is when I found out how to reboot to a terminal screen in ubuntu ) so I reset it , read up some more on my drivers. Still couldn't find anything that would give me the correct settings for it . I know it is supported , I have seen the various intel files are already in their directories.
My monitor is actually a SONY TV/Monitor  its a SONY BRAVIA KDL 32S5100
  the info I got so far says the max resolution is 1920 x 1080 .

 It should be able to support 1024x768 and 1280x1024 I would imagine.
I will look to see if I can find a linux Monitor spec for it now , I was just going to try stuff like STANDARD Monitor (generic) and see if it would support the resolution the card puts out. I think my problem is in the card not going into the other resolution modes.  So I am still digging away on the net .  I will post any ubuntu Monitor settings if I can locate them.:P

---

### Post by LineAxe on 2009-08-29
Help !
oh help /!

Heeeelll - cough cough -ppppppp!!!!!:KS

---

### Post by Yellow Pasque on 2009-08-29
Try to use the intel video driver and then copy the /var/log/Xorg.0.log file to your home directory. Now you can boot into X with vesa and post the contents of that file here (between [ CODE ][ /CODE ] blocks, of course).

---

