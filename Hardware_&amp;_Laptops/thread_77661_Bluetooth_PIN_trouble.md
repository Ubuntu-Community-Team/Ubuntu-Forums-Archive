---
title: "Bluetooth PIN trouble"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by Hinko on 2005-10-17
I can't get my bluetooth connection up and running. Or actually: Everything goes well accept for the damn thing not accepting my PIN :-( I just want to use multisync, and it finds my Ericsson perfectly.

I tried a lot of things allready, including changing /etc/bluetooth/pin to the desired number (it's 1234 by default, but that didn't work either) or using bluepin instead of bluez-pin. but with no succes. Anyone?

---

### Post by devnulljp on 2005-10-31
Try this for the PIN (worked with my Treo)

[INDENT]sudo vi /etc/bluetooth/pin[/INDENT]

insert the following replacing 1234 with your  PIN.

[INDENT]#!/bin/sh
echo "PIN:1234"
[/INDENT]

Make the file executable: 

[INDENT]sudo chmod +x /etc/bluetooth/pin[/INDENT]

---

### Post by frisket on 2007-09-12
> **devnulljp said:**
> Try this for the PIN (worked with my Treo)

[INDENT]sudo vi /etc/bluetooth/pin[/INDENT]

insert the following replacing 1234 with your  PIN.

[INDENT]#!/bin/sh
echo "PIN:1234"
[/INDENT]

Make the file executable: 

[INDENT]sudo chmod +x /etc/bluetooth/pin[/INDENT]

Done that, but when I type sudo hidd --connect {my phone's address} as suggested on the Ubuntu Bluetoothsetup page) the phone lights up and asks for a PIN, but when I type it in (the one I put in /etc/bluetooth/pin) it doesn't accept it.

Going the other way (trying to initiate from the phone), I give a PIN on the phone when it asks, but I never get any pop-up on the PC asking for it -- it just fails immediately (and I do have bluez-passkey-gnome installed -- what is supposed to trigger this?)

The phone is a SE Z520i

---

### Post by kusumoto on 2008-04-07
*having the exact same problem, but with a different phone*

---

### Post by onfyreforjesus on 2008-05-27
same problem on hardy. ,y phone is a SE w810i

---

