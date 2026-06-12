---
title: "Xorg-problem with vesa/savage-driver"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by nielsk on 2008-02-21
Hi!
I'm using a Libretto L1 with a S3 Savage/IX (the resoultion is 1280x600) and everything worked more or less fine until I upgraded to 7.10.

Xorg makes me some problems. With XFree I got 1280x600 to work with the savage-driver, since the switch to Xorg I had to switch to the vesa-driver for getting full resolution (otherwise it's only 800x600). After the update to 7.10 Xfree won't start up when using the vesa-driver. I get only a blank screen and a white non-blinking cursor in the upper left corner. Changing to a TTY via alt+ctrl+f? is not possible. Only a hard power down will do anything. Switching to savage gets Xorg to work but only with 800x600 (and I think I tried everything - incl. Option "UseBios" "True" and different configurations for the modelines (5 or so are findable in the net).

I attached the Xorg.0.logs for the different drivers and the xorg.conf (sorry, the latter one is a little messy…a lot of try'n'error-stuff…a grown conf-file ;) ). 
I differentiated between the log-file for loading savagefb, vesa and savage (the file-name says all)

---

