---
title: "hcid.conf file is empty, can't continue with adding Bluetooth headset"
date: 2008-12-15
forum: Hardware
---

### Post by nLinked on 2008-12-15
I am trying to add my Bluetooth headset using [this]("https://help.ubuntu.com/community/BluetoothHeadset") official tutorial.

One of the first steps is to go to the file with the command: sudo gedit /etc/bluetooth/hcid.conf

It opens but the file is empty. There is no text in it so I can't edit it like the tutorial suggests.

I have verified that my bluetooth adapter works. I can see my headset in the device list (although it fails at pairing because Ubuntu automatically tries to connect with the 0000 passkey, which is incorrect for this headset (should be 5555). The Bluetooth wizard doesn't ask me for my own passkey. So I have to follow that tutorial but the hcid.conf file is empty.

What can I do?

---

### Post by eee1000huser on 2009-02-23
Seems like hcid.conf is missing in Intrepid (ubuntu 8.10)... anyone had success getting it back?

---

### Post by zakarov on 2009-03-22
I've been searching for a while on this too - it seems like most solutions involve an applet in gnome. Does anyone know if there is a way to still add devices from the terminal? (Not running Ubuntu Desktop)

---

### Post by Plantface on 2010-08-04
Well did you find it?

---

