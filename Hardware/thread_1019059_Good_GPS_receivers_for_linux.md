---
title: "Good GPS receivers for linux?"
date: 2008-12-22
forum: Hardware
---

### Post by beefjerkymonster on 2008-12-22
I'm looking to buy a USB GPS receiver, but I want to make sure it will work with Ubuntu before I buy.


Are there any I should avoid, any recommended? 


I just want to dodge as many problems as I can. :)

---

### Post by eaidoido on 2008-12-23
mom got a tomtom gps for christmas, ive hooked it up to my laptop with no luck thus far. trying to install their software through wine, i get a complaint of a msvcr80.dll library. continue.

---

### Post by eaidoido on 2008-12-23
mom got a tomtom gps for christmas, ive hooked it up to my laptop with no luck thus far. trying to install their software through wine, i get a complaint of a msvcr80.dll library. continue.

---

### Post by Rhubarb on 2008-12-23
If you have working bluetooth, you can use any bluetooth GPS receiver that you like.
Just bear in mind that you probably won't be able to use any windows GPS software without using wine / virtualbox (I'm not sure it it'd work in wine, as afaik wine can't access external hardware directly like that).

There is some very good GPS software available though, it really depends what you want / need.
It'll work with google earth, and with tangoGPS
[http://www.tangogps.org/gps/cat/About](http://www.tangogps.org/gps/cat/About)

There is a little fiddling around to get it all working, as you'd need to use gpsd (GPS deamon), and probably rfcomm to make the connection.
This information can be found online.

Give me a PM if you want me to help you with this, as I have lots of experience getting this to work in Ubuntu.

-Rhubarb

---

### Post by nixi on 2009-01-07
For GPS on EeePC there is a good website at [http://www.eeextra.com/eee/install-a-gps-on-a-netbook-part-1-the-hardware.html]("http://www.eeextra.com/eee/install-a-gps-on-a-netbook-part-1-the-hardware.html")

Holux 1200 is used in that example, but a Holux GR-240 has a SiRF star III chip. 

TangoGPS should work well with Ubuntu 8.04 or earlier. However, I'm trying it out with Ubuntu 8.10 on my EeePC 701, and got into some graphics trouble. 

Initially all seemed to work very well, but after a program freeze, manual crash, and restart, the map window is all white, and I can't see the maps anymore. Anyone here recognize this sort of error?

---

### Post by Rhubarb on 2009-01-11
> **nixi said:**
> ... Initially all seemed to work very well, but after a program freeze, manual crash, and restart, the map window is all white, and I can't see the maps anymore. Anyone here recognize this sort of error?

Hmmm, I'm not familiar with that error at all (as I don't have any problems with tangoGPS in Ubuntu 8.10).
All that I can think of, which is rather lame, is to remove tangoGPS, and re-install it again.

Best of luck - Rhubarb

---

### Post by nixi on 2009-01-11
Hi, it occurred to me that the problem might have something to do with the Ubuntu appearance theme I use, DarkRoom. So, after changing the theme to the standard one, Human, the maps became visible, but only for some time; for after some panning and zooming they began appearing white again. I changed to that DarkRoom theme again, and the maps appear visible again... ..for now.

---

### Post by nixi on 2009-01-16
The maps seem to appear as they should now :).

However, TangoGPS keeps saying > no GPS found How can I make it find the GPS device (USB)? I suspect there is something wrong with GSPD. 

I typed "gpsd -n /dev/ttyUSB0" in the Terminal (as it was done with Debian Sid in an article: [http://www.linux.com/feature/152468](http://www.linux.com/feature/152468)), and no error messages appeared. Yet tangoGPS insists: "no GPS found". Typing "sudo gpsd" merely generates: > gpsd: can't run with neither control socket nor devices How does GPSD work (on Ubuntu Intrepid)? 

Launching TangoGPS from the Terminal shows: 
> reconnecting to gspd FAILED
NOGPSno gpsdata for timer
So it seems there is something wrong with GPSD. :(

Typing "lsusb" identifies the device as > Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port 

I guess "2303" is its Port, but how can I find its "GPSD Host IP"?

"dmesg | tail" generates:
> [17757.366629] usb 2-2: configuration #1 chosen from 1 choice
[17757.370844] pl2303 2-2:1.0: pl2303 converter detected
[17757.382630] usb 2-2: pl2303 converter now attached to ttyUSB0
[20068.824100] usb 2-2: USB disconnect, address 3
[20068.831543] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[20068.836297] pl2303 2-2:1.0: device disconnected
[20072.592062] usb 2-2: new full speed USB device using uhci_hcd and address 4
[20072.794935] usb 2-2: configuration #1 chosen from 1 choice
[20072.798336] pl2303 2-2:1.0: pl2303 converter detected
[20072.820723] usb 2-2: pl2303 converter now attached to ttyUSB0 



EDIT

Ok now GPSD woke up: I typed in the Terminal: 
> gpsd /dev/ttyUSB0
(which the address shown with dmesg above) and then I started tangoGPS to see whether it can recieve a signal, and it does! :) 

There is more good stuff to read at --> [http://ubuntuforums.org/showthread.php?p=6560917#post6560917](http://ubuntuforums.org/showthread.php?p=6560917#post6560917)

---

### Post by Rhubarb on 2009-01-17
Thanks nixi :D
Good to know you've got it working again.

---

### Post by jaygeebuntu on 2009-03-26
> **Rhubarb said:**
> Hmmm, I'm not familiar with that error at all (as I don't have any problems with tangoGPS in Ubuntu 8.10).
All that I can think of, which is rather lame, is to remove tangoGPS, and re-install it again.

Best of luck - Rhubarb

Hi Rhubarb

I'm hoping you can help with a tangogps problem I've got.
 
Briefly: I added a new map repo to tangogps in Ubuntu 8.10 which didn't work but I can't find a way to remove it (only new and edit functions available in the GUI) so I decided to completely remove the program and then install a fresh download.

Trouble is following a Synaptic complete removal and a new debi installation I get a message saying the same version is already installed and the unwanted map repo reappears. Is there a way of getting a truly complete removal?

---

### Post by cjreeve on 2009-09-26
Hi, I expect you have bought a GPS dongle now but I thought I'd just add this info for anyone else. I recently bought a CVGI-B07 GPS dongle and it works well with my version of ubuntu (eeebuntu 3.0). I had some problems with gpsd in that it wrote to the device and crashed and I had to reset the Star III chip  with the SiRFDemo software. It works well with gpsd with the -b option. [You can read more about how I got it working on my eee-pc]("http://theadventuresofsuperdoc.blogspot.com/2009/09/gps-with-cvgi-b07-on-eeebuntu.html") [here]("http://theadventuresofsuperdoc.blogspot.com/2009/09/gps-with-cvgi-b07-on-eeebuntu.html"). I was able to run SiRFDemo on my linux pc too. I just had to create a soft link for the COM port: sudo ln -s /dev/ttyUSB0  ~/.wine/dosdevices/com1

---

### Post by savantelite on 2009-10-09
my holux m-1200 bluetooth gps dongle is immidatly reconised by the blue tooth mananger and goes on to ask me  if I would like to use it for gps location where I say yes. But I still cannot connect tangogps or gpsdrive to my coordinates?

I think it has something to do with GPSD and my correct ip. but It may be just buggy software too?

---

### Post by gerkin on 2009-10-24
I'm using a Holux M-241 over bluetooth on my Eeepc 900 

After configuring the bluetooth dongle it works like a charm with 
TangoGPS & Viking using GPSD (which I run with a bash script)

See my post(s) here for more info:
[http://ubuntuforums.org/showthread.php?t=875478&highlight=holux](http://ubuntuforums.org/showthread.php?t=875478&highlight=holux)

Gerkin

---

