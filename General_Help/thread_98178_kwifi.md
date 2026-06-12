---
title: "kwifi"
date: 2005-12-02
forum: General Help
---

### Post by dajomu on 2005-12-02
Kubuntu should remove kwifimanager from it packages, it sucks. Wifi-radar is much better and it actually works. 

Another thing, how well does klik work with KB 5.10?

Will the next release include beagle, xen and maybe something like initng?

Dajomu

---

### Post by welsh_spud on 2005-12-02
I think Wifi-radar is a GTK app (im not sure, so don't quote me on this) whereas kwifi is a KDE QT app. GTK programs just don't quite integrate well or look right in KDE, so kwifi was used.

---

### Post by dajomu on 2005-12-02
Well, I am using wifi-radar on my kubuntu and it works like a charm. Looks more like gnome program, but we want things that works instead of eyecandy right? Apart from this kde rocks.

---

### Post by mlomker on 2005-12-02
Network-manager seems to be the new hot thing for gnome...I'm hoping that there will be a QT interface for it at some point.

---

### Post by dajomu on 2005-12-03
good tip. Do you know if there is a .deb package for the network-manager

---

### Post by mlomker on 2005-12-03
[QUOTE=dajomu]good tip. Do you know if there is a .deb package for the network-manager[/QUOTE]

It's in the Ubuntu repos...probably Universe, so make sure you have all of the repos enabled.

---

### Post by holotone on 2006-01-31
nm-applet (which I beleive is the network-manager refered to above) is hands down the best wifi solution for a network roamer like me...

sudo apt-get nm-applet

Not sure which repo it's in, though, so YMMV.

---

### Post by gamma on 2006-02-01
Kwifi just seems to scout out the wireless networks, but doesn't actually start a dhcp session with them. You could find a network with that and then type dhclient wlan0, but it's a lot quicker to type iwconfig wlan0 essid networkname && dhclient wlan0....

---

### Post by sfabel on 2006-02-01
The KDE solution seems to be "wlassistant":
[http://sourceforge.net/projects/wlassistant/]("http://sourceforge.net/projects/wlassistant/")

But, unfortunately, there are no kubuntu packages as of now, because there seem to be problems with kubuntu/debian unstable:
[http://www.kde-apps.org/content/show.php?content=21832]("http://www.kde-apps.org/content/show.php?content=21832")
(look at the last comment as of today).

Can someone from Ubuntu take a look at that app? This seems to be exactly what we need!

Cheers,
Stephan

---

### Post by aseem_mal on 2006-02-03
About Wifi-Radar: Its the only utility that actually helped me use WEP on my Ubuntu setup.( I couldn't figure out WPA. Tried, Tried and Gave up.)

However, every time I re-start my computer, I don't get a wireless connection. I have to go into Wifi-Radar, click the Connect button, and then I go online.:-k 

Is there a way to make Wifi-radar connect automatically to my SSID when the computer starts? Or is this a bug in Wifi-radar?:confused: 

- Aseem

---

