---
title: "Lenovo Webcam Activation ??"
date: 2011-11-22
forum: Hardware
---

### Post by dik909 on 2011-11-22
I just got a smoove new Lenovo laptop and have 11.10 on it.  It has a built-in webcam, but I can't figure out how to get it working.  I installed 'Cheese' and even the 'Preferences' isn't allowing me to configure.

Any advice/suggestions on how to locate/active the webcam ??

Thanx !

---

### Post by bluexrider on 2011-11-22
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Go to section 3.1 for configuration 

Good Luck

---

### Post by dik909 on 2011-11-24
that didn't help :/

it's a built-in webcam.  lemme see about getting a pic of what appears:

---

### Post by dik909 on 2011-11-24
just took a screenshot, but don't have anywhere to host the image.  it says:

---------------------------

'Adobe Flash Player Settings'
Camera and Microphone access
chatrandom.com is requesting access
to your camera and microphone.  If you
click Allow, you may be recorded.
   ALLOW    DENY

---------------------------

here's the bxtch of it: whether i click Allow or Deny,  nothing happens.  it's as though i'm not being let to click either of them at all.  i click and click and nothing happens - just have to close the window.

i right-click on it to go to 'Settings', but the same:  nothing.

this is frustrating.  built-in webcam works for Cheese, but that's it... :/

---

### Post by bluexrider on 2011-11-25
so its the Flash part that doesn't work.
It works with Cheese?

---

### Post by gordintoronto on 2011-11-25
If you open a terminal and run this command:
lsusb

one of the lines with give information about the webcam. Eg:
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

The best information is the ID, in my case, 0ac8:303b

You can plug that into Google along with some other words, such as USB and solved.

---

### Post by dik909 on 2011-11-27
ya, i believe it must be in the Flash settings.  how do i effect them ?  on chatroulette or any such site the 'Adobe Flash Settings' dialogue box opens, like i said, but clicking on it does nothing whatsoever... :/

it's not a USB webcam, it's the built-in webcam that sits rite above the screen.

thanks for taking the time to help me figure this one out, btw. :)

---

### Post by gordintoronto on 2011-11-28
Every built-in webcam I have seen, was connected as a USB peripheral. Try lsusb

---

### Post by dik909 on 2011-11-29
okay, did 'lsusb' and this what came up:


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 004: ID 064e:a222 Suyin Corp. 



so now how to i get it to work ?? :/

---

### Post by dik909 on 2011-11-29
> **dik909 said:**
> okay, did 'lsusb' and this what came up:


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 004: ID 064e:a222 Suyin Corp. 



so now how to i get it to work ?? :/


Bus 2, Device 4 is the Syuin webcam.  i did a google search for '064e:a222 USB' like you suggested, but am not sure what i'm supposed to be looking for or doing to get it to work ??

---

### Post by gordintoronto on 2011-11-29
Well darn! Usually this google search turns up something useful. If the web cam is quite new, maybe it's just a matter of time. I would keep an eye on the gspca web site, [http://mxhaard.free.fr/](http://mxhaard.free.fr/)

It doesn't have any content for 064e at the moment, but I expect that to change.

---

