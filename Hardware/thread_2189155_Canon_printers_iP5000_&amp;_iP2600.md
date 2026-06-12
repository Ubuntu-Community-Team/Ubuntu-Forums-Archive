---
title: "Canon printers iP5000 &amp; iP2600"
date: 2013-11-20
forum: Hardware
---

### Post by billg1931 on 2013-11-20
Both of my Canon printers are not recognized, and I cannot find an appropriate driver for them.

---

### Post by heir4c on 2013-11-21
For the IP2600:

[http://www.canon-europe.com/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP2600.aspx?DLtcmuri=tcm:13-732358&page=1&type=download](http://www.canon-europe.com/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP2600.aspx?DLtcmuri=tcm:13-732358&page=1&type=download)

Install first the program gdebi
```
sudo apt-get install gdebi
```
When you than download the file, go to the Downloads folder and unpack the .tgz file (by rightclick on it). That create a folder iP2600_debian. Open it and than you will find 4 files. 2 .deb files and 2 tar.gz files.
You need the 2 .deb files. First rightclick on the file: cnijfilter-common_2.90-1_i386.deb and choose for: Open with and select there the GDebi packagesmanager.
That will install the driver. Than you do the same with the other .deb file: cnijfilter-ip2600series_2.90-1_i386.deb

When you get a red error line in gdebi (about libcupsys2) than you must look at this site for the solution:

[http://ubuntuforums.org/showthread.php?t=811811&page=3&p=9261461#post9261461](http://ubuntuforums.org/showthread.php?t=811811&page=3&p=9261461#post9261461)
For your information (If you not know this): The $ sign you see in front of some of the commands, you don't use them in the terminal. There's not a part of the command. This sign is what you see at the "prompt" in the terminal. Example: gerolf@gerolf-E35M1-M:~$
Take your time to do this!!!
I have also a IP2600 and I have to do what they say in the second link.
I made a howto in Dutch for on the Dutch Ubuntu-forum (I don't think you can read Dutch, but maybe for other people who can, I post the link): [http://forum.ubuntu-nl.org/documentatie/howto-ip-2600/](http://forum.ubuntu-nl.org/documentatie/howto-ip-2600/)

---

### Post by heir4c on 2013-11-21
For the IP5000 there is no driver. (I don't find one) 
So, search via Google for: "IP5000 linux driver" and you find many treads on that.

---

### Post by aikishugyo on 2013-11-28
The iP5000 should be supported in gutenprint, at least theoretically.
Best is version 5.2.9, which I hope is in the latest Ubuntu.

---

