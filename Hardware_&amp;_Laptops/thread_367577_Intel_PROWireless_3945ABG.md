---
title: "Intel PRO/Wireless 3945ABG"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by ELD on 2007-02-22
Anyone know how i can get that wireless to work?

---

### Post by nachotronics on 2007-02-24
If you card doesn't work out of the box, you can get it working following **[these steps]("http://www.ubuntuforums.org/showthread.php?t=297092&highlight=edgy+dell+1390")**
The driver in that post is the one for any of these cards:

Dell Wireless 1350 WLAN MiniPCI Card, 
Wireless 1350 WLAN PC Card, 
Wireless 1370 WLAN MiniPCI Card, 
Wireless 1390 WLAN ExpressCard, 
Wireless 1390 WLAN MiniCard, 
Wireless 1450 WLAN miniPCI Card, 
Wireless 1470 Dual-Band WLAN miniPCI Card, 
Wireless 1490 Dual-Band WLAN MiniCard, 
Wireless 1500 Draft 802.11n WLAN mini Card

The procedure is exactly the same for your card using ndiswrapper, but you will need to get the windows drivers for your wlan card.

After getting your wlan working you might want to install network-manager-gnome following **[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**. This utility helps you set up WEP or WPA secured networks

---

### Post by Lorenz on 2007-02-24
Actually your card should work out of the box. It does for me - with more problems, but that's not the topic now. No need to install drivers. I had to restart the computer after the install and then it was recogniced!

---

### Post by ELD on 2007-02-25
> **nachotronics said:**
> If you card doesn't work out of the box, you can get it working following **[these steps]("http://www.ubuntuforums.org/showthread.php?t=297092&highlight=edgy+dell+1390")**
The driver in that post is the one for any of these cards:

Dell Wireless 1350 WLAN MiniPCI Card, 
Wireless 1350 WLAN PC Card, 
Wireless 1370 WLAN MiniPCI Card, 
Wireless 1390 WLAN ExpressCard, 
Wireless 1390 WLAN MiniCard, 
Wireless 1450 WLAN miniPCI Card, 
Wireless 1470 Dual-Band WLAN miniPCI Card, 
Wireless 1490 Dual-Band WLAN MiniCard, 
Wireless 1500 Draft 802.11n WLAN mini Card

The procedure is exactly the same for your card using ndiswrapper, but you will need to get the windows drivers for your wlan card.

After getting your wlan working you might want to install network-manager-gnome following **[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**. This utility helps you set up WEP or WPA secured networks

Thanks but my card is the title of this topic, and the card is not in that list.

And i will stick to windows until linux gets better at this, just easier for now.

---

### Post by Ek0nomik on 2007-02-25
Correct, your card isn't in that list.  However he said you just have to get the drivers for your card instead of the ones posted.  The guideline should still work.

My wireless card still doesn't work, but I plan on continuing to try.  :)

---

### Post by ELD on 2007-02-25
Problem is i can't do anything ubuntu won't even pick up my wiredconnection from my router when i plug it in. Have tried restarting and it does nothing, why can't it just work, a question i always ask with linux.

---

### Post by Ek0nomik on 2007-02-25
> **ELD said:**
> Problem is i can't do anything ubuntu won't even pick up my wiredconnection from my router when i plug it in. Have tried restarting and it does nothing, why can't it just work, a question i always ask with linux.

Well, that's what people are trying to figure out my good friend.  It's not as if people don't want things to work.  They are trying.  They aren't getting paid to make this better.

As far as a wired connection, in most cases it picks it up automatically.  I know it always has for me.  That's something that should work out of the box.

If it isn't working, search the forum for your network card.

---

### Post by treesurf on 2007-02-25
That wireless card should work out of the box.  It did on my laptop, at least.

Have you tried going to System>Administration>Networking to enable the card and configure the connection?

---

### Post by falcons7 on 2007-02-26
Also, to make your life a little easier. I suggest Installing gnome network manager. It can be installed via system>Administration> Synaptic Pagage Manager

this program will allow you to connect to any type of network including wpa and wpa2

---

### Post by ELD on 2007-02-27
> **falcons7 said:**
> Also, to make your life a little easier. I suggest Installing gnome network manager. It can be installed via system>Administration> Synaptic Pagage Manager

this program will allow you to connect to any type of network including wpa and wpa2

That the thing, i can't install it, i have no net in ubuntu!

---

### Post by Praill on 2007-02-27
Im using the Intel PRO/Wireless 3945ABG as well and it worked out of the box. Poorly, but it still worked.
One thing I noticed with my installation was that the ubuntu install turned off my hardwares wireless switch on my laptop. For me I had to hit fn+f2 to turn it back on (Dell Inspiron 6400), but Im not sure where your wireless switch is.

Also, since the highly unlikely situation has occurred that the LAN adapter does work, I would assume you just need to configure the the network properties. System-->Administration-->Networking.
The devices might not be enabled, or might not be set to auto dhcp.

For the record, this is no different than windows xp. You are just used to windows xp so you can install things easier. Once you get used to linux you'll actually be amazed at how many more things are recognised from the install. For me, edgy recognises everything (except for my winmodem :mad:) I only have to install 3d acceleration on my video card. Windows fails to recognise about 10 devices, including both NIC's.

---

### Post by ELD on 2007-02-27
Well if someone would like to give me a walkthrough on how to get started i would appreciate it.

I would like wireless, i don't care about the wired as i will never use it.

---

### Post by ELD on 2007-02-28
A note:

Wireless with this laptop and chipset works perfectly in Feisty Herd 4 :D

---

### Post by Praill on 2007-02-28
> **ELD said:**
> Well if someone would like to give me a walkthrough on how to get started i would appreciate it.

I would like wireless, i don't care about the wired as i will never use it.

Well, there is a linux driver for this wireless card [http://ipw3945.sourceforge.net/]("http://ipw3945.sourceforge.net/"), but this module should be included with the ubuntu install.
Can you try 
```
iwconfig
```
in a terminal and post the output?

Btw, are you running the live CD or an actual install?

---

### Post by ELD on 2007-03-01
Well to install the one you sent me i have to install some other subsystem, and something else, do some compiling and that is just not acceptable to me.

It works perfectly in Feisty Herd 4, is there anyway to get it to work like it for edgy?

---

### Post by CrazyTn on 2007-03-02
ELD all you have to do is install the linux-restricted-modules-generic

---

### Post by ELD on 2007-03-02
Well i am going to stick with Fiesty, much less hassle to me, thanks for the replies guys, i am sure this will help someone else :)

---

### Post by ELD on 2007-03-02
> **CrazyTn said:**
> ELD all you have to do is install the linux-restricted-modules-generic

Where can i find these for edgy?

---

### Post by CrazyTn on 2007-03-02
Do a search for it in Synaptic Package manager. 

I am using a Dell E1505 and it works for me
Should work for you also,

---

### Post by ELD on 2007-03-02
Yeah got them now, problem sorted, cheers.

---

### Post by CrazyTn on 2007-03-02
Glad that 1 newbie can help another :)

---

### Post by new-one on 2007-03-15
Hello All, 

I have the similar problem with this card.
I have a VAIO VGN-FE31H

Get below some info.

most@TRAK:~$ dmesg |grep -i Wireless
[17179588.376000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179588.456000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
most@TRAK:~$ lsmod |grep 3945
ipw3945               124576  0
ieee80211              35272  1 ipw3945
most@TRAK:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

most@TRAK:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:A9:4A:39:D0
          inet addr:172.16.40.53  Bcast:172.16.40.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe4a:39d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:431241 (421.1 KiB)  TX bytes:10345 (10.1 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          inet6 addr: ::172.16.40.53/96 Scope:Compat
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

This laptop has a switch. Even when I turn it to ON the led remains dark. 
On windows when I set it to on the led is shows that the wireless is on.

Do you have any ideas of what might be happening?

Thanks

---

