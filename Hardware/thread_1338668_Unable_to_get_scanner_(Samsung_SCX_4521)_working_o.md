---
title: "Unable to get scanner (Samsung SCX 4521) working on Ubuntu 9.10"
date: 2009-11-26
forum: Hardware
---

### Post by testmiss123 on 2009-11-26
Having had managed to install the Samsung SCX-4521F printer, I tried installing the scanner.  But no luck.

Here are the steps I followed from the link [http://www.elijahlofgren.com/hardware/#scx-4521f:](http://www.elijahlofgren.com/hardware/#scx-4521f:)

In the instructions below, I am unable to find the 45-libsane.rules file (so I manually created one and try to test it without success) and I do not have a group called "scanner" in my installation.  Can someone help?

[LIST=1]
[*] Add 2 lines like this to the end of /etc/udev/rules.d/45-libsane.rules before the **LABEL="libsane_rules_end"** line 

# Samsung|SCX-4521F
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="3419", MODE="664", GROUP="scanner"
[*] Restart udev:sudo /etc/init.d/udev restart
[*] Create a symlink that is required to for Xsane to be able to see the scanner:
 sudo mkdir /dev/usb 
sudo ln -sfn /dev/usblp0  /dev/usb/lp0
[*]Now to keep from having to type the above commands after every reboot,
[LIST=1]
[*]Create the file **/etc/init.d/samsung.sh** with the content: #!/bin/bash
mkdir -p /dev/usb
ln -sfn /dev/usblp0  /dev/usb/lp0
[*]Make it executable with the command: sudo chmod 775 /etc/init.d/samsung.sh
[*]Make it be run on every boot: sudo update-rc.d samsung.sh default
[/LIST]
 
[/LIST]

---

