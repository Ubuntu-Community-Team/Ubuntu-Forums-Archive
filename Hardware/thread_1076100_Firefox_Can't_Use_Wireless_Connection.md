---
title: "Firefox Can't Use Wireless Connection"
date: 2009-02-21
forum: Hardware
---

### Post by ufarmer on 2009-02-21
I just installed Ubuntu 8.10 on my laptop and, while it is able to establish a connection to my wireless router, Firefox is unable to connect to any websites.  However, if I plug the laptop into the modem directly using an ethernet cable, Firefox has no problems.  Does Firefox have to be configured to look for a wireless connection instead of the ethernet connection?  Or do I need to set a default connection in Ubuntu?

Thanks.

---

### Post by sgosnell on 2009-02-21
Are you sure the wireless router has an internet connection?  Are you sure the laptop is properly connected to the router?  Firefox shouldn't need any configuration, nor should Ubuntu, as long as it's actually connecting to the router wirelessly.  Have you tried an ethernet connection to the router?  If so, does that work?

---

### Post by WaffleCode on 2009-02-21
I wouldn't think that Firefox really cares what type of connection you have (though I *could* be wrong).

Try opening a terminal (Applications -> Accessories -> Terminal) and typing
*ping google.com*

If it doesn't start printing out lines of text, you are probably not connected.

In that case, go to System -> Hardware Drivers and tell us what it says.

---

### Post by ufarmer on 2009-02-21
Here's my complete set up.  I have a desktop computer running a dual boot of Debian 4.0 and Windoze XP, and a laptop running Ubuntu 8.10.  My desktop is plugged into the router directly through an ethernet cable and I am trying to connect to the router wirelessly using the laptop.

The router connection to the desktop works fine in Windoze but it gets lost every time I boot into Debian.  No matter what operating system I am using on the desktop computer the router shows a green internet light indicating a connection to the internet and the laptop shows a Gnome desktop icon claiming that I am connected wirelessly.  However, the laptop is unable to connect to any websites no matter which OS the desktop is running.  So even in Windoze, when the internet connection is definitely functioning for the desktop and the internet light is green on the router, the laptop is unable to connect.  In all cases "ping google.ca" returns "ping: unknown host google.ca".

Clearly Debian has a problem seeing the router -- and if anyone knows the answer to that I'd be glad to hear it!  But the problem with the laptop seems to be the laptop's fault.

Any advice is appreciated.

---

### Post by sgosnell on 2009-02-22
What wireless card does your laptop have?  Ubuntu 8.10 has a problem with Atheros cards, because the driver was removed from the kernel.  If you have an Atheros card, try this:

```

sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid-generic
sudo modprobe ath5k

```You may also need to blacklist ath_pci and ath_hal in /etc/modprobe.d/blacklist.

If none of this works, try reading [this page](https://help.ubuntu.com/community/EeePC/Fixes).  It's for the Asus EEE, but many netbooks seem to have the same problem, as well as other laptops.  One of the suggestions might help.

---

### Post by ufarmer on 2009-02-22
The card is supposed to be an Intel WiFi Link 5100 WLAN controller -- and kernel 2.6.27 is supposed to have the driver for it.  How can I confirm the card and the driver?

---

