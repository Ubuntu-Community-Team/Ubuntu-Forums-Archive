---
title: "Dell Inspiron 8600 wireless weirdness"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by dbunder on 2006-03-16
First, relevant information: Dell Inspiron 8600 w/ Intel Broadcom 2200 wireless card, default Breezy kernel image (haven't had time to compile a custom one yet), latest versions of wireless card firmware installed, latest wpa-supplicant release.

I set up my wireless with WPA2 encryption according to the instructions in this thread: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

In my wifi_wpa.sh script I put "dhclient eth1" at the end so I can get an ip address on boot, but I never can.  Why?  Cause the kernel detects my wireless card set to "off".  On Dell laptops you can enable/disable wireless on the fly by pressing Fn-F2.  It thinks that I have my wireless card turned off each time I power cycle the computer.  If I have the wireless working and reboot, it detects the card, router, and gets an ip just fine.  

What I have to do to get it working:
-log into a Gnome or KDE session, open a terminal, type iwconfig
-iwconfig isn't picking up the router, so the wireless card must be off, right?
-hit Fn-F2 to turn on my card, iwconfig, it still isn't seeing it.
-hit Fn-F2 again, iwconfig, it's seeing it and has a strong signal.
-sudo dhclient eth1 - it gets an ip address and all is well.

I don't see anything in the BIOS or anywhere else to autoset wireless on "on".  When running windows on the laptop, wireless always works without a hitch between power cycles unless I explicitly turn wireless off.

Anyone else experience this?  If so, is there a fix?  It's not a deal-breaker, it's just awfully annoying.

---

### Post by Zelut on 2006-03-16
wondering a little bit about your wifi_wpa.sh script.  What is this used for that isn't found in /etc/network/interfaces?

My machine also cycles the wireless via Fn-F2, and I never have to touch that.  I simply have my info in /etc/network/interfaces & it picks things up everytime.

# my wireless entry in interfaces file.
iface wlan0 inet dhcp
wireless-essid <my_wireless>
auto wlan0

---

### Post by dbunder on 2006-03-16
I think we have completely different setups. Are you using wpasupplicant?

---

### Post by Zelut on 2006-03-16
I'm not.  I'm using ndiswrapper + driver is all.
If we are on different setups I'm not sure what to suggest.  You're positive that its been switched off on each boot?

---

### Post by dbunder on 2006-03-18
bump

someone else must have this problem.  i've done searches on the gentoo forums, google, the gentoo and debian wikis, everywhere, and can't find any info on it.  thinking it's a kernel param that's shutting it off on boot or such and i'll have to compile a custom kernel.  driving me sort of nutty.

---

### Post by dbunder on 2006-03-21
lil update.  found a site that says you can't get the wireless to switch on automatically via software on the 8600.  it has to be done manually with the keys, at least on the setup i'm using.  a few other dell models have tools that enable wireless via software.

---

### Post by Zelut on 2006-03-21
That is odd.  My machine has a key-press toggle that can enable/disable the wireless but it stays in its on/off position unless set otherwise.

I hope you can get it to work if you can use the key-press.

---

### Post by dbunder on 2006-03-21
the keypress works fine if i do it 2-3 times.  it'd just be nice if my wireless came up on every boot automatically. :)  no big though.

---

