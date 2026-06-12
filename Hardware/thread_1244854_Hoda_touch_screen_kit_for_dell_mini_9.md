---
title: "Hoda touch screen kit for dell mini 9"
date: 2009-08-19
forum: Hardware
---

### Post by saintslaughter on 2009-08-19
Ok so I have purchased a Hoda Touch Screen for my dell mini 9, and have also posted on mydellmini.com forums but no replys yet.   I have the touch screen installed via a script that came on the provided cd. The touch screen works kind of. Its connected via USB, and only "Touch clicks" where the mouse cursor is. I think this has to do with calabration. The app for calabration is called "TouchKit" and has been added to /usr/local, as well as /usr/bin through a link, so when I type Sudo TouchKit, it should execute. (From my understanding) this has all ben done by the script provided. When I do a sudo TouchKit, the app says No Touch Controller found. Do I have a bad touch board? Has anyone else atempted this, or something similar? Im a bit stumped, any light would be appreciated.

---

### Post by FelixH87 on 2009-10-09
Hey over there!
I hope you have already managed your problem. (I've had a similar problem with my Samsung NC10 and a hoda touchscreen bought from [www.fidohub.com](www.fidohub.com)). But in case you haven't this is what has fixed it on my NC10:
1.) The driver that comes with the touchscreen is an old one. They only work with ubuntu 8.04 and lower. (version in my case: TouchKit-2.05.2306-32b-k26)
2.) Your touchscreen is (i'm quiet sure) currently running with the linux-own basic driver 
--> xserver-xorg-input-evtouch
This driver is interfering with the TouchKit-Driver. 

So you should try: 
search under "system" - "system management" (Or something like this.. my system is running under german language) for "touchscreen-calibration". 
Do the calibration an check wether this could fix the problem.
IF NOT:
Deaktivate (~unistall) the evtouch in the package manager.
Go to:
[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
and get the latest driver for your touchscreen. You can use the BETA without any concerns.
The file comes with a readme and a setup.sh. Run it... it's the same like the TouchKit-installation. (ends with a reboot)
[i can't tell you wether YOU have to choose RS323,PS/2 or USB. In my case the Touchscreen was connected at the port of the onboard-webcam.. an that is an intern usb-port. easy to define...if it has 4 wire, black,green,white,red it might be a usb-port ;) ]
the first indicator that the install was successfull is that your touchscreen is reacting after the reboot ;) ) seriously .. that means he is working without the linux-own driver ...and that means WITH the eGalax-one's.
The x-y-achses might be mixed or any other kind of weird thing.
Start the egalax-calibration via eGalaxTouch over your terminal.
Do the calibrations under "tool".
Apply the changes.
After this the touchscreen should be calibrated and work fine.
I hope this will help you. 

Greetings from Germany.
Felix

---

### Post by saintslaughter on 2009-10-15
Wow This worked, Thank You So much. I was very close to giving up, and dual booting with XP, just to see if the touch screen worked. 

thx,
Saint

---

