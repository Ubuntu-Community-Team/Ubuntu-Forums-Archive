---
title: "How do you control your wifi?"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by Zyzzyva100 on 2005-12-01
I have had ubuntu on my thinkpad x31 for a little over a week now, and I am loving it.  Breezy really makes for a nice distrobution for laptops, save a few things.

The only things that are really annoying me at this point revolve around networking.  The combination of slow boot times (as it searches) and fighting with the network manager to connect are getting on my nerves.

For the boot times, i tried editing the /etc/network/interfaces file to remove auto etho and auto atho, but since I have to go to configure the network everytime I change access points (and I only use 2, work/school and home), it overwrites any changes i make to the file.  I also tried a trick that was in a thread about hoary, and was supposed to make the dhcp aquire go in the background, but that failed because the interfaces file always writes the essid of the last access point used to it, so when I come from work to home or visa versa, it is always looking for the wrong access point.

As for the management of the connection, I have tried gtk-wifi (doesn't work at all, I guess maybe this is a problem with the atheros chip?  too bad since its actually easily supported with madwifi) and wifi-radar, which just disconnects every 30 seconds or so.

I am left using the network manager, and going to configure (and having to type in my password) every time I boot up.  I even tried using the location profiles to make it easier, but once again it seems to always save the last ssid used to both profiles, so thats useless too.

Has anybody found a better way to manage wireless?  I only have 2 ssid's to connect to, and windows was able to handle this without problem.  I just had a preferred list with the 2 in there, and it worked fine.  I think the issue wifi-radar was having is that at work/school there are about 15-20 access points at any given time that are available (they all have the same ssid though), and it just wasn't connecting to the strongest signal (which windows always seemed to do).  So, any ideas on how to better manage the wireless?  I have work arounds figured out, but I would love to have a more stable solution.

---

### Post by Zyzzyva100 on 2005-12-01
Well the other thread in here about the T42 with the link to [http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#middlebutton](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#middlebutton)

has pretty much solved all of the problems I was having.  Still a little slow on "bringing up network connections" on boot, but everything else is good.

That link is a great read for thinkpad users, I am surprised that I missed it before.

---

### Post by Lambert on 2005-12-01
Glad to see you your problem was solved. Just some fyi for you if interested.

You can control network access through virtual interfaces so they're not overwritten and you can set up multiple acess points. This would prevent your interface file from being overwritten. 

So here is the basics.

In your interface file you would set up some stanzas like this.

iface home inet dhcp
xxxx
xxxx
xxxx

iface work inet dhcp
xxxx
xxxx
xxxx
xxxx

iface open inet dhcp
xxx
xxx
xxx

Then from the command line you can bring up an interface by typing

ifup eth0=home

or work, or open or whatever you name it.

There's also something called guessnet where you can set up your interface and when it sends out the broadcast to bring up the interface it checks for a familiar ap based on info in your interface file. This of course though is being replaced by network manager and the like.

---

### Post by Zyzzyva100 on 2005-12-02
Thanks for the extra info.  Network manager is working perfectly!

One question though, is there a way to make it so that the computer doesn't go through "configuring network interfaces" on boot?  I have to control-c it every time or else booting takes forever.  But network manager brings up my networking interfaces just fine regardless, so how can i get rid of this boot-time service?

---

### Post by jamesrw on 2005-12-03
application called wifi-radar works well.... can be installed through synaptic 'add applications'

---

### Post by zi99y on 2005-12-06
[QUOTE=Zyzzyva100]One question though, is there a way to make it so that the computer doesn't go through "configuring network interfaces" on boot?  I have to control-c it every time or else booting takes forever.  But network manager brings up my networking interfaces just fine regardless, so how can i get rid of this boot-time service?[/QUOTE]

I have this slow boot too and end up breaking out the network interface lines. Anyone know how to remove them if they aren't necessary?

---

### Post by JackDog on 2005-12-06
Speaking of **Network Manager**... Where is it? I have universe and multiverse defined in synaptic but "Network Manager" is no where to be found. I believe when I had SUSE10 installed it used this tool, and it was very very nice.

---

### Post by funkydan2 on 2005-12-06
It's in universe ... [http://packages.ubuntu.com/breezy/net/network-manager](http://packages.ubuntu.com/breezy/net/network-manager)

---

### Post by Corvillus on 2005-12-11
As for the people complaining about the network interface probes on boot, you can disable those by going into System -> Administration -> Networking and disabling all the interfaces (I don't think network manager or wifi-radar use them anyway, as they pick up my interfaces just fine regardless).

---

### Post by zi99y on 2005-12-11
I managed to fix the slow boot by removing the "auto" lines for eth0 and eth1 in /etc/network/interfaces

Network manager is pretty nice but I'm wondering why I have about 20 nm-applet processes running at once? if I kill them they just respawn......

---

### Post by JackDog on 2005-12-12
[quote=Corvillus]As for the people complaining about the network interface probes on boot, you can disable those by going into System -> Administration -> Networking and disabling all the interfaces (I don't think network manager or wifi-radar use them anyway, as they pick up my interfaces just fine regardless).[/quote] 
I tried following this advice, as well as editing the interface file by hand. Neither will fix the bootup problem. When I boot it still spends 60 seconds configuring something, however once I have booted they are never setup anyway. 

To me, this is the missing piece for Ubuntu. Network configuration and switching should be **completely** seamless to the user. No system passwords or extra dialogs to modify the network settings. Network Manager is definitely a step in the right direction. But even that product needs better integration with Linux/Gnome/Ubuntu.  

For instance if you bootup and only a wireless connection is available, that you have used before, it should connect automatically. If you havent used it before, you should need to log in, and select it via Network Manager. 

If a wireline connection is available, it should just activate it since the user has knowingly plugged in the cord. Network Manager should then enable the user to switch the default interface. It almost does this now, its just not intelligent enough and the tools conflict.

---

### Post by zi99y on 2005-12-12
[QUOTE=JackDog]I tried following this advice, as well as editing the interface file by hand. Neither will fix the bootup problem. When I boort it still spends 60 seconds configuring something, however once I have booted they are never setup anyway. [/QUOTE]

JackDog - can you post the contents of your /etc/network/interfaces file? It's strange as this fix worked for most of us.

---

