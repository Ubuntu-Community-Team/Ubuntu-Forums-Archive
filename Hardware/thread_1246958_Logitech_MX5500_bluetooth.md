---
title: "Logitech MX5500 bluetooth"
date: 2009-08-22
forum: Hardware
---

### Post by miesnerd on 2009-08-22
So my keyboard arrived this morning. Plugged in bluetooth reciever; keyboard, mouse, etc.

Mouse is still charging, so I'm leaving it alone for now.
Keyboard worked right off the bat.
I installed HIDPoint, and restarted the computer. I wanted to get the other keys to work.

Now, the bluetooth keyboard doesnt work.

Here's the kicker though-
After doing some searching, Ive found that even though my adapter registers as plugged in (via lsusb) it doesnt seem to work beyond that. How intriguing, considering it (and the connection, and the keyboard) worked the first time it was just plugged in.
Even more intriguing, was that doing commands Ive found such as hcitool scan and sudo hidd --search yield responses such as "no such device" and for hid: sudo: hidd: command not found.

In sum,
WTF?

---

### Post by miesnerd on 2009-08-22
UPDATE:
HIDPOINT IS AT FAULT HERE.
Just uninstalling their software makes all the ubuntu- default software work.
Now dont get me wrong, I'm sure I'll have to follow the guides to get the keyboard and mouse to work by default on the next startup, but its ridiculous that their software inhibited any of my earlier attempts to work.

Amazing.

PS- LOVE the Logitech MX5500!

---

### Post by miesnerd on 2009-08-22
update:
I'm an excited, dirty liar.
I checked the config, but ubuntu already had it setup perfectly, so my hw was detected automatically.
Beautiful!

---

### Post by JMCB on 2010-08-19
Alright, I signed up for this forum because of this. Sorry to necro. I am a windows PC user. I have never ventured into the world of Linux and I thought now might be the time to try it out. I just installed Ubuntu with the latest release, and neither my mouse nor my keyboard work. They are connected via a bluetooth dongle, but it loses connection and I cannot get it to work.

Going into Linux, I knew that I was going to need to put in some work to do things I could easily do on Windows, but this is just ridiculous. I'd appreciate any input.

Thanks!

---

### Post by pricetech on 2010-08-20
No help, just a question;  What brand / model is the dongle ??  I want to make list of dongles to avoid.

---

### Post by JMCB on 2010-08-20
It is the default dongle that comes with the MX5500 Revolution, in my case, the Logitech MX 5500 Revolution Bluetooth 2.0 EDR M/N C-UV35.

Any help on the issue would be appreciated. I'm typing this from Windows 7 BTW. ;p

---

### Post by indiana_crook on 2010-09-13
So, Im confused.  What did you do to get the mouse working.  I'm having some issues of my own.

---

### Post by checoimg on 2011-02-23
I think I have the solution do you still hace this problem??
I used the bluetooth manager. I installed many bluetooth stuff from synaptic.

here is the list of packages intalled on the "bluetooth" search
bluetooth
libgnome-bluetooth7
gnome-bluetooth
python-bluez
pulseaudio-module-bluetooth
bluez
bluez-cups
bluez-pcmcia-support
bluewho
bluemon
blueman
bluez-gstreamner
bluez-alsa
btscanner
obex-data-sever

this packages are really small so I just installed everything seeemed usefull for bluetooth. :P I think you just need the "blueman" package

so just:

"sudo apt-get install blueman"

and I will post a picture when I get it uploade.

---

### Post by checoimg on 2011-02-23
[IMG]http://i1085.photobucket.com/albums/j436/checo_evo/Screenshot.png[/IMG]

---

