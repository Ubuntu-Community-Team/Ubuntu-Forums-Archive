---
title: "Hercules Webcam Classic in Ekiga &amp; Skype"
date: 2009-12-28
forum: Hardware
---

### Post by patrick11ty on 2009-12-28
I have karmic 9.10 and got the Hercules Webcam Classic working and this is how I did it and I am thinking it may be of use to others.


first I followed the instructions from here:
[http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/)

I skipped the dvb parts.. in hindsight really there was nothing extra required to mark, just to run it without going through all the menus to check.

after loading everything, the webcam worked in ekiga but not skype.

I got it working in skype by following the advice here>
[http://forum.skype.com/index.php?showtopic=144791](http://forum.skype.com/index.php?showtopic=144791)

mainly from "ThomasU">
	> How to launch Skype + V4L2 directly from Gnome/Ubuntu 	Jaunty menus so that the webcam works:
	Menu System --> Preferences --> Main Menu
	In the window select Internet, then Skype
	Click on [Properties] button
	In Command enter:
	bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'


after this even skype was working.

---

