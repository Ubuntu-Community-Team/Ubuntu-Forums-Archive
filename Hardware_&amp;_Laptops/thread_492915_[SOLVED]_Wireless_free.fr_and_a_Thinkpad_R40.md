---
title: "[SOLVED] Wireless free.fr and a Thinkpad R40"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by siddartha on 2007-07-05
Hello,

I have an IBM ThinkPad R40 (2722-BDG) which says centrino and lspci shows
Intel Corporation PRO/Wireless LAN 2100 3B mini PCI adapter (rev 04)
The driver used is ipw2100 and from this point of view everything is ok.

Now I'm trying to make it work with a private wireless network from the French provider free.fr. My understanding is that they are using standard hardware with linux on the inside (the new HD router). My 7.04 Ubuntu sees that network and the signal is good - 97% The wireless adapter is set to DHCP and I entered the Password to gain access to the router, yet no IP is received.

So my laptop sees the network, I have the password which everybody else uses happily over various flavours of windows yet no DHCP exchange. What am I missing? I have no previous experience with wireless but on this device I'm trying to connect the UTP outlet is broken so I'm left with no other choice.

My only hint so far is from dmesg - it says no ip6 routers found.

---

### Post by randcoop on 2007-07-05
You need to provide more information, I think, before you can get help.

What interface is being used for wireless (eth0? eth1?).  Is that interface configured?  Are you using network manager or some other software to connect?  Have you tried the command line to run ifup (sudo ifup eth1)?

It's likely that this will be resolved fairly easily, but that can't be said with certainty without more information.

So perhaps show the results of:

```
iwconfig
```

and 

```
ifconfig
```

for a start.  And also tell us what software you're using to connect (meaning, did you go into System/Network and then try to enable the interface or did you use networkmanager, or did you use some other software).

---

### Post by siddartha on 2007-07-05
Well, I can't just copy&paste as I have to use a different station to get online.

So
it is eth0, eth1 being the not-working ethernet
ubuntu 7.04 autodetected everything well so probably we are talking about gnome network manager from the gnome control panel
as I don't know how to force a retry with dhcp i have used ifconfig eth0 up and down allright

I will try later on iwconfig. ifconfig gives the regular information about the hw address et all but no IP and mask a sign that dhcp wasn't successful

---

### Post by walkerk on 2007-07-05
try using [wicd]("http://wicd.sourceforge.net")

not sure this will help but it might.. you'll need to uninstall network-manager (wicd is much better than network-manager imo)

---

### Post by randcoop on 2007-07-05
I'm still a bit confused by your response.  If there are two interfaces being seen (eth0 and eth1), then it is likely that the wireless interface is eth1.  The eth0 interface is the wired connection.

If that's the case, then try using the simple command:

```
sudo ifdown eth1
sudo ifup eth1
```

WICD (the program recommended by the other poster) effectively automates the ifup (which is short for ifconfig up) and ifdown approach.  

If ifup eth1 doesn't work, post the response you get here.

---

### Post by siddartha on 2007-07-10
Sadly I can't post any of the ifconfig or iwconfig as the terminal I have at hand is an ancient pentium with win98 and no usb mass storage support.

Bonus it seems that I have to use AES encription for sending the ascii key so here's another problem: I have no encryption option.

---

### Post by siddartha on 2007-07-10
> **walkerk said:**
> try using [wicd]("http://wicd.sourceforge.net")

not sure this will help but it might.. you'll need to uninstall network-manager (wicd is much better than network-manager imo)

Util I get online with that computer I have no chance of changing the software, and I badly need some packs installed.

---

### Post by siddartha on 2007-07-10
> **randcoop said:**
> I'm still a bit confused by your response. 

I am even more confused by yours.

> **randcoop said:**
>  If there are two interfaces being seen (eth0 and eth1), then it is likely that the wireless interface is eth1.  The eth0 interface is the wired connection.

I have written my case. What is the relevance that in your newbie guide they are called differently? Do you want me to bother changing the config of the modules just to please your book?

> **randcoop said:**
> If that's the case, then try using the simple command:

```
sudo ifdown eth1
sudo ifup eth1
```

WICD (the program recommended by the other poster) effectively automates the ifup (which is short for ifconfig up) and ifdown approach.  

I have no use for automating anything as long as it doesn't work all the way.

> **randcoop said:**
> If ifup eth1 doesn't work, post the response you get here.

It does work. Yet, as it does not authenticate I don't get an IP from the DHCP. Now... what is your point?

---

### Post by imdano on 2007-07-10
Based on what you said about needing to use AES encryption, I'm guessing that the network you're trying to connect to is using WPA.  If that's the case, try following this guide.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by randcoop on 2007-07-11
For reasons that escape me, you decided to be antagonistic on a thread that you started asking for help with a problem.  If my questions annoy you, don't answer them.  If my help isn't helpful, ignore it.  If you think I have no chance of helping, talk to others in the thread.

But responding with negative comments to someone trying to help (even if not good at it or unable to do so) is an inappropriate way of using help forums.

Rest assured, I won't try helping you any more.  While I wish you luck in your effort to get on line, I'll be (pleasantly) surprised if you are able to do it.

---

### Post by siddartha on 2007-07-12
> **imdano said:**
> Based on what you said about needing to use AES encryption, I'm guessing that the network you're trying to connect to is using WPA.  If that's the case, try following this guide.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)


I will try this as soon as possible. Sadly, anyway I try it says I need more software than the default ubuntu packs. This means I have to fix the Ethernet problem, get to install some packs and use Wifi only afterwards. I was hoping to do it so I won't need to fix the Ethernet.

---

### Post by siddartha on 2007-10-16
> **walkerk said:**
> try using [wicd]("http://wicd.sourceforge.net")

not sure this will help but it might.. you'll need to uninstall network-manager (wicd is much better than network-manager imo)

And that was the correct answer I have come to realise long after.
At the time of writing this thread the wired card was broken and I was trying to get a solution as to connect with the wireless card.

Now I know that the connection was based on WPA and Network manager only knows of WEP. I needed wpa supplicant as well (why isn't this in the default config for Ubuntu? just because network manager doesn't know how to use it?). I still have no idea how to use the scripts for supplicant.

The first step was to get a PCMCIA wired net card and get the updates. Than the quest continued. I had no idea about the configuration of the wirless AP, just a password that was working for everybody else (on Windows I might add).

I found and really got help from installing kwlan (it is in the Ubuntu repositories, that is). Wifi radar is crap and it never worked for me further away than just having a nice window with a list of wireless networks in sight, and the signal strenght. Kwlan has some drawbacks (for example it does not do dhcp out of the box after connecting with the AP. It does have a nice tray icon that shows you the traffic, IP and other nice info once you have your mouse cursor above.

In the end I bit the bullet and installed wicd. Now all the other network tools are gone. In comparison with kwlan it does not have the nice systray icon with all the information. But it is system neutral. Kwlan is a KDE toy. wicd can work with xfce as well with no extra dependencies. It also shows the signal strenght, it knows to get the IP in case you don't provide one.

Both wicd and kwlan do manage wired connections as well so you might just dump all the other apps and applets and just go ahead and install these. Kwlan is in the ubuntu repository, wicd it has its own repository and they can even work side by side.

---

