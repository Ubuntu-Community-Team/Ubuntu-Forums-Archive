---
title: "Broblems connecting a bluetooth mouse (Logitech V270)  to laptop (FSC Amilo 1520)"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by ankkau on 2007-12-16
Hello!

I am having some troubles getting a bluetooth mouse working with my new laptop.

Setup:
* Mouse: Logitech V270
* Laptop: Fujitsu Siemens Amilo 1520-23
* OS: Ubuntu v. 7.10

Problem:
* Mouse can be found with 'Bluetooth manager' and it can be set 'Trusted' but it does'n move the cursor
* I've tried to run "sudo hidd --search" in terminal but it can found only some mobile phone
* I have checked in Vista that the mouse works properly

Contents of my '/etc/default/bluetooth':
   BLUETOOTH_ENABLED=1
   HIDD_ENABLED=1
   HIDD_OPTIONS="--master --server"
   #HIDD_OPTIONS="-i --connect 00:07:61:83:ed:d7 --server" (i have tried this line)

I've written also in Ubuntu Finnish forum but it seems like I'm getting no help from there in  this issue. I hope this can be solved, anyways. :)

EDIT:
* I marked a error notification in logon: "Cannot listen to HIDD channel, already connected" or something like that.

---

### Post by steveneddy on 2007-12-16
Look[ here]("http://ubuntuforums.org/showthread.php?t=586105").

Hope it helps.

Follow the directions and read the links for a complete understanding of how this works.

You are on the right track, though.

---

### Post by ankkau on 2007-12-16
> **steveneddy said:**
> Look[ here]("http://ubuntuforums.org/showthread.php?t=586105").

Hope it helps.

Follow the directions and read the links for a complete understanding of how this works.

You are on the right track, though.


Hello! Thanks for the post!

I proceeded the steps..

* 'lsusb' gives me "Bus 003 Device 011: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)"

but

* 'sudo hidd --search' and '  hcitool scan' do not find any devices

* if I try to run ' sudo hidd --connect 00:07:61:83:ed:d7' (mouse address) I get message "Can't get device information: Host is down"

Anyways all the time "Bluetooth traveller mouse" can be seen in Bluetooth manager as a bonded device.

---

### Post by NaplesBill on 2007-12-19
I'm having pretty much the exact same problem on an Acer 5610 with a Kensington Bluetooth dongle and a Logitech V270.  I've tried all the workarounds I've found and so far nothing works.

---

### Post by tonyric on 2007-12-19
When I got errors such as those, I kept bouncing between hcitool and hciconfig (with carious options) until the mouse started working. Once it works the first time you are good to go.

---

### Post by NilsE on 2007-12-19
Make sure that the following 2 apps are installed via Synaptic

gnome-bluetooth

bluez-utils

Then keep doing the sudo hidd --search and the sudo hidd --connect 00:07:61:89:32:b9   ** with your mouse address**

While turning the mouse off and on periodically and pressing the reset button once in awhile..

I think you said it but also make sure the mouse is marked as trusted and that "visible and connectable for other devices is selected in the bluetooth preferences.

Once you get it connected then you will need to add the automatic connection line like this in the /etc/default/bluetooth file

HIDD_OPTIONS="--connect 00:07:61:89:32:b9 --server"

With you address.

---

### Post by NaplesBill on 2007-12-20
The same mouse and bluetooth dongle worked perfectly on my HP laptop at work with the same version of Ubuntu.  I'm guessing now that there is some type of issue with my Acer laptop due to the optional bluetooth module that mine does not have.   I will get my hands on the OEM bluetooth module and try again at a later date.  For now I'll use the BT mouse at work and the RF mouse at home.

---

### Post by ankkau on 2007-12-25
Thank you NilsE, I think that installing the bluetooth-gnome packet solved the problem! Mouse works perfectly. It is recognized properly if I turn it on and off during tasks. Cheers, Antero:guitar:

---

