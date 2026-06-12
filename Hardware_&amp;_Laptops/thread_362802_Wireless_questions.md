---
title: "Wireless questions"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by Boule on 2007-02-16
Hi,

I just installed ubuntu on my laptop (dell, intel wireless card, nothing fancy). I managed to get the wireless connection to work using the GUI (system->administration->network). I had to manually enter the ESSID in order for the connection to work. I have 2 questions:

1. Isn't there a way to scan for available networks ? What if I don't know the ssid, but i want to get a connection (like in a restaurant or hotel or something)

2. If I'm switching between 2 locations, isn't there a way to make both connections work automatically, or do I have to reconfigure every time I want to connect to one ?

Thx for ur help,
Boule

---

### Post by l:x on 2007-02-16
Hello Boule,

I use "[NetworkManager]("http://www.gnome.org/projects/NetworkManager/")" wich displays a list of available wireless networks when you click on the applet icon.

If you're using GNOME, just install the "network-manager-gnome" package and all deps will be installed too.

This tool also helps you with your "switching locations" problem.

Kind regards,
Niels R.

---

### Post by gradedcheese on 2007-02-16
I prefer the shell, so if you don't mind using it too, then fire it up with Applications->Accessories->Terminal

```

iwconfig

```

This will show you the status of your wireless interface (and tells you its name, like eth1 or wlan0 or whatever).  Now to scan (say the interface is "wlan0")

```

sudo iwlist wlan0 scanning

```

If you do choose NetworkManager, be aware that you'll need to edit /etc/network/interfaces to comment out (put "#" in front of lines having to do with) your wireless interface from that file.  You'll then want to run "sudo /etc/init.d/networking restart" and log out and then back in.

---

### Post by Boule on 2007-02-16
Thx for ur help !!

I checked the network manager page, and i saw a field called VPN connections in the screenshot. Does the application also handle them or do I need to download cisco's client anyway ?

I just noticed I posted in the wrong category, sorry about that...

---

### Post by Agatsu on 2007-02-16
> **gradedcheese said:**
> I prefer the shell, so if you don't mind using it too, then fire it up with Applications->Accessories->Terminal

```

iwconfig

```

This will show you the status of your wireless interface (and tells you its name, like eth1 or wlan0 or whatever).  Now to scan (say the interface is "wlan0")

```

sudo iwlist wlan0 scanning

```

If you do choose NetworkManager, be aware that you'll need to edit /etc/network/interfaces to comment out (put "#" in front of lines having to do with) your wireless interface from that file.  You'll then want to run "sudo /etc/init.d/networking restart" and log out and then back in.

Extreme newbie questions: I have a Dell D610 with Broadcom wireless NIC. My networking GUI indicates that it sees the NIC as wireless, but the iwconfig command you recommended indicates the NIC is eth1 not wlan0. The wireless isn't working, so I'm assuming this is part of the issue. thx for any help.

---

### Post by Boule on 2007-02-16
My wireless is seen as eth1 and it works fine, that's not the issue...

---

### Post by gradedcheese on 2007-02-16
generally speaking, the WiFi interface you should be configuring is the one that iwconfig shows as having wireless extensions.  It gets a little weird because some cards provide two interfaces (real wifi and management) while most don't.  If it's a removable card (PCMCIA or the like) you can unplug it, see what interface you have, and then plug it back in and see what you have ;)

---

### Post by Agatsu on 2007-02-16
Thanks for the info!
I was picking around the forum and someone recommended installing the latest ndiswrapper and drivers, so I'll give that a try.

---

### Post by Boule on 2007-02-16
Anyone knows about how NetworkManager handles VPN connections ?

---

### Post by Boule on 2007-02-21
All right, dumb question: after I install network-manager and netwoek-manager-gnome, how do I lauch the application ? I can't see it anywhere in the menu, and alt+f2 didn't work...

How about wireless assistant ? I think it's for KDE, but it works on gnome... Is it any good ?

---

### Post by gradedcheese on 2007-02-21
Log out of gnome and then back in.  If you want to launch it manually:

```

nm-applet &

```

don't use the KDE thing.  NetworkManager will be standard on Ubuntu in the next release anyway.

---

### Post by Boule on 2007-02-22
Yeah I can see it ran when I relogged. But I don't understand how/why, I couldn't find it in the session startup manager ??

---

### Post by gradedcheese on 2007-02-22
> **Boule said:**
> Yeah I can see it ran when I relogged. But I don't understand how/why, I couldn't find it in the session startup manager ??

It's an applet, they don't get listed in the session... that's only for regular applications.  Notification Area Applets just pop up by themselves, sort of like the Update Manager, for example.

---

### Post by Boule on 2007-02-22
It says "no network connection" while I'm online... how can i make it find my network interface ?

---

### Post by gradedcheese on 2007-02-22
You need to remove the interface in question from /etc/network/interfaces -- that is, put a '#' in front of the line:

```

auto wlan0

```

Edit that file with sudo and substitute 'wlan0' for the name of your interface, if it's different.  Then restart networking and it should find your interface (you might have to log out and log back in, I am not sure).

---

### Post by Boule on 2007-02-22
Thanks a lot for your help !

I commanted the lines, but it didn't help... here's how the file looks like now. The wireless is eth1
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
iface wlan0 inet dhcp


iface eth1 inet dhcp
wireless-essid
wireless-key









#auto eth1

```

---

### Post by gradedcheese on 2007-02-22
right... now do

```

sudo ifdown eth1

```

or 

```

sudo /etc/init.d/networking restart

```

Then log out of gnome and log back in, I think.

---

### Post by Boule on 2007-02-22
Still nothing... But I had to manually reactivate eth1 from the networking tool. ifconfig eth1 up didn't seem to work. Well actually ifconfig said it was already up, but I had to check "enable this connection" to reconnect.

---

### Post by gradedcheese on 2007-02-23
try this, comment out the 'auto eth1' and 'iface eth1' lines and then save and reboot the PC entirely.

---

### Post by Boule on 2007-02-23
Ok, it's working now :D
I went crazy on the file and removed everything related to wlan0 or eth1 :p that's how it looks now:
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#iface eth1 inet dhcp
#wireless-essid
#wireless-key









#auto eth1

#auto eth1

auto eth0

```

I didn't know the wireless connection had to be deactivated from ubuntu in order to be handled with network manager, I thought it was a layer on top or something !

Anyway, thanks a lot for your help !

---

### Post by Boule on 2007-02-23
Well now I have a better grasp of how things work...
All that had to be done was open system->administration->networking and remove the configuration of the wireless by unchecking "Enable this connection". That corresponds to removing the wireless-essid and wireless-key lines. All the rest can stay !

---

### Post by kristalsoldier on 2007-02-23
Hi...

I was trying out the EdgyEft from a Live CD. Had tried the Dapper earlier and had problems with the printer...but on this latest one, the printer works but not the wireless.

Am using a Sony Vaio with an inbuilt Intel wireless...

I did a iwconfig in the Terminal (APP>TERMINAL)

Here is what it spits out:

[INDENT][/INDENT]lo no wireless extensions.
eth0 no wireless extensions.

eth1 unassociated ESSID: "XXXXX" (where XXXXX is the SSID which I entered in System>Admin>Netwrorking)
Mode: managed Frquency=nan kHz Access Point: Not-Associated
Bit rate: 0 kb/s Tx-Power: 16dBm
Retry Limit: 15 RTS thr: off Fragment thr: off
Power Management: off
Link Quality: 0 Signal Level: 0 Noise level: 0
Rx invalid nwid:0 Rx invalid crypt: 0 Rx invalid frag:0
Tx excessive retries:0 invalid misc: 4 Missed Beacon: 0
[INDENT][/INDENT]sit0: no wireless extensions.

On Dapper, I has to fill in the WEP key and it worked fine!

Am still in trial mode and this is perhaps the last thing that I need to iron out. Everything else seems to be fine.

Please advise?

Thanks in advance!

Also: At the outset, I went to Network Settings and entered the ESSID and Network Password (which I am presuming is the same as the WEP password) and left the Connection Setting> Config on Auto (DHCP). I also tried the above by imputting manually the IP Add. Subnet Mask and Gateway Add. Same result!

Thanks!

---

