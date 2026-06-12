---
title: "Jaunty, MS Bluetooth Intellimouse Explorer"
date: 2009-04-29
forum: Hardware
---

### Post by funfrank on 2009-04-29
I cleanly installed Jaunty the other day on my Toshiba A105 Satellite and it looks great.  The fonts are fantastic, for one.  I'm at a standstill with my MS Bluetooth Intellimouse Explorer.  When I plug in the usb dongle, the bluetooth gnome applet appears.  I click to setup new device, but no device appears in the device search.  Now how can the bluetooth applet start, but no device appears?  

hciconfig returns the folllowing:

hci0:	Type: USB
	BD Address: 00:50:F2:E2:26:1C ACL MTU: 192:8 SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:1120 acl:0 sco:0 events:48 errors:0
	TX bytes:463 acl:0 sco:0 commands:47 errors:0

Armed with my mouse's BD Address, I wanted to edit two files:

etc/bluetooth/hcid.conf
etc/default/bluetooth   

with a little code from some older threads:

HIDD_ENABLED=1
HIDD_OPTIONS="--master --connect 00:50:F2:E2:26:1C --server"

However, the hci daemon doesn't seem to exist in Jaunty.  The etc/bluetooth directory contains only the following files:

audio.conf  input.conf  main.conf  network.conf  rfcomm.conf

Perhaps I'm barking up the wrong tree anyway.  Because I still do not understand why the bluetooth applet would load upon plugging in my dongle, but still not display the device.  Even more perplexing, the BD Address shows up in hciconfig.  Any advice?

Frank

---

### Post by funfrank on 2009-05-06
There are 51 views of this thread as of 6 May 2009.  Anybody else care to describe their problem? 

I've troubleshooted using the Jaunty live CD.  Still, the mouse is nowhere to be seen in the gnome bluetooth applet.  

Frank

---

### Post by funfrank on 2009-05-17
ok - mouse was defective.  consider this thread solved.

---

