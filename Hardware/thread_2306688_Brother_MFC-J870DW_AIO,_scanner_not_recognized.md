---
title: "Brother MFC-J870DW AIO, scanner not recognized"
date: 2015-12-17
forum: Hardware
---

### Post by Paper Pusher on 2015-12-17
I have a Brother mfc-j870DW all-in-one with printer and scanner.  I was able to get the printer function working  by running the Brother Driver Install Tool in the Command window.  The Brother site offers a scanner driver for this unit for download, but they do not seem to have an install tool for the scanner.  Can anyone help me install the scanner driver?

---

### Post by deepakdeshp on 2015-12-17
This may help

[https://sites.google.com/site/easylinuxtipsproject/17](https://sites.google.com/site/easylinuxtipsproject/17)
[http://ubuntuforums.org/showthread.php?t=2246878](http://ubuntuforums.org/showthread.php?t=2246878)

---

### Post by Paper Pusher on 2016-01-07
Thank you for the links depakdeshp.  Here is what we did a month ago, action which enabled the print function fine but does not enable the scan function.  Went to the Brother site and was able to identify the newest drivers for both printer and scanner for my MFC-J870DW.  I downloaded the following files (I am running on a Gateway Model RAV80(?) netbook, 32-bit):

mfcj870dwlpr-3.0.0-1.i386
mfcj870dwcupswrapper-3.0.0-1.i386.deb
brscan4-0.4.3-2.i386.deb
brscan-skey-0.2.4-1.i386.deb
linux-brprinter-installer-2.0.0-1.gz

Unzipped the installer and ran it in a command window.  Followed all instructions and it all appeared to complete successfully, although I do not recall seeing any indication that it was accessing the scanner drivers specifically.

Question: If we want to try this again, do we need to uninstall the printer driver before proceeding?  I am wondering if we need to try an earlier version of the scanner driver, or see if perhaps we missed an instruction while the installer was running.

I followed the second link provided by depakdeshp, which goes to an earlier Ubuntu Forum thread that introduced the nifty Brother printer install utility.  That in turn directed us to a Brother support page: [http://support.brother.com/g/s/id/linux/en/download_scn.html](http://support.brother.com/g/s/id/linux/en/download_scn.html)
We confirmed the MFC-J870DW uses the brscan4 driver, although that page listed an earlier version than the one we downloaded a month ago from the Brother Linux driver site (earlier version: brscan4-0.4.2-1.i386.deb).

Is there a chance that this earlier version might be more likely to work?  

Will appreciate any guidance you can provide.

---

### Post by gifford on 2016-01-08
Are you doing a USB or network install for the printer? My experience has been that using the command line and following the instructions on the Brother site has always been successful.

---

### Post by kurt18947 on 2016-01-09
Have you checked to see if the udev fix is in place? Here's Brother's instructions for USB connections:

[http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on)

I haven't done a USB scanner install in months so don't know if this is still necessary or not.

Network connected scanners require the following line. This is part of Brother's installer script.

```
 [HR][/HR][INDENT]*****Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2  models), brsaneconfig3 (for brscan3 models) or brsaneconfig4 (for  brscan4 models) accordingly.**[/INDENT]
[HR][/HR][INDENT]5-1. Add network scanner entry Command  :  brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx [Example]("http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on#config1")5-2. 

Confirm network scanner entry Command  :  brsaneconfig2  -q  |  grep  (name  of  your  device)[/INDENT]

```[INDENT]

[/INDENT]

---

### Post by Paper Pusher on 2016-01-14
Thank you for the guidance.  We are connected via USB; printer is not networked.  We checked to make sure we have downloaded the most recent printer and driver files from the Brother linux site, extracted the installer, and attempted to run it.  As noted in my earlier message, when we did this in early December it appeared to run successfully, unzipping the appropriate print driver files as it ran.  It queried for model number and we input that.  After that run, the printer works but scanner no.  Just now, after again checking to make sure all the appropriate files are present on the downloads folder, we tried to run  the installer again, in hopes we could direct it to install the scanner drivers,  Unfortunately, we could not even get the installer to run this time:

XXX:~/Downloads$ sudo ./linux-brprinter-installer*
Driver-packages cannot be found.
 Confirm the model name.

Any ideas to explain why we could not run  installer again? I'm thinking perhaps we need to delete all these downloaded folders/files and try again from scratch.
We'll continue to plug away...

---

### Post by kurt18947 on 2016-01-15
I run the Brother installer script slightly differently though I don't know if it matters. If the script is in downloads I cd Downloads then
"sudo bash linux-br<tab> to autocomplete. I don't know if you need to undo what you've done or if you can just reinstall. Is the udev rule addition present in lib/udev/rules.d/40-libsane.rules? A way to check might be to try scanning with sudo privileges. Perhaps something like "sudo simple-scan"(or other scanning package). If the scanner works with sudo but not as an desktop user I'd suspect something with the libsane rules.

---

### Post by Paper Pusher on 2016-05-26
Again, I want to thank those of you who posted replies to me query. I ultimately succeeded in getting both printer and scanner to work.  I did this by (a) switching to a different computer (64-bit vs. 32-bit), (b) upgrading to from Ubuntu 14.04 to 16.04 and (c) downloading all driver packages from the Brother web page for printer, scanner, and installation, and (d) following the instructions exactly as provided on the Brother Linux driver page for my printer (MFC-J870DW).  I suspect that the Ubuntu upgrade and changing to a 64-bit computer were probably key to my success.  Thank you again and I am closing this thread.

---

