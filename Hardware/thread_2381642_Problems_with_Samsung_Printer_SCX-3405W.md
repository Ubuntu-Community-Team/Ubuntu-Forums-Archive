---
title: "Problems with Samsung Printer SCX-3405W"
date: 2018-01-03
forum: Hardware
---

### Post by Raggylad on 2018-01-03
I'm running Ubuntu 16.04 and have a Samsung SCX-3405 multi function network printer (less than 4 years old).  This has worked fine until a recent OS update but now will not print.

On checking the system settings - printer, the printer status shows this error message:

[INDENT]> Stopped - File "/usr/lib/cups/filter/rastertoqpdl" not available: No such file or directory
[/INDENT]

On checking the drivers, no drivers for Samsung SCX-3400 series printers are listed in the directory.

Samsung have recently (November 2017) transferred all responsibilities for their printers to HP.  On checking the relevant product section of the HP support site, it states that no Linux drivers are available for this printer.

Where to go from here ?

Any advice or help _very_ gratefully received.

---

### Post by DuckHook on 2018-01-03
This may actually be very good news in the longer term. I've always found HP's Linux support to be the best of all the printer vendors. However, it will take quite some time for HPLIP to get all of those Samsung printers under their umbrella. And if HP decides to spin off the Samsung product as a separate division, it is possible that HPLIP will never support them. In the meantime, I'm sure you can still download Samsung's drivers from their site. My searching shows: [https://www.samsung.com/us/support/supportOwnersProduct.do?prd_ia_cd=N0000191&prd_mdl_cd=SCX-3405W%2FXAC&prd_mdl_name=SCX-3405W#content3](https://www.samsung.com/us/support/supportOwnersProduct.do?prd_ia_cd=N0000191&prd_mdl_cd=SCX-3405W%2FXAC&prd_mdl_name=SCX-3405W#content3)

There's only one Linux driver on that page. Have you tried installing this?

You can also try booting with an older kernel. This might help pin down whether the problem is in a newer kernel or whether it was more general with the update.

---

### Post by Raggylad on 2018-01-03
Thank you for that.  All the Samsung pages I found just referred me to HP !  I'll try installing that and see how I get on.

---

### Post by Raggylad on 2018-01-04
I'm having difficulty getting my Samsung SCX-3400 series printer to work after a recent OS update to 16.04 - see over on the hardware forum.

I've managed to find a generic Linux printer driver from a Samsung site and have downloaded it.  This leaves me with a folder called:

> [INDENT]uld_v1.00.36_00.91.tar.gz
[/INDENT]


which is currently sitting in the 'Downloads' folder.  

I have tried extracting it and running the command lines in Terminal suggested elsewhere in the forums in order to install the driver - but with no success at all.  I'm obviously doing something wrong, but have no idea what !  I can type lines into Terminal but readily admit that I have no understanding of what they mean - merely their outcome.  I'm no coder !

Looking for any help and advice, please, on what I need to do to get the driver from that folder extracted and installed.

Thank you !

---

### Post by Holger_Gehrke on 2018-01-04
'uld_v1.00.36_00.91.tar.gz' is not a folder but a (gnu-zipped) tar-archive. Open a terminal and enter this (You can copy and paste this; pasting into the terminal is ctrl-shift-v in most terminal-emulators, not ctrl-v as in most other programs. If this doesn't work, look for a paste-option in the edit-menu of your terminal.);
```

cd ~/Downloads
tar -xzf uld_v1.00.36_00.91.tar.gz

```
This will unpack the archive and there will be a new directory named 'uld'. Change to that directory and call the installer-script by entering
```

cd uld
./install.sh

```
If this gives any errors, post them here. (Copying in the terminal is also different from normal. Most terminal-emulators use ctrl-shift-c; if this does not work look for a copy-option in the Edit-menu of your terminal)

Holger

---

### Post by slickymaster on 2018-01-04
Merged [https://ubuntuforums.org/showthread.php?t=2381642](https://ubuntuforums.org/showthread.php?t=2381642) with this one.

---

### Post by Raggylad on 2018-01-04
Holger,
Thank you for that. The package has now installed.

All,
However, I am still getting the same error message as in the Op - even after re-starting.  Any thoughts ?

---

### Post by DuckHook on 2018-01-04
> **Raggylad said:**
> …However, I am still getting the same error message as in the Op - even after re-starting.  Any thoughts ?

> **DuckHook said:**
> …You can also try booting with an older kernel. This might help pin down whether the problem is in a newer kernel or whether it was more general with the update.
&#8593;

---

### Post by pdc on 2018-01-05
this group have long suggested that their iteration of the Samsung driver is better [http://www.bchemnet.com/suldr/index.html](http://www.bchemnet.com/suldr/index.html)

---

### Post by Raggylad on 2018-01-16
> **DuckHook said:**
> &#8593;

I have now tried with kernels 4.4.0-104 and 4.4.0-103.

No printer connection and same error messages as before.

---

### Post by Holger_Gehrke on 2018-01-17
The program '/usr/lib/cups/filter/rastertoqpdl' is part of the package 'printer-driver-splix', which according to the description in synaptic is a printer driver for Samsung and Xerox laser printers. On my system (Xubuntu 17.04) it was installed as part of the base installation.
You might want to check if this package is installed on your system and install it if it isn't.

Holger

---

### Post by haos-engine on 2018-09-02
[COLOR=#2A2E2E][FONT=&amp]For my Samsung SCX-3405W I was having troubles installing this driver.Even with latest drivers **uld_V1.00.39_01.17** ([https://ftp.hp.com/pub/softlib/software13/printers/SS/SL-M4580FX/uld_V1.00.39_01.17.tar.gz](https://ftp.hp.com/pub/softlib/software13/printers/SS/SL-M4580FX/uld_V1.00.39_01.17.tar.gz)) I was having problems; always receiving:
```
Unable to open raster stream - : Broken pipeOnly
```
after I turned to [http://splix.sourceforge.net/](http://splix.sourceforge.net/) or [https://sourceforge.net/projects/splix/](https://sourceforge.net/projects/splix/) and used it's rastertoqpdl it was working.Here's my **PPD** file: [https://gist.github.com/ChaosEngine/65532a1bb837e5adaa067af7670ff2c2](https://gist.github.com/ChaosEngine/65532a1bb837e5adaa067af7670ff2c2)[/FONT][/COLOR]

---

