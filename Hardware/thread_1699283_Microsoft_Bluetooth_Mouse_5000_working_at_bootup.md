---
title: "Microsoft Bluetooth Mouse 5000 working at bootup"
date: 2011-03-03
forum: Hardware
---

### Post by Handssolow on 2011-03-03
Good news here, at the login screen I've got my Microsoft Bluetooth Mouse 5000 ver1.0 working on my Toshiba M35X-S114 laptop with a NEXT Bluetooth dongle.

Like others I could get a working Bluetooth mouse using the Bluetooth applet but on reboot the mouse would have stopped connecting. I'd then have to remove and re-add the mouse to get it working again.

After several hours of experimenting, I was surprised to find that all I needed was to uncomment the channel line in /etc/bluetooth/rfcomm.conf and change from channel 1 to channel 2. I did also uncomment the comment line and add a description of the mouse device. All this seems to have done is to make the description appear in bold in the applet. I did install the bluetooth package but I don't think this is relevant.

here is my etc/bluetooth/rfcomm.conf file

#
# RFCOMM configuration file.
#
#rfcomm0 {
#	# Automatically bind the device at startup
#bind yes;
#
#	# Bluetooth address of the device
#device 00:1D:D8:93:98:BD;
#
#	# RFCOMM channel for the connection
channel 2;
#
#	# Description of the connection
comment "Microsoft Netbook Bluetooth Mouse 5000 ver1";
#}

Edit: I've rebooted the laptop several times and each time it's automatically connected. However, I temporarily altered the boot line in Grub whilst working on a graphics issue and the mouse went to sleep. On reboot I had to press the connect button under the mouse and also connect in the applet window. I didn't though need to remove and re-add the mouse.

2nd Edit: It paired successfully again this morning. Just an aside; my rfcomm.conf file happens to show my mouse's MAC and bind yes but are commented out. These just happened to be have been left there after my earlier experiments.

3rd Edit: After login if no immediate pairing, a small movement on the track pad with one finger whilst also moving the mouse with the other hand is often enough. I also do this when using my XP Netbook.

---

