---
title: "PLEASE HELP! installing gnome on top of server install"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by Choad on 2005-12-23
the default installation of ubuntu makes my laptop run too slow, it only has 128 mb of ram. so im starting from the beggining, and i have done a server install. i cant get that laptop on the internet so everything has to come from the breezy cd. 

so far i have installed x window and gnome through apt-get

now when it starts up, it boots in to an (albeit wierd resolution) gnome startup screen. asking for username and password. however i cant login, because it says there is no .xsession file, no session manager and no window manager.

im not exactly teh l33t linux haxor, i am just googling for various how-to's and fumbling my way allong

please, please PLEASE can i get some help setting this up.

(oh and i suppose i could get on the internet, but it would involve someone telling me how to get a usb wlan card setup and active through a console)

thanks in advance

---

### Post by kaamos on 2005-12-23
You could try this, worked very well for me:
[http://ubuntuforums.org/showthread.php?t=75971](http://ubuntuforums.org/showthread.php?t=75971)

---

### Post by Choad on 2005-12-23
[QUOTE=kaamos]You could try this, worked very well for me:
[http://ubuntuforums.org/showthread.php?t=75971](http://ubuntuforums.org/showthread.php?t=75971)[/QUOTE]

that requires being attatched to the internet.

---

### Post by kaamos on 2005-12-23
Whoops. I'm sorry. Then I think this could be useful: [http://ubuntuforums.org/showthread.php?t=101790](http://ubuntuforums.org/showthread.php?t=101790)

So you get the necessary files on a cd and then can install them. Xubuntu uses the xfce window manager that is lighter than gnome, it was sort of trying to be the point of my post to try that. :)

---

### Post by varunus on 2005-12-23
Well, there's no reason you couldn't get your usb wlan card working through the console.  Linux consoles and GUIs have no difference, really; the GUIs are just a layer on top of console commands.

First of all, lets see if your card was detected.  Type "ifconfig" and see if your card is listed there.

I get output like this, showing me that my card was detected:
```
ath0      Link encap:Ethernet  HWaddr 00:90:96:8B:02:5C
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:749212 errors:1116683 dropped:0 overruns:0 frame:1116683
          TX packets:649672 errors:15945 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:724377002 (690.8 MiB)  TX bytes:184419821 (175.8 MiB)
          Interrupt:22 Memory:efb60000-efb70000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13298194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13298194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1473513276 (1.3 GiB)  TX bytes:1473513276 (1.3 GiB)

```

If you do, then you said its a wireless card?  Do the following:
Type:
```
sudo iwconfig ath0 essid SSIDOFROUTER
```
```
sudo dhclient ath0
```

Replace ath0 with whatever your card shows up as (lo is the loopback, this is not your card).

If your card doesn't show up, how did you get it set up the last time you used GNOME in the GUI?  We can duplicate this from the console.

---

### Post by greenwom on 2005-12-23
Good idea to follow the thread above.

List what kind of wireless adapter you have (exact model), we should be able to get you online pretty easy.

I have two P3 machines with 128mb of RAM and they run ok.  Do you have a swap partition? 
the command 'free' will tell you about your memory:
just type free

---

### Post by Choad on 2005-12-23
ok i have a netgear wireless card, and i need to use ndiswrapper with it, i have done it before. at the moment im installing ubuntu-desktop, so i'll see if that helps and get back to you all if i need more help. 

thanks for the replies :D

---

