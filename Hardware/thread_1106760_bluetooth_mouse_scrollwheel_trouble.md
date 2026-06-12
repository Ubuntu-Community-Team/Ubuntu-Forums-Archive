---
title: "bluetooth mouse scrollwheel trouble"
date: 2009-03-26
forum: Hardware
---

### Post by mike.freislich on 2009-03-26
Hi all,

I have a Microsoft Bluetooth Notebook Mouse 5000. The standard stuff is working fine e.g. button 1,2,3 (left, middle/scroll-button, right). However, the additional button on the left of the mouse and more importantly the scroll-wheel are not working.

I am on Ubuntu 8.10, so I have been trying to configure via HAL and xinput with no joy. I have found the device using xinput:

Device 'Broadcom Corp':
	Device Enabled:		1
	Middle Button Emulation:		2
	Middle Button Timeout:		50
	Wheel Emulation Inertia:		10
	Wheel Emulation:		0
	Wheel Emulation X Axis:		0, 0
	Wheel Emulation Y Axis:		4, 5
	Wheel Emulation Timeout:		200
	Wheel Emulation Button:		4
	Drag Lock Buttons:		0

I guess it's showing up as Broadcom since this is the make of the bluetooth module in my laptop (dell XPS m1330).

I have tried using xinput test <device number> with the following results:

left button click: 
- button press 1
- button release 1

right button click:
- button press 3
- button release 3

scroll-wheel click:
- button press 2
- button release 2

scroll-wheel scroll up and down:
- <nothing> (I would have expected button 4 & 5 respectively)

extra side button:
- <nothing> (I would have expected button 6 or higher)

I have tried setting wheel emulation to 1 and changing the wheel emulation button to "2". This allows me to use the wheel button to emulate scrolling, but I am still unable to use the actual scroll-wheel. This mouse works perfectly under vista (obviously). Is there something that I need to do to get the other buttons/scrollwheel to work?

thanks
Mike

---

### Post by mike.freislich on 2009-03-28
Bump.

---

### Post by mike.freislich on 2009-03-31
Bump... is there anyone out there?

---

### Post by mike.freislich on 2009-04-02
Bump... and some more information...

Recently I tried booting off the Ubuntu 8.10 x86 Live CD (USB flash). The very same mouse works perfectly, including scroll-wheel and extra "back" button. Darn...

I checked xinput and it shows the device as:
Device 'Microsoft Bluetooth Notebook Mouse 5000':
	Device Enabled:		1
	Middle Button Emulation:		2
	Middle Button Timeout:		50
	Wheel Emulation Inertia:		10
	Wheel Emulation:		0
	Wheel Emulation X Axis:		0, 0
	Wheel Emulation Y Axis:		4, 5
	Wheel Emulation Timeout:		200
	Wheel Emulation Button:		4
	Drag Lock Buttons:		0

This is what I would have expected...

I'm guessing this has to do with my bluetooth more than the mouse... In my Ubuntu install on my hard-disk, if I go to the preferences of the bluetooth applet (in the notification area) and set the icon to only be visible when a device is present, the icon disappears (even though the mouse is work; albeit without the scroll-wheel). Also, in the applet preferences on the live-cd, the dialog has 2 tabs namely "<machine-name>", and "General". In my HD-installed OS, I only have the "General" tab.

Anyone got an idea of how to get the bluetooth working and picking up my mouse properly?

-Mike

---

### Post by mike.freislich on 2009-04-03
Boy it's lonely in here. :-)

For what it's worth, I've managed to solve my problem. Yay! :guitar:

I discovered that if I uninstalled and reinstalled bluez (the bluetooth drivers) the mouse worked perfectly just after this... After a reboot, didn't work again...

After much digging through package install scripts and daemon logs I discovered that the bluetoothd wasn't starting when the system booted up. Hmmmm... starting the daemon with the following command got it working after bootup by typing the following command:

```
$ sudo /etc/init.d/bluetooth start
```

p.s... running this command without the 'sudo' prefix had me confused for a while because it echoed that the bluetooth was starting, but in actual fact according to /var/log/daemon.log it was "unable to connect to D-Bus". Gotta be run with privileges !Doh!

Next issue was to get this to run at boot time. More digging... found that init.d and rc.d etc. has changed a lot since I last delved into unix (freebsd 2.5). It seems that the bluetooth script in init.d is symlinked into the various /etc/rcN.d directores (where "N" represents the system runlevel that, when entered, will cause the script to run).
In a terminal I typed:
```

$ runlevel
N 2
$

```

this suggested that the current runlevel is 2. I had a look in rc2.d, and low and behold... no symlink to the bluetooth startup script (in /etc/init.d). There were however links in the rc(3,4,5).d folders.

I added the symlink:
```

$ sudo ln -s /etc/init.d/bluetooth /etc/rc2.d

```

Booted my system... and "Hey Presto!" I have my bluetooth mouse available from the login screen.

I'd say thanks for all the help, but... 

anyway... hope this helps someone else! :-)

---

