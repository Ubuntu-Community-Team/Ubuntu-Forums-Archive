---
title: "Install Canon Pixma IP2700 printer"
date: 2011-02-05
forum: Hardware
---

### Post by arashiko28 on 2011-02-05
Hello. I just bought a Canon Pixma IP2700 printer and can't get it to print from Ubuntu.

> Bus 002 Device 003: ID 04a9:10d3 Canon, Inc. 


As you can see it is recognized from lsusb.
When installing, I din't get the 2700 series on the predetermined list of printers but still installed 2000 series just in case it's included, seems it's not the case.

I thought that there was some factory problems, but I plugged it to a windows computer and worked in matter of seconds.

I've been searching for the drivers but haven't succeeded and the CD only has windows drivers.
Please help!

---

### Post by adrien214 on 2011-02-15
Hi Arashiko, 

It seems you are not using the proper drivers.

Plug your printer in the USB port, and then turn it on, make sure it is available by checking again with lsusb.

Go to [Canon]("http://software.canon-europe.com/software/0038679.asp")

Download the file to your computer, e.g. to your home directory. Unpack the archive by right-clicking and selecting "unpack here".

A folder is created with several subarchives, select the one which name finishes in "-deb" and extract it again to your home directory (not in the directory which the original archive created. Using the terminal, switch to this directory:

```
cd cnijfilter-ip2700series-3.30-1-i386-deb
```

and then type

```
sudo ./install.sh
```

The terminal will output several lines before prompting you to plug your printer in. If you did it already (as said above), simply hit enter. Then follow the instructions. You printer will be setup in 1 min.

Note that I tried to print a gimp file 1 min ago, the printer made several noises for at least 40sec until it managed to find the single paper sheet I fed it. But it worked =D

Note: I just realize now this thread is shown as [SOLVED], but really, how can a problem be solved without an answer being suggested ?

---

### Post by salvador0687 on 2011-09-20
Help please i am brand new here in ubuntu 11.4 ive been able to print connecting the printer directly to the usb port in the pc but if i try to look for in so i can connect in in a network i am not able to find the drivers so it does not print eventhough it can print when connected to the usb oirt can someone help me please. i am going to printing anf when adding the network trhough windows printing via samba and it does not show me the model of my printer, please help

---

### Post by Corvair on 2012-03-22
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.30-1_i386.deb
dpkg: error processing ./packages/cnijfilter-common_3.30-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 ./packages/cnijfilter-common_3.30-1_i386.deb
claude@claude-desktop:~/cnijfilter-ip2700series-3.30-1-i386-deb$ 

I have tried to install the driver and here is what I get.

I have Ubunto 10.04 with amd64. Why does it not match my system?

---

### Post by Corvair on 2012-03-22
I had to reinstall ubuntu 10.04 because my hard disk got corrupted. Before that my printer was working fine. Now I send in a print order which seems to go to the printer and disappears as if it was printed but nothing happens in the printer.

---

### Post by Corvair on 2012-03-22
My problem is solved. I had the same problem when I first installed tje printer, finely remembered. Look at the address below,

Thank you.


[http://ubuntuforums.org/showthread.php?t=1736064&page=2](http://ubuntuforums.org/showthread.php?t=1736064&page=2)

---

