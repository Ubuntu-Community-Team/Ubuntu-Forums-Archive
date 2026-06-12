---
title: "Xserver failed to load...."
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by Kieffer87 on 2006-01-15
This is the third time Ive tryed to install on my desktop. My laptop went fine. Anyhow I did a clean install ereased everthing, installation went fine but when it tryes to load xserver, I get a message saying it may not be configured correctly, etc. I tryed configureing it but I still get the same problem. Im looking at the log right now and there are a few warnings.

1.The direcory /usr/share/x11/fonts/cyrillic does not exist entry deleted from font path
2. The directory /usr/share/x11/fonts/CID does not exist entry deleted from font path.
3. fonts.dir not found (or not valid) in /var/lib/defoma/x-ttcidfont-conf .d/dirs/CID Entry deleted from font path
4. Open APM failed (/dev/apm_bios) (No such Device)
5. Ignorin request to load module GLcore
6. skipping /usr/x11r/lib/modules/extensions/libGLcore.a:m_debug_clip.o: No symbols found (there are 3 of these with different debug files.)

And thats it. I sure hope you guys can help!! This is a dell 4700 3.0 w/HT 1GB ram

---

### Post by Kieffer87 on 2006-01-15
Anyone?

---

### Post by christhemonkey on 2006-01-15
what graphics card have you got?

---

### Post by Kieffer87 on 2006-01-15
ATI x800 PCIE

---

### Post by christhemonkey on 2006-01-15
is ther any reference to it in the error log?

---

### Post by Kieffer87 on 2006-01-15
When I try to access the actual log I get a permission denied. Even when logged in under root via sudi -i.

---

### Post by Kieffer87 on 2006-01-15
When I type in startx from the console I see (EE) no Devices Detected. and how it skips the 3 debug files as stated above.

---

### Post by Kieffer87 on 2006-01-15
also XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

---

### Post by christhemonkey on 2006-01-15
you shudnt log in with root.
You can do silly things like deleting important stuff by accident:)
sudo vi /name/and/placeof/logfile

---

### Post by Kieffer87 on 2006-01-15
Other than what I said about the fonts in my first post. The only other things I see are ATI: PCI Mach64 in slot 1:0:0 could not be detected. Im guessing thats my problem. Now just hot to fix it :)

---

### Post by Kieffer87 on 2006-01-15
I put my old x300 car in and it works fine. So it must have just been somthing with the x800 card it didnt like.

---

### Post by christhemonkey on 2006-01-15
mayhaps this card is not supported yet?

---

### Post by christhemonkey on 2006-01-16
Thanks to fireonyx for this:
[QUOTE=fireonyx]The ATI driver has been recently updated, and you have to install the driver, which you can find out here somewhere.  In the meantime, edit the /etc/X11/xorg.conf and under the graphics card, put the option "noaccel".  Here is the code : 
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "NoAccel"
EndSection[/QUOTE]

---

### Post by Kieffer87 on 2006-01-22
Got it all working with some new drivers. Thanks for the help guys!

---

### Post by rock freak on 2006-01-23
hmmm i have got the X850XT and i am having the smae problem as you only i havnt got a card i can try it on. 

how did you sort it!!!

---

### Post by Kieffer87 on 2006-01-23
[https://wiki.ubuntu.com/BinaryDriverHowto]("https://wiki.ubuntu.com/BinaryDriverHowto")

I followed this how-to when I had my x300 card installed, shut down, installed x800 and walla. You should be able to do everything without having to start xserver.

---

### Post by rock freak on 2006-01-23
> sudo apt-get install xorg-driver-fglrx

on that page

when i run it it says 

> Reading package lissts... Done
Building dependency tree... Done
E: couldn't find package xorg-driver-fglrx


any ideas people i am running 64bit with the 32bit brezzy installed it doe sit with the 64bit on breezy and dapper and on both 32bit installs as well

---

### Post by Kieffer87 on 2006-01-23
Did you make sure to run the install for 64bit? That would be my guess?

---

### Post by rock freak on 2006-01-23
its ok i firgured out what was wrong the sources.list only had one in so put all of the right ones back in and worked a charm im on ubuntu atm my crossover from windows is almost complete!

---

### Post by Kieffer87 on 2006-01-24
I hear ya on the corssover, I finally got AA working right and all hardware working great so im offically a linux man. No more xp for me, I love having 850MB of ram and 98% processor to work with vs windows only id have around 400MB of ram to work with and around 80% processor!

---

### Post by guytrinn on 2006-01-25
hey rock freak, i am having the same problem as you. Could you please just tell me what you did because i am lost as of right now.

---

### Post by guytrinn on 2006-01-27
[QUOTE=rock freak]on that page
 
sudo apt-get install xorg-driver-fglrx


when i run it it says

Quote:
Reading package lissts... Done
Building dependency tree... Done
E: couldn't find package xorg-driver-fglrx

any ideas people i am running 64bit with the 32bit brezzy installed it doe sit with the 64bit on breezy and dapper and on both 32bit installs as well[/QUOTE]


i am having this same problem. some help would be highly appreciated...

---

