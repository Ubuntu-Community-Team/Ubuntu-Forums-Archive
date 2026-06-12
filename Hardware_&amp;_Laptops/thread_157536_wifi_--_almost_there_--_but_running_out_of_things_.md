---
title: "wifi -- almost there -- but running out of things to try"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by rosslaird on 2006-04-09
I have installed ndiswrapper and seem to have a running wifi setup.
ifconfig -a shows this for my card:

eth1      Link encap:Ethernet  HWaddr 00:16:CE:00:35:7A
          inet6 addr: fe80::216:ceff:fe00:357a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Memory:e2000000-e2002000

But I seem to missing a step, or something is wrong, because the wifi does not seem to be working. When I remove the cable for eth0, and run something like 
dhclient eth1, I get a "no offers" message. Also, dmesg says "no IPv6 routers present". I don't think the router is the problem, but I'm stuck.

Help would be very nice.

Ross

---

### Post by hajk on 2006-04-09
You must configure the wireless interface, like in System -> Administration -> Networking. If your driver is properly set up, then there should be a wireless interface eth1, highlight it and then choose Properties. Make sure you enable the interface, then pick your network, choose DHCP, provide the WEP key, and OK it all. Then, on the first window again, activate eth1 and choose it as gateway. That should do it, in most cases. Make sure that eth0 is not activated (or at the least is not the default gateway).

Have fun!

---

### Post by rosslaird on 2006-04-09
Thanks for the help.

I followed your suggestions, and I seem still to be missing something.
The wifi card is active, the networking is setup as instructed, eth1 is the default gateway, eth0 is off. Still no dice. ( I did not enter a WEP key, but I do not know what the key value would be, nor how to find it - however the key did seem to be entered already in the dailog box, like this: ***)

Kwifimanager shows the card, and says this:

Out of Range
Access Point: N/A
Local IP is listed as "unavailable"
(The connection speed shows 54, with a nice green line.)

"Scan for Networks" yields no networks found. As for out of range, the laptop is two feet from the router...

---

### Post by hajk on 2006-04-09
Well, your router may be set up to expect a WEP key (it may be listed on a label on the bottom of the router, it could be in hex or ASCII characters). Another issue: the router may accept new connections only for a short while (like a minute) after giving a longish push on a button, or after changing a setting when logged in to the router via another (possibly wired) connection. These are not Linux (Ubuntu) problems, read the documentation that came with the router for details.

---

### Post by rosslaird on 2006-04-09
Nope, my router is set up to accept connections with security. Other laptops plug-in fine.

I have managed to get the wireless card to see the router's wifi network, but everything I try with iwconfig results in "Access Point: Not Associated" or "Cell Not Associated". (I have tried specifiying the ap in iwconfig.)

---

### Post by jml on 2006-04-09
Is your wireless access point/router set up to use WEP or WPA encryption.  

If its WEP, is the security key or pass phrase typed in ASCII text or Hexadecimal?  You need to type in the correct key in Network manager for WEP to work.

If it is using WPA encryption, you job will be a little bit harder.  Ubuntu does not support WPA encryption out of the box.  You will need to download, install and manually configure an application called wpa_supplicant.  If you "Google" on the term wpa_supplicant, one of the first few sites listed will be the wpa_supplicant web site.  First check to see if the chipset of your wireless card is supported, (I spent two weeks trying to make it work before I discovered my chipset was not supported.)

Then, if you enable the "Unsupported" Ubuntu repositories, (Universe and Multiverse) then go into Synaptec, update your sources list and then search for wpa_supplicant.  Once you find it, install it.

The wpa_supplicant website has a very good set of installation instructions along with a generic configuration file to use as a starting point for your own configuration efforts.  Configuration must be done by manually editing a configuration file with a text editor like Gedit.

Hope this helps.

Joe

---

### Post by rosslaird on 2006-04-09
[QUOTE=jml]Is your wireless access point/router set up to use WEP or WPA encryption. [/QUOTE]

Nope. I turned all security on the router off.

I'm beginning to think that the router is dodgy -- because the wifi card seems to be doing everything correctly. In fact, there is an article I just picked up today in the latest issue of Linux magazine about configuring wifi with my exact (almost) laptop. I followed all the steps in the guide and -- everything checks out fine until the task is to find the access point. Then nothing. Also,  I've had some network difficulties (non-wireless) lately that may be attributable to a router in yo-yo mode. I'm going to run out and get a new router and see what happens.

---

### Post by rosslaird on 2006-04-10
Well, it wasn't the router... I installed a new router and am still having the same problem: Access Point Not Associated. Scan turns up no results. This is so weird, and so frustrating. I'm almost ready to justy buy a card I can plug in...

---

### Post by rosslaird on 2006-04-10
Update:

My new router config says encryption is off, "iwlist eth1 scan" says encryption is off, but when I scan for networks using kwifimanager, it shows that encryption is on. Maybe this is closer to my problem...

---

### Post by Ensnared on 2006-04-10
I've had some issues that seem a bit similar to yours with my previous wireless-card - I chalked it up to driver incompatibility with my hardware (was an Accton W3101A or something, LAN/56k modem miniPCI combo). It's supposed to have a standard prism chipset, but apparently it didn't - I ended up replacing the card with an Intel instead, which works.

Anyway, if that isn't the problem it may be that ESSID-broadcast is turned off in your router. What you can try is editing /etc/network/interfaces and add the necessary entries there, like so:
```
iface eth1 inet dhcp
	wireless-essid YOUR-ESSID
	wireless-key YOUR-WEP-KEY
```
Then run ifdown eth1 followed by ifup eth1. Atleast that's all I had to do with my card - the one that works, that is ;)

---

### Post by rosslaird on 2006-04-10
OK, wait, hang on --- 

I removed the wlan driver, removed ndiswrapper, installed a new driver, installed the most recent ndiswrapper from source, re-ran the steps, and it works!

Now I'm afraid to turn off my machine...

---

### Post by YuHoo on 2006-04-10
1) What card do you have?
2) Check for supplied drivers that are compiled specifically for linux, like for intel - ipw2200
3) Make sure you're broadcasting your ESSID and put a 128bit WEP encryption on the signal without a password

You shouldn't worry to turn off your computer, you can always rescue from mistakes with the Ubuntu CD. Those three steps above are my best guess, and are what I'd do in your position. I'd also recommend that you get some comfort food and try to relax, maybe walk away from this for a while. The more tense you get the more likely you'll make small errors.

---

### Post by rosslaird on 2006-04-11
Thanks to everyone for all the tips and suggestions (technical as well as psychological...).

In case anyone else has a similar problem with an acer aspire 5000 laptop, here are some suggestions:

1. Don't use the driver from the cd. Instead, go to one of the official acer support sites (there are several, just google them) and follow the driver links. Enter your laptop version and download the exact driver for it (the cd driver seems to be more generic).

2. Download and compile the latest ndiswrapper from source. Use one of the guides from the ubuntu wiki if you get stuck. (Search the wiki for "ndiswrapper.")

3. Load the driver into ndiswrapper and load the module (modprobe ndiswrapper).

4. Check dmesg to make sure there are no error messages ("tail /var/log/messages" or just "dmesg".

5. Use iwconfig to see the device (mine is eth1).

6. Use iwlist eth1 scan to see where the access point is. (eth1 is my device; yours may be different.)

7. Use "sudo iwconfig eth1 essid name_of_access_point mode managed enc off open channel 6" (substitute your own info for the access point and encryption and channel).

8. "sudo ifconfig eth1 up" (or whatever the device is called).

9. "sudo dhclient eth1" (or whatever...)

10. "sudo ifdown eth0" (if you have a wired interface also).

These steps worked for me, after many hassles. The important thing seems to be to match the driver to the machine, and both to the correct version of ndiswrapper (the repository version did not work for me).

Cheers.

Ross

---

### Post by YuHoo on 2006-04-11
There ought to be a sticky of just what people have done to fix problems with their laptop wifi. I've heard of problems across the board and there should just be a localized area to get help.


Good to hear you fixed the problem!

---

