---
title: "Bluetooth device on Acer Travelmate P243 not working"
date: 2012-07-11
forum: Hardware
---

### Post by wijit on 2012-07-11
Having wondered around for while to find the proper place to address the problems. Actually this was the first place I visited but I have visited Askubuntu before and hoped that there would be an answer. Askubuntu has a link to debugging process and after following the advice I guested that the problem should be categorised as a bug. I went to Launchpad but again it seemed there was a difference between Launchpad's and mine. A bug should be a mistake in a program but my problem tends to involve the device might so new that no driver (a or several parts of software) supports. That was why I came back here. After installed Precise side by side with Windows 7 Pro on Acer Travelmate P243, Bluetooth device did not work properly. I have less knowledge on programming but a bit familia with Ubuntu. I love it actually. After skimmed through lsusb, dmesg and udev log, it seemed each part of the kernel got different answers for the bluetooth. The device did work so the kernel could read. The driver also worked since when I pluged my old usb bluetooth dongle, the dropdown menu of the bluetooth applet had 6 more lines from originally 3 lines and I had a chance to transfer files between the notebook and my phone. I attached files with this post for the hope that someone might have a solution. It might not have to be a new program code. I rememberred that a year ago Pytheas22 had helped me on similar situation. My new Dell Inspiron 4030N had an Atheros xxxx, a so new model NIC that Lucid did not have its driver. Lukily me, he knowed that there was a driver for such a device in a wireless package. I was with it until Lucid's update included the driver not long ago.
Parts of dmesg is:
[   13.971047] init: failsafe main process (760) killed by TERM signal
[   14.087796] Bluetooth: Core ver 2.16
[   14.087938] NET: Registered protocol family 31
[   14.087941] Bluetooth: HCI device and connection manager initialized
[   14.087944] Bluetooth: HCI socket layer initialized
[   14.087946] Bluetooth: L2CAP socket layer initialized
[   14.087952] Bluetooth: SCO socket layer initialized
[   14.090705] Bluetooth: RFCOMM TTY layer initialized
[   14.090710] Bluetooth: RFCOMM socket layer initialized
[   14.090713] Bluetooth: RFCOMM ver 1.11
[   14.092783] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.092788] Bluetooth: BNEP filters: protocol multicast
[   14.096177] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0

Compared to parts of dmesg afer restarted with a dongle which has:
[   13.971047] init: failsafe main process (760) killed by TERM signal
[   14.087796] Bluetooth: Core ver 2.16
[   14.087938] NET: Registered protocol family 31
[   14.087941] Bluetooth: HCI device and connection manager initialized
[   14.087944] Bluetooth: HCI socket layer initialized
[   14.087946] Bluetooth: L2CAP socket layer initialized
[   14.087952] Bluetooth: SCO socket layer initialized
[   14.090705] Bluetooth: RFCOMM TTY layer initialized
[   14.090710] Bluetooth: RFCOMM socket layer initialized
[   14.090713] Bluetooth: RFCOMM ver 1.11
[   14.092783] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.092788] Bluetooth: BNEP filters: protocol multicast
[   14.096177] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
and 2 new lines at the end:
[19670.999723] Bluetooth: Generic Bluetooth USB driver ver 0.6
[19671.000287] usbcore: registered new interface driver btusb

all files are attached here:

:confused:

---

### Post by wijit on 2012-07-20
According to Acer support, this model comes with either of these Bluetooth devices:
Bluetooth_Atheros_7.4.0000.0095_W7x86W7x64_A
Bluetooth_Broadcom_6.5.1.1240_W7x86W7x64_A

---

