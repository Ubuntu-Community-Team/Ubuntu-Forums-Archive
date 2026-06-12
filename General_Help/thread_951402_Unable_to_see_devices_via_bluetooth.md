---
title: "Unable to see devices via bluetooth"
date: 2008-10-18
forum: General Help
---

### Post by shehaal on 2008-10-18
Hi there,

I'm running Hardy. I've just purchased a bluetooth USB tongle, however when I plug it in, nothing happens. I have to run bluetooth-applet from a terminal window in order to get that running and displaying in the notification area of the desktop panel (even though in the applet preferences, it is set to display all the time).

I've searched around a bit; there seems to be a number of references to ensuring a particular option is checked under the devices tab in the preferences - however I don't even have this tab (I only have "services" and "general").

When I right click on the applet, the option to browse a device is greyed out. There's nothing listed in the services tab. If I try and pair the computer from my phone, it can't find anything.

Any ideas on how to get these two devices to play nicely with each other, or at least see each other so they can be paired?

Thanks,
Stuart.

---

### Post by Kevbert on 2008-10-18
Welcome to Ubuntu.
What's the bluetooth device make and model ?
First thing to check is go to System-Preferences-Sessions and check that Bluetooth Manager is ticked (so it starts up on boot-up). Now go to System-Preferences-Bluetooth and check that at least Input Service is ticked under Services and under General, Receive files, Authorization, Hardware and Only display when adapter present are ticked (see attached picture).
With another bluetooth device on and discoverable, try running the following in Applications-Accessories-Terminal
hcitool scan
If you have a message 'Device is not available' or nothing displayed you may have other problems.

---

### Post by shehaal on 2008-10-18
@Kevbert,

Thanks. :) I remembered about the session prefs after I posted, however I have now enabled that and rebooted. The options under the general tab for the bluetooth devices is the same as your screenshot. Result of the terminal command is:

```
Device is not available: No such device
```

Also, the applet icon isn't showing in the panel. I've tried a number of different USB ports, all to no avail.

---

### Post by Kevbert on 2008-10-18
With the bluetooth dongle connected enter the following command in Applications-Accessories-Terminal
```
lsusb
```
Is the dongle seen by this command ?
Do you have any problems with USB connections in general ?  You may get errors on boot up.  It may be worth looking at your logs with a text editor. They can be found in the /var/log directory.
Additional bluetooth programs you may need are bluez-gnome, bluez-utils, gnome-bluetooth, gnome-vfs-obexftp (just search for bluetooth using Synaptic Package Manager, if you don't already have them installed).

---

### Post by shehaal on 2008-10-18
I don't usually have problems with usb devices. It doesn't appear that the dongle is seen by that command (no change in the list between when the dongle is plugged in and when it isn't).

I already have all those programs installed. :)

When I plug the dongle in, the following entry appears in kern.log:

```
Oct 19 10:52:39 office-pc kernel: [52184.824686] usb 1-1: new full speed USB device using uhci_hcd and address 9
Oct 19 10:52:39 office-pc kernel: [52184.971514] usb 1-1: configuration #1 chosen from 1 choice
```

From syslog:

```
Oct 19 10:52:39 office-pc kernel: [52184.824686] usb 1-1: new full speed USB device using uhci_hcd and address 9
Oct 19 10:52:39 office-pc kernel: [52184.971514] usb 1-1: configuration #1 chosen from 1 choice
Oct 19 10:52:39 office-pc NetworkManager: <debug> [1224373959.259995] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c10_0_noserial'). 
Oct 19 10:52:39 office-pc NetworkManager: <debug> [1224373959.708508] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c10_0_noserial_if1'). 
Oct 19 10:52:39 office-pc NetworkManager: <debug> [1224373959.791318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c10_0_noserial_if0'). 
Oct 19 10:52:39 office-pc NetworkManager: <debug> [1224373959.852850] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c10_0_noserial_if0_bluetooth_hci_0'). 
Oct 19 10:52:39 office-pc NetworkManager: <debug> [1224373959.869590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c10_0_noserial_if2').
```

There are entries in other logs, but it's just a repeat of the above.

---

### Post by Kevbert on 2008-10-19
Strange. With the bluetooth adapter connected, do you have gnome-obex-server installed ?  If you do hit Alt-F2 and enter gnome-obex-server and you should have the bluetooth icon displayed.
If this does not work, please take a look at [COLOR="Blue"][this]("http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu")[/COLOR].

---

### Post by shehaal on 2008-10-19
You ripper - it worked! I can connect and browse my phone now, however for some reason Wammu is having trouble connecting. When I enter in the port, it says:

```
Error opening device
Device 00:17:B0:AD:CC:4A does not exist!
```

But when I run hcitool scan, it comes back saying:

```
Scanning ...
	00:17:B0:AD:CC:4A	shehaal
```

---

### Post by Kevbert on 2008-10-19
With Wammu you may need to connect the phone in a certain way. If you run the program click on Help and select Gammu phone database then you can find the connection details.  If you are able to connect to the phone, in a different way, you can add or edit the support page. If you want new features for Wammu it may be worth registering (the support guy is very good at getting back to you with a response).

---

### Post by gordonh on 2008-11-02
Hi,

I too have bluetooth problems.

I've just upgraded to intrepid and there are no obvious problems with that.

I bought a bluetooth dongle and a GSP "thing" a couple of weeks ago, but I've only now tried it out in anger.

I've managed to pair with my phone (Nokia 6500 slide), but the GPS fails to pair, with no further info.

Attempting file transfer either way from the phone succeeds so the blutooth itself is working.

Any ideas re the GPS?

It was bought from Ebay and was apparently originally bought from wayfinder, and it's been sold as a SIRFSTAR which I understand is a generic name.

---

### Post by gordonh on 2008-11-02
Hi,

I too have bluetooth problems.

I've just upgraded to intrepid and there are no obvious problems with that.

I bought a bluetooth dongle and a GSP "thing" a couple of weeks ago, but I've only now tried it out in anger.

I've managed to pair with my phone (Nokia 6500 slide), but the GPS fails to pair, with no further info.

Attempting file transfer either way from the phone succeeds so the blutooth itself is working.

Any ideas re the GPS?

It was bought from Ebay and was apparently originally bought from wayfinder, and it's been sold as a SIRFSTAR which I understand is a generic name.

---

### Post by gordonh on 2008-11-09
bump

---

