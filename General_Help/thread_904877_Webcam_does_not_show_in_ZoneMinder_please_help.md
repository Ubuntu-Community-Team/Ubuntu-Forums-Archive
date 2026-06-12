---
title: "Webcam does not show in ZoneMinder?? please help"
date: 2008-08-29
forum: General Help
---

### Post by pjpeter on 2008-08-29
My webcam works in cheese but does not work in ZoneMiner :( 
- as you can see in the attached screenshot.


The error I receive in the log is as follows:

08/30/08 00:25:31.328090 zmwatch[5637].INF [Restarting capture daemon for New, shared memory not valid]
08/30/08 00:25:31.614872 zmwatch[5637].INF ['zmc -d /dev/video0' stopping at 08/08/30 00:25:31]

I've tried increasing the memory allocated but still no luck... :( 

I would really appreciate any help!!:confused:

---

### Post by Crafty Kisses on 2008-08-29
Post results of > lsusb

---

### Post by pjpeter on 2008-08-29
> **Codename said:**
> Post results of > lsusb

I hope this is what you meant:

peter@peter-desktop:~$ lsusb
Bus 003 Device 009: ID 043d:0069 Lexmark International, Inc. X74/X75 Printer
Bus 003 Device 008: ID 043d:0060 Lexmark International, Inc. X74/X75 Scanner
Bus 003 Device 007: ID 043d:0061 Lexmark International, Inc. X74 Hub
Bus 003 Device 006: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 003 Device 005: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 003 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0db0:6982 Micro Star International Medion Flash XL V2.7A Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 041e:4028 Creative Technology, Ltd Vista Plus cam [VF0090]
Bus 001 Device 001: ID 0000:0000

---

### Post by ondemanddesign on 2011-03-29
I have this exact same problem.

---

### Post by oregonbob on 2011-04-22
Did anyone ever get this working?

I installed zoneminder and cannot get it to work with either of my two USB webcams. I have tried Logitech Quickcam Express S5500 and Logitech Pro 9000, neither work.

The cams show up as [COLOR="Red"]red-colored[/COLOR] devices in zoneminder where working cam devices show [COLOR="DarkGreen"]green[/COLOR]. I have changed perms on /dev/video0 to crwxrwxrwx. Programs Cheese and Camorama see the video just fine.

Zoneminder works great on my Linksys netcams, but not USB webcams. Zoneminder is cool as it can be set to capture and record motion, databasing it in mysql.

---

### Post by DukeBoxer on 2011-04-22
You might want to try this thread...

[http://www.zoneminder.com/forums/viewtopic.php?p=63801](http://www.zoneminder.com/forums/viewtopic.php?p=63801)

This loads the camera in ZoneMinder as V4L1 compatible. This is what I had to do to get a Logitech Quickcam working. Just follow the instructions there!

---

### Post by oregonbob on 2011-04-22
Thanks DukeBoxer, that worked! I can now use either of my two Logitech webcams.

Settings I used for webcam attached.

---

### Post by DukeBoxer on 2011-04-22
Nice! It took me about 4 days to get everything working correctly after I realized I could install it from Synaptic. I was trying to build it for a day before that! It works good though. My wife and I have a café and suspected a property manager of going in after hours and we caught him 3 times on camera and once when I didn't get it recording yet (actually the first day I got everything running) One more thing to check out which was a problem for me was the Buffers, located in the "Source" pop up menu. I changed the post event image count to 600 so even after someone leaves the motion detection area the camera still captures and if he re-enters the area it will trigger it to keep capturing as the same event instead of stopping and starting a new event

---

### Post by alek66 on 2012-09-02
> **DukeBoxer said:**
> Nice! It took me about 4 days to get everything working correctly after I realized I could install it from Synaptic. I was trying to build it for a day before that! It works good though. My wife and I have a café and suspected a property manager of going in after hours and we caught him 3 times on camera and once when I didn't get it recording yet (actually the first day I got everything running) One more thing to check out which was a problem for me was the Buffers, located in the "Source" pop up menu. I changed the post event image count to 600 so even after someone leaves the motion detection area the camera still captures and if he re-enters the area it will trigger it to keep capturing as the same event instead of stopping and starting a new event



Does the installation of the Logitech quickcam drivers work from synaptic ? or it only downloads the packages?

I want to know if after downloading with synaptic its all done...thanks

---

### Post by oldos2er on 2012-09-03
Please start a new thread for your question, this one's four years old.

---

