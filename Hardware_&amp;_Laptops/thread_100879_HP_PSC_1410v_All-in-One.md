---
title: "HP PSC 1410v All-in-One"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by Doomed_Tupperware on 2005-12-08
I plugged the printer in, and everything seems to be fine, but when I try to print from OOWriter or any other program, it won't print.

---

### Post by matthew on 2005-12-08
If you haven't installed the printer (in software) you need to do that. To do so:

Open System->Administration->Printing

Click Printer->Add Printer

follow the directions as they come up

---

### Post by Doomed_Tupperware on 2005-12-08
Ah, thanks a lot, that did it.

---

### Post by matthew on 2005-12-08
Glad to hear it! If anything else comes up, feel free to ask.

---

### Post by Doomed_Tupperware on 2005-12-08
Actually, yeah, one more thing, how do I install the scanner portion of this scanner/printer?

---

### Post by matthew on 2005-12-08
For the scanner you need to edit a file. I'll walk you through it.

Open a terminal by clicking in the menu: Applications->Accessories->Terminal

Then type ```
sudo cp /etc/sane.d/dll.conf /etc/sane.d/dll.conf_backup
``` followed by ```
sudo gedit /etc/sane.d/dll.conf
``` A text editor will open this file for you. Add this at the end of the file ```
# The hpaio backend (hplip package) supports HP multifunction
# devices. It is intended as a replacement for hpoj, choose
# whichever works best for you
hpaio

``` Here's a copy of my entire /etc/sane.d/dll.conf for comparison
```
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
coolscan
coolscan2
#dc25
#dc210
#dc240
dmc
epson
fujitsu
#gphoto2
gt68xx
hp
hpsj5s
hp5400
ibm
leo
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
nec
niash
pie
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
snapscan
sp15c
#st400
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l

# The HP OfficeJet backend is not part of the SANE distribution
# but is provided by the hpoj Debian package
hpoj

# The hpaio backend (hplip package) supports HP multifunction
# devices. It is intended as a replacement for hpoj, choose
# whichever works best for you
hpaio

``` Now we need to make sure you have the scanning program installed
```
sudo apt-get install xsane xsane-common
``` This will install the scanner program for you if it isn't already installed. 

You can access it in Applications->Graphics->Xsane Image scanning program.

That should do it.

---

