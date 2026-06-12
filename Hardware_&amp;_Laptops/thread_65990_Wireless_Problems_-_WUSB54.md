---
title: "Wireless Problems - WUSB54"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by thoms on 2005-09-15
I just acquired a Linksys WUSB54 wireless network adapter. installed the ndiswrapper debs on my machine, set up the network setting and ta da! it actually worked.

I dist-upgraded and roughly 20 minutes afterwards my connection just cut out. Now, there's no wireless adapter in the network config, when I load ndisgtk with the adapter plugged in, it just freezes and when I load it without the adapter in, the program works but I get the message "modprobe config already contains alias directive" in the terminal. I've tried rebooting, reinstalling the ndiswrapper packages and am fresh out of ideas. Help!

---

### Post by numberexhaust on 2005-09-15
[QUOTE=thoms]I just acquired a Linksys WUSB54 wireless network adapter. installed the ndiswrapper debs on my machine, set up the network setting and ta da! it actually worked.

I dist-upgraded and roughly 20 minutes afterwards my connection just cut out. Now, there's no wireless adapter in the network config, when I load ndisgtk with the adapter plugged in, it just freezes and when I load it without the adapter in, the program works but I get the message "modprobe config already contains alias directive" in the terminal. I've tried rebooting, reinstalling the ndiswrapper packages and am fresh out of ideas. Help![/QUOTE]
 did u dist-upgrade to breezy?  i think breezy badger has the madwifi drivers preinstalled, so your ndiswrapper might be clashing with it.  that's my best guess.

---

### Post by thoms on 2005-09-16
Good idea, but I specifically didn't upgrade to breezy yet in case something like that happened.

---

### Post by numberexhaust on 2005-09-16
[QUOTE=thoms]Good idea, but I specifically didn't upgrade to breezy yet in case something like that happened.[/QUOTE]
 and ndiswrapper -l and lspci show the card and driver to be there?

---

### Post by thoms on 2005-09-16
ndiswrapper -l shows the driver to be there when the device isnt plugged in. At the moment though, it just freezes without displaying anything when the device is in.

Not sure if its of any use, but I tried deleting the ndiswrapper.ko module and the ndiswrapper -l command worked fine again, showing everything to be present.

---

### Post by thoms on 2005-09-17
[QUOTE=numberexhaust]did u dist-upgrade to breezy?  i think breezy badger has the madwifi drivers preinstalled, so your ndiswrapper might be clashing with it.  that's my best guess.[/QUOTE]

If I were to upgrade to breezy, I can't see anything on the madwifi page about support for my (or any) usb device. Could I still use ndiswrapper?

---

### Post by numberexhaust on 2005-09-17
[QUOTE=thoms]If I were to upgrade to breezy, I can't see anything on the madwifi page about support for my (or any) usb device. Could I still use ndiswrapper?[/QUOTE]
 my experience with breezy is pretty limited, you might want to ask someone more experience about that.

---

