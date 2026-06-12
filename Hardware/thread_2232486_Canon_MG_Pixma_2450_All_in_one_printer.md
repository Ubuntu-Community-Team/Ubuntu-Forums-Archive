---
title: "Canon MG Pixma 2450 All in one printer"
date: 2014-07-02
forum: Hardware
---

### Post by jim62 on 2014-07-02
I have tried to Google it but all the suggestions I have tired, seem to have failed, as nothing still prints.I have installed different drivers, [http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg2420#DriversAndSoftware](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg2420#DriversAndSoftware)
and I have done stuff in the terminal I have no idea was.

I have tried to install it via plug and play in the printer section of the system, without any luck. I run Linux Mint.

Some links and sites I have tried:

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG2450.aspx](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG2450.aspx)

[http://www.upubuntu.com/2011/12/how-to-install-canon-pixma-mp-canon-mx.html](http://www.upubuntu.com/2011/12/how-to-install-canon-pixma-mp-canon-mx.html)

[http://ubuntuportal.com/2011/12/how-to-install-canon-printer-driver-for-linux-ubuntu.html](http://ubuntuportal.com/2011/12/how-to-install-canon-printer-driver-for-linux-ubuntu.html)

[http://linux.wikia.com/wiki/Getting_Canon_PIXMA_to_work_on_Linux](http://linux.wikia.com/wiki/Getting_Canon_PIXMA_to_work_on_Linux)

[http://forums.linuxmint.com/viewtopic.php?f=47&t=147511](http://forums.linuxmint.com/viewtopic.php?f=47&t=147511)


At this point I dont know what to do, or what I am doing wrong. The printer shows up in my settings, but it does nor print. It also appears that my laptop keeps trying to download some files after my attempt that it can not do and the system gives me the following error, even after a restart:

ERROR###ERROR###ERROR###ERROR###ERROR###ERROR###ERROR
W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Does anyone have any idea how I can fix this? I dont care about the scanning part of it, I just want it to print documents.

Thank you for any responds..

---

### Post by xc3RnbFO8P on 2014-07-02
From Canon site download **3. MG2400 series IJ Printer Driver Ver. 4.00 for Linux (debian Packagearchive)**
Make a folder in /Download/**Canon**
Extract **cnijfilter-common_4.00-1_amd??.deb** to /Download/Canon (do you have 64- or 32 bit install ?)
Then do the same with **cnijfilter-mg2400series_4.00-1_amd??.deb**
In /Download/Canon folder, double click on these package and install them, if all goes well restart the computer.

---

### Post by jim62 on 2014-07-02
Holy Crap, that actually worked!! Thank you, thank you, thank you!!! You are a genius!!

You would not happen to know how I can remove that error message that keeps popping up in my Update Manager too?

---

### Post by xc3RnbFO8P on 2014-07-02
> You would not happen to know how I can remove that error message that keeps popping up in my Update Manager too?

you have to start a new thread for that!

What about scanner, download **MG2400 series ScanGear MP Ver. 2.20 for Linux (debian Packagearchive)**
extract in Canon folder and install
then you have to find **Scangear** in your computer

---

### Post by jim62 on 2014-07-02
Will do, both working fine now, thanks again.

---

