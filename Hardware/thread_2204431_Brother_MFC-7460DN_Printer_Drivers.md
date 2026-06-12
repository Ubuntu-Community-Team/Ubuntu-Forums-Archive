---
title: "Brother MFC-7460DN Printer Drivers"
date: 2014-02-08
forum: Hardware
---

### Post by webmanoffesto on 2014-02-08
I'm new to Ubuntu and I installed Ubuntu 13.10 64Bit. But I still can't print. That is a BIG problem for me. Before I bought the printer I checked the Brother website to make sure there were Linux drivers, so I'm surprised to get stuck here. Please help me to resolve this problem.

I've been the the Brother website and downloaded drivers. I think I installed them. I also installed drivers I found in the Ubuntu Software Center. This should be working by now.
- [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Error Message:
"Missing Driver: Printer 'Brother-MFC-7460DN' requires the '/usr/lib/cups/filter//usr/lib/cups/filter/fax-pnh-filter' program but it is not currently installed. Please install it before using this printer."


[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/BrotherPrinterMissingDriverv01.png[/IMG]

---

### Post by gifford on 2014-02-08
With the Brother printer driver install you need to install the LPR driver and the cupswrapper driver. Also, if you are to use the scanner functions the correct brscan file must be installed.
I know the process can be frustrating but if you follow the instructions on the Brother site you should not have any problems. Go to the page listing the drivers and then click on the link for your particular printer. This should take you to a page listing the rpm and deb versions of the drivers and directly underneath the box it will list install instructions. Make sure all of the pre-required procedures are complete such as [B]sudo mkdir /usr/share/cups/model.
[/B]Take your time and following all of the instructions. I know it may be frustrating but once completed you will have a rock solid installation. 
Also, I am not sure of what drivers you installed from the Ubuntu software center. The Brother site has the latest and most comprehensive listing of the appropriate drivers.
Is the printer to be a network or USB printer?

---

### Post by webmanoffesto on 2014-02-09
I'm making progress, I have CUPS wrapper installed. When I print I'm able to select the correct printer, but it prints a bunch of blank pages. 
I'm following the directions I found here [http://goo.gl/XzTJII](http://goo.gl/XzTJII)

Do you have advice how to solve this problem?

-----------------.

The promising sounding "linux-brprinter-installer" didn't solve the problem "Driver-packages cannot be found. Confirm the model name." 
[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/171f96b9-7c3f-4f62-b0a0-899fb0b405f7.png[/IMG]

---------.
[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/brothercupswrapperisinstalledv2014-02-09n01.png[/IMG]
-----------------.
[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/0cce5920-6b00-4076-b98f-eb6cde6f316f.png[/IMG]
--------------



[http://i1232.photobucket.com/albums/ff365/webmanoffesto/fax-pnh-filternotavailablev2014-02-09n01.png](http://i1232.photobucket.com/albums/ff365/webmanoffesto/fax-pnh-filternotavailablev2014-02-09n01.png)
[http://i1232.photobucket.com/albums/ff365/webmanoffesto/brothercupswrapperisinstalledv2014-02-09n01.png](http://i1232.photobucket.com/albums/ff365/webmanoffesto/brothercupswrapperisinstalledv2014-02-09n01.png)
[http://i1232.photobucket.com/albums/ff365/webmanoffesto/ModifyBrotherMFC7460DNv2014-02-09n01.png](http://i1232.photobucket.com/albums/ff365/webmanoffesto/ModifyBrotherMFC7460DNv2014-02-09n01.png)
[http://i1232.photobucket.com/albums/ff365/webmanoffesto/UsingCUPStoAddPrinterv2014-02-09n01.png](http://i1232.photobucket.com/albums/ff365/webmanoffesto/UsingCUPStoAddPrinterv2014-02-09n01.png)

This link solved my problems:
Linux-brprinter-installer
[http://goo.gl/5KBXw4](http://goo.gl/5KBXw4)

The correct "machine name" was MFC-7460DN

As per the instructions in the link above:
When you see the message "Will you specify the DeviceURI ?",
- For USB Users: Choose N(No)
- For Network Users: Choose Y(Yes) and DeviceURI.

---

### Post by gifford on 2014-02-10
Glad you got it solved. As a side note, the European site for Brother is very different than the USA site. Instructions are different as well as the layout.

---

### Post by ghedum on 2014-04-20
I have the same printer, but in my case it is connected throught the Network, not USB. The terminal asks me the following:

[FONT=courier new]0: https
1: lpd
2: socket
3: ipps
4: http
5: ipp
6: serial:/dev/ttyS0?baud=115200
7: ipp14
8: smb
9 (I): Specify IP address.
10 (A): Auto. (usb://dev/usblp0)

select the number of destination Device URI. ->[/FONT]



What do I choose?

---

