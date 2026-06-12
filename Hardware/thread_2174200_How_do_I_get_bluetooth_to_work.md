---
title: "How do I get bluetooth to work?"
date: 2013-09-13
forum: Hardware
---

### Post by Rachel_Bunker on 2013-09-13
I'm can't get bluetooth to work on my laptop and it's driving me nuts.  The laptop is an older model, about 3-4 years old so that might be the issue but I'm hoping not.  Anyway, the laptop is a HP Pavilion DV7T-2200 if that makes a difference.  I'm currently running Ubuntu 13.04 64 bit as my only OS.  Now, back to bluetooth; as I said, bluetooth doesn't work.

When I try rfkill list all I get
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

However, when I try dmesg | grep Blue I get
[   17.191726] Bluetooth: Core ver 2.16
[   17.191756] Bluetooth: HCI device and connection manager initialized
[   17.192022] Bluetooth: HCI socket layer initialized
[   17.192226] Bluetooth: L2CAP socket layer initialized
[   17.192236] Bluetooth: SCO socket layer initialized
[   17.212460] Bluetooth: RFCOMM TTY layer initialized
[   17.212485] Bluetooth: RFCOMM socket layer initialized
[   17.212487] Bluetooth: RFCOMM ver 1.11
[   17.378944] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.378949] Bluetooth: BNEP filters: protocol multicast
[   17.378962] Bluetooth: BNEP socket layer initialized

I am now at a loss as to what to do.

---

### Post by Kirboosy on 2013-09-13
Let me be the first to say. Welcome to the forums! :D


You might be missing required packages in order to manage the bluetooth hardware
[URL="https://help.ubuntu.com/community/BluetoothSetup"]
Bluetooth Setup -- Ubuntu[/URL]


I also found this...

>   I figured it out myself, something was not installed by default for bluetooth.
  So, i went and installed again Synaptic and installed the following packages:
   sudo apt-get install \
  bluetooth blueman \
  bluez-hcidump bluewho python-bluez  bluez-tools \
  brcm-patchram-plus-nexus7
  One of this fix my bluetooth problem, now it works just fine both  ways(PC-Phone,Phone-PC) I forgot to mention that the problem occur  immediatly after fresh install of Ubuntu 13.04.
  Stupid of me i didn't test the bluetooth before clean install, but now it's all good.

 
[u Wiki]("https://help.ubuntu.com/community/BluetoothSetup")

[Link to the page]("http://askubuntu.com/questions/286834/bluetooth-not-working-in-ubuntu-13-04")


Hope that helps!
~Caboose

---

### Post by Rachel_Bunker on 2013-09-13
Thank you for the welcome!  I am currently in a doctor's waiting room but I will definitely try that when I get home.

---

### Post by Rachel_Bunker on 2013-09-13
I tried that but no luck. :(

---

### Post by Kirboosy on 2013-09-13
This may seem like a silly question but are you sure the chip is actually turned on?

---

### Post by Rachel_Bunker on 2013-09-13
No, I'm not sure.  How do I find out?

---

### Post by Rachel_Bunker on 2013-09-13
I tried to find out the bluetooth status in the terminal by doing: sudo service bluetooth status

I got: bluetooth start/running, process 923

What is process 923?

---

### Post by Kirboosy on 2013-09-16
The chip could be turned off from the BIOS. If you shutdown your computer and enter into the BIOS there might be an option to enable your bluetooth.

---

