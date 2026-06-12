---
title: "internal wifi"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by GolfGeek on 2006-03-19
I have seen and read a lot of solutions with addon wifi but what about the builtin laptops. I have a compaq presario 2108cl. The drivers at HP require you to download their softpaq.exe and run it. Where can I find drivers for this scenario. Thanks

---

### Post by Zelut on 2006-03-19
Post the output here of the following and we'll see if we can find you the appropriate drivers:

(try these until one gives results.  Not all will return information)
lspci | grep 802.11
lspci | grep Wireless
lspci | grep Wifi

lspci -n

---

### Post by GolfGeek on 2006-03-20
Thanks for the reply. I went back to the wireless and these are the results:

lspci|grep 802.11 was the only one to give results which were:
0000:00:09.0 network controller Broadcom Corp BCM4306 802.11b/g lan controller (rev2)

---

### Post by Zelut on 2006-03-20
..and the output from 'lspci -n' please.  (So far it looks like the identical model that I have, so I dont see any reasons we can't get it working.)

---

### Post by GolfGeek on 2006-03-20
This is the listing for the -n query:
0000:00:00.0 0600: 1002:cab0 (rev 13)
0000:00:01.0 0604: 1002:700f (rev 01)
0000:00:02.0 0c03: 10b9:5237 (rev 03)
0000:00:06.0 0401: 10b9:5451 (rev 02)
0000:00:07.0 0601: 10b9:1533
0000:00:08.0 0703: 10b9:5457
0000:00:09.0 0280: 14e4:4320 (rev 02)
0000:00:0a.0 0607: 104c:ac50 (rev 02)
0000:00:0c.0 0c00: 104c:8026
0000:00:10.0 0101: 10b9:5229 (rev c4)
0000:00:11.0 0680: 10b9:7101
0000:00:12.0 0200: 100b:0020
0000:01:05.0 0300: 1002:4336
carl@calibsys:~$

---

### Post by Zelut on 2006-03-20
Looks like we have an identical card.  Lets try these steps & see what we can get going.

> sudo apt-get install ndiswrapper-utils
wget [http://christer.homeip.net/bcmwl5.inf](http://christer.homeip.net/bcmwl5.inf)
wget [http://christer.homeip.net/bcmwl5.sys](http://christer.homeip.net/bcmwl5.sys)
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l (thats L)

That should report 'driver present, hardware present'.

If so follow with:
> sudo modprobe ndiswrapper
sudo ndiswrapper -m

(might need to reboot at this point)
Configure your wireless settings

Let me know what does/doesn't work.

---

### Post by GolfGeek on 2006-03-20
The instructions did return "driver present, hardware present"
The next instruction "modprobe ndiswrapper" returned an error.
At that point I rebooted the system and repeated the instructions

modprobe ndiswrapper"
sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
carl@calibsys:~$

Look like we're getting close!!!

I just checked the networking and wlan0 is present but not configured. Have to get the ssid and try to remember the wpa setup. If I have to, I can always reconfigure the router.

---

### Post by Zelut on 2006-03-20
note: you should be using 'sudo modprobe ndiswrapper' if you are not

ok.  You can try to configure your card now (System > Admin > Networking).  It should list a wireless device where you can specify your network.

You can also try this from the command line (I do everything anymore from the command line.. I'm lazy)

sudo dhclient wlan0 (assuming you use DHCP).  If you get an IP assignment you should be in business.

---

### Post by GolfGeek on 2006-03-21
Got your latest. You're right about the use of sudo. Very easy to forget to use it in the beginning. Anyway, I went to networking and have the wireless connection showing up but not yet configured. I went in, clicked to enable this connection and realized that the security setting only shows WEP and I had configured the router for WPA. I thought I had seen somewhere that WPA was available for security setting. I did manage to find my notes so at least I have access to the router settings. Next suggestion and incidently, thank you for all the help you've given so far. That was quite  an astute move a year ago to (get involved )/(make thechoice) to ubuntu.

---

### Post by Zelut on 2006-03-21
If you're wanting to setup WPA then this may be where I get off.  I haven't set that up on my network & I wont be able to help you.  If you turn it off (if only temporarily) to test you should be ready to go..

---

### Post by GolfGeek on 2006-03-21
Christer - thanks ever so much. I have it to this point. After reading the current state of affairs for WPA I think I may reset the router back to WEP. Its obviously not as secure but in this environment it should be adequate until the latest releases are published. I have more than enough to do/ read/ learn/ experiment/ etc/etc. This way I can run 100% Ubuntu. Thanks again.

---

### Post by jml on 2006-03-22
I'm on thin ice here as well, but Ubuntu does not yet support WPA "out of the box."  You will need to download an application called wpa_suppilcant to configure WPA encryption.  Two cautions.  Make sure that it supports the wireless chipset that your card is using, ( I spent over two weeks trying to configure this application before I discovered that the chipset my card used was not supported.)  If you go to the wpa_supplicant web site, you will find a list of supported chipsets.  If your card is supported, download and install the application.  The second caution is that there is no graphical interface for configuring this application.  It requires manual editing of a configuration file.  Detailed instructions as well as a sample script are available on the web site.  Hope this helps.

Joe

---

