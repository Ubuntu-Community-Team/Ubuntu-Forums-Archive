---
title: "Canon MX870 Network Printer/Scanner - Prints, but no scan."
date: 2012-03-13
forum: Hardware
---

### Post by kamiller42 on 2012-03-13
I have an MX870 networked. When I first installed Ubuntu, the printer and simple scan worked fine. It still prints, but I have lost scanning ability. 

When I run scanimage -T, I get the following...
[pixma] bjnp_open_tcp: Can not connect to scanner: Connection refused
scanimage: open of device pixma:MX870_000000EECC8F failed: Invalid argument

I have been through a couple of network changes, but nothing major. My guess is the printer's IP has changed since the device was installed, and it doesn't know about the change.

Where can I go to get more information about this pixma:MX870_000000EECC8F device? How can I uninstall a scanner and just start from scratch? (I did try purging sane, libsane, etc with no luck.)

---

### Post by jerrrys on 2012-03-13
I don't have one, but found this

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Canon+MX870+scanner&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Canon+MX870+scanner&sa=Search&cof=FORID:9)

---

### Post by kamiller42 on 2012-03-14
Found a lot of solutions on getting the print function to work. Nothing on the scanner.

---

