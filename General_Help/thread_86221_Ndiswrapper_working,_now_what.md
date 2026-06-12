---
title: "Ndiswrapper working, now what?"
date: 2005-11-04
forum: General Help
---

### Post by tmmuk on 2005-11-04
Hi, I eventually got my belkin f5d7001uk wireless card working by installing a newer version of ndiswrapper (1.4) from the ndiswrapper website.

After I got it working, I opened kwifimanager, opened the configuration window, put in the root password, got into administrator mode, and put in my network settings (icluding wep key, ESSID etc)

When I hit "Scan for Networks..." It shows my network ESSID in the popup box. I can click ok but cannot select it properly.

I also tried editing my /etc/network/interfaces file. Here is the wireless bit:

```

iface wlan0 inet dhcp
wireless_keymode open
wireless_key XXXXXXXXXXXXXXXXXXXXXXXXXX
wireless_mode managed
wireless_essid XXXXXXXXXXXX
wireless_nick XXXXXXX
auto wlan0

```

How can I connect to my network?

---

### Post by mlomker on 2005-11-04
What do you get for this:

```

iwconfig wlan0
ifconfig wlan0

```

---

### Post by tmmuk on 2005-11-04
[QUOTE=mlomker]What do you get for this:

```

iwconfig wlan0
ifconfig wlan0

```[/QUOTE]

for iwconfig wlan0:
```
thomas@kubuntu:~$ iwconfig wlan0
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

for ifconfig wlan0:
```
thomas@kubuntu:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:ea020000-ea021fff


```

---

### Post by tmmuk on 2005-11-05
bump

---

### Post by tmmuk on 2005-11-06
Do you need any more info?

---

### Post by mlomker on 2005-11-06
**ndiswrapper -L** is showing driver present, hardware present?  The iwconfig output indicates that it definitely isn't working yet--the ESSID should list your access point's name.

Have you tried temporarily disabling encryption on your access point as a test?  It's nice to know if it is a driver problem or a security settings issue.

---

### Post by tmmuk on 2005-11-07
[QUOTE=mlomker]**ndiswrapper -L** is showing driver present, hardware present?  The iwconfig output indicates that it definitely isn't working yet--the ESSID should list your access point's name.

Have you tried temporarily disabling encryption on your access point as a test?  It's nice to know if it is a driver problem or a security settings issue.[/QUOTE]

I will try that. The only problem is that I cant seem to configure my AP any more through the web based interface. It is a Belkin Pre-N router (try google) and It had an option for setting it only fo use as an access point. Ever since changing that I have not been able to configure it, though several devices that worked before the change still work now. I think that since it has come an AP, and an attached device on the network, it has lost its static ip and been given a dynamic ip which might be stopping me from configuring it. One strange thing is that the reset switch on the bottom doesnt seem to work. I reckon setting it as an AP changed the firmware and seems to be a one-way path. Also I think I might have had mac address filtering on, which complicates things. The strange thing is though, if I enable wireless on my router (a netgear one, used as a router/modem - the pren router is used for wireless) I do not pick it up when scanning from my linux box.

Also my internet connection over ethernet seems to have failed. You can read about it here: [http://kubuntuforums.net/index.php?topic=1411.0](http://kubuntuforums.net/index.php?topic=1411.0)

The strange thing is that I can still access samba shares and configure the Netgear router over ethernet, but no internet. Also it seems to have failed for no apparent reason, It was working then it failed. Any help with this would be great too.

Do you know how I can set my router's ESSID (and should it be the access point essid, or the router essid?) as modifying /etc/network/interfaces or using the network configurationg widget doesnt seem to work.

sorry for the long post :)

EDIT: sudo ndiswrapper -l shows:
```

bcwml5a             driver present, hardware present

```
cant see any problems there

---

### Post by mlomker on 2005-11-07
> I do not pick it up when scanning from my linux box.

I think you need to figure out how to reset the AP to defaults and reconfigure it.  

> Also my internet connection over ethernet seems to have failed. You can read about it here:

Your wireless and ethernet cards in your **ifconfig** have the same IP address, which won't work.  I'm not even sure how you managed that, unless one of them is static and the other one is coming through on DHCP.  You need to give up on the GUI and look at your /etc/network/interfaces file.

> The strange thing is that I can still access samba shares and configure the Netgear router over ethernet, but no internet. 

I may be related to the default route.  Look at the output of **route -n**

> modifying /etc/network/interfaces

That's where it's done.

---

### Post by tmmuk on 2005-11-08
can you post an example /etc/network/interfaces file (based on my one if possible) showing how to use different ip addresses for wlan0 and eth0?

thanks

---

### Post by mlomker on 2005-11-08
[QUOTE=tmmuk]can you post an example /etc/network/interfaces file (based on my one if possible) showing how to use different ip addresses for wlan0 and eth0?
[/QUOTE]

It'd be easier if you posted yours first.  If you are using DHCP on both interfaces then it shouldn't be possible to have the same address on both.

Static addresses are similar to this, and DHCP is similar to what you already posted.

```

iface eth0 inet static
   address 10.2.1.10
   netmask 255.255.0.0
   gateway 10.2.1.1

```

---

### Post by tmmuk on 2005-11-08
Just checked my /etc/network/interfaces file

The eth0 and wlan0 Ips were both the same
I have changed them both from 192.168.0.7 to 192.168.0.7 and 192.168.0.8

I will tell you if I get it working (rebooting now)

EDIT: still not working after reboot :(

here is the out put of **route -n**:
```

Kernel IP routing table
Destination         Gateway           Genmask        Flags   Metric  Ref  Use  Iface
192.168.0.0         0.0.0.0           255.255.255.0  U       0        0     0   wlan0
192.168.0.0         0.0.0.0           255.255.255.0  U       0        0     0   eth0

```

should the "destination" be my router ip? or should the "gateway" be my router ip? or neither?

---

### Post by mlomker on 2005-11-08
You won't want to have two interfaces on the same subnet at the same time.  You can **sudo ifconfig wlan0 down** or eth0, whichever you aren't using.

There also doesn't seem to be a default route listed there.  Did you specify a gateway?

---

### Post by tmmuk on 2005-11-08
[QUOTE=mlomker]Did you specify a gateway?[/QUOTE]

No, I dont think so. Where can I specify one? Is it my router ip?

---

### Post by mlomker on 2005-11-08
[QUOTE=tmmuk]No, I dont think so. Where can I specify one? Is it my router ip?[/QUOTE]

Yes, your router IP.  Refer to post #10 in this thread.  You might want to post your /etc/network/interfaces file.

---

### Post by tmmuk on 2005-11-08
After several failed attempts on getting it working, I decided to try removing anything to do with wlan0 from my /etc/network/interfaces file (but made a backup first) After a reboot that seems to have worked, although it isnt really a fix to my wireless problem, though it does allow me to get internet, which is good.

Im guessing it didnt like the two (waln0 and eth0) having similar settings.

---

### Post by jrmann1999 on 2005-11-08
for bcmwl5a driver based nics, sometimes NDISwrapper imports their settings with the radio disabled.  Check /etc/ndiswrapper/bcmwl5a/*.conf and make sure you don't see a line like RadioState|1, it should be a 0 if I'm not mistaken.

---

### Post by delfaver on 2005-12-08
Howdy, not to interject (only fair to warn you I am a novice with this), but I have been working on getting my wireless to work for a number of days also and have found some things not mentioned yet:

1.  Even though I'm using a broadcom internal wireless card I also am running it on an AMD 64 system and had to run an AMD 64 generic driver to load the wlan0 at all.  I found this on Linuxant's web site.
2.  I have two nic cards in my laptop eth0 and wlan0 and eventhough I could enter the ip of my wireless access card and login to it, DNS and other aspects would not work until I unloaded the eth0 card (discussion on Linuxant).
3.  I had to manually input the gateway.  (discussion on Linuxant)
iwconfig add gw xxx.xxx.xxx.xxx
4.  I had to manually input the mode 'managed' (discussion on Linuxant)
iwconfig wlan0 mode Managed
5.  I had to manually input the essid for my access point, no security. (discussion on Linuxant)
iwconfig wlan0 essid accesspointname
6.  I also added 'modprobe ndiswrapper' to the wireless.conf file. (my own maybe, maybe not brilliant idea)

All that said, I still don't have internet connectivity.  When I did the above steps, particularly number 2, I did notice that DNS did resolve ip addresses.  I put an ipaddress in the url of the browser and where before it would just crap out, I noticed it did in fact resolve the Ip address to the domain name.  Just did'nt get to it.  Hope some of this may help.

---

### Post by Slayback on 2006-02-21
[QUOTE=tmmuk]The only problem is that I cant seem to configure my AP any more through the web based interface. [/QUOTE]
When you change the router to AP mode, it sets a static IP address of 192.168.2.254.  Add a route to that network, or just change something to a static in that network range temporarily to be able to access the router and set the static IP to something within your network.  If you need help with doing this in Ubuntu, let me know.

Sorry for raising this from the grave, but I just bought this Belkin PreN router and NIC yesterday and am also trying to get it going with ndiswrapper.  Anyone else have any good luck?

---

