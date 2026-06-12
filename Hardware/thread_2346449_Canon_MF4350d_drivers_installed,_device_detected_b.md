---
title: "Canon MF4350d drivers installed, device detected but no printing [16.04LTS]"
date: 2016-12-14
forum: Hardware
---

### Post by verdigris2 on 2016-12-14
Hello everyone,

I am running Ubuntu 16.04LTS on a 64bit machine.
Upon plugging in the printer (via USB), the device was detected and I believe a driver was automatically installed (UFRII-LT). 

Printing from Libre Office yields no response from the printer.
Printing a test page from the "Printer Properties" window also yields no response. The Printer State goes briefly from "processing" to:
```
idle-src=libcanon_pdlwrapper.c, line=514, err=0[COLOR=#6A6A6A][FONT=arial]**¥nDEBUG: Wrote 1 pages...**[/FONT][/COLOR]
```

I later installed the official drivers from the [Canon website]("https://www.usa.canon.com/internet/portal/us/home/support/details/printers/support-laser-printers-imageclass/imageclass-mf4350d"), for 64bit Linux with no change in result.

As a side note, this device works fine as a scanner. I didn't have to download any additional drivers. 

Any ideas on how to solve this, or if there are any other commands I can run to see if there are other error messages?

Thank you!

---

### Post by sviswana on 2017-06-13
I have the same issue. Did you get this to work? If so, can you please let me know the steps?  Thanks in advance

---

### Post by pdc on 2017-06-13
Hi sviswana; welcome to the forums;

so you need Canon's UFR driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html) and it is at version 3.31 as it was updated on 14th April (this year): it has an [COLOR="#0000FF"]Install Script[/COLOR] that should do all the work for you

so if you click to DOWNLOAD and select to SAVE it and it should end up in your Downloads directory; you will be downloading [COLOR="#0000FF"]linux-UFRII-drv-v331-uken.tar.gz[/COLOR]

if you can open a terminal; .......... hold down the control and alt and t buttons together ................and we will need you to paste commands into the terminal ....... if you right-click on the text prompt in the terminal; and you can select PASTE from the menu that appears ... oh, and hit the ENTER key after each paste ....... make sure you **COPY** the commands below ...

so the commands are 
```
cd Downloads
```
```
tar -zxvf linux-UFRII-drv-v331-uken.tar.gz
```
```
cd linux-UFRII-drv-v331-uken
```

If you now make the terminal "Full-screen" by clicking on the middle of the three buttons top-right; and it will ask you some questions; now launch the install script with 
```
./install.sh
```

...... any joy?

---

