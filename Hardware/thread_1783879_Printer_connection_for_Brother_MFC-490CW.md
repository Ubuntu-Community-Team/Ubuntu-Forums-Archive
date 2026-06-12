---
title: "Printer connection for Brother MFC-490CW ??"
date: 2011-06-16
forum: Hardware
---

### Post by jedson3 on 2011-06-16
I am trying to get a Brother MFC-495CW printer to work with my Ubuntu program. Have gone to the Brother support page and downloaded and run their installer. Also tried downloading and installing deb files for the cupswrapper and driver. Nothing seems to work. When I try to print, the printer says it is receiving data, but does not print. Any help will be greatly appreciated. 

jedsoning

---

### Post by walt.smith1960 on 2011-06-16
USB connection or network?  I had trouble with a networked printer installing thinking it was a USB connection.  How you check depends on which Ubuntu you're running.  10.10 and earlier it's system -> administration -> printing (I think, working from memory). Right-click the Brother icon and click "properties". Does the Device URI seem sensible?  My USB installations worked properly so I'm not sure I can be of any help there.

In 11.04 I use "super" or "windows" key then in the search box put "printing". You'll get to the same place.

---

### Post by jedson3 on 2011-06-16
I am using Ubuntu 10.04 with a USB connection. Not on a network. When I go to Administration/printer, and follow the links to the driver section, it show that I am using "Brother MFC-495CW CUPS."  I don't know  whether  that makes sense. The driver I downloaded and tried to install did not have that name. 

Jedson

---

### Post by walt.smith1960 on 2011-06-16
> **jedson3 said:**
> I am using Ubuntu 10.04 with a USB connection. Not on a network. When I go to Administration/printer, and follow the links to the driver section, it show that I am using "Brother MFC-495CW CUPS."  I don't know  whether  that makes sense. The driver I downloaded and tried to install did not have that name. 

Jedson

I have something similar on a Brother  MFD.  Here is a screen shot of my USB installation.
[ATTACH]195276[/ATTACH]  The driver is from Brother.

If that looks right I'm not sure what could be causing your difficulty.  Have you tried searching using terms like "Brother+490CW"?  If you haven't done so, you could look through this.  It looks like Brother has an installer.  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090)

---

### Post by jedson3 on 2011-06-16
Mine looks pretty much the same, except it has the printer model I use. I used the installer at the Brother site. 

/home/jedson/Desktop/Screenshot.png

jedson

---

### Post by jedson3 on 2011-06-16
Hey --
I tried running that installer again, and this time it worked. There seems to be more than one. Anyhow, all is up and running. Thanks for your help.

Jedson:p

---

### Post by walt.smith1960 on 2011-06-16
I'm glad you were able to get your machine working.  I'd not seen the installer in the FAQ section before today.

---

### Post by PakeJow on 2011-09-17
i cant get my printer to work over a network. the printers drivers installed correctly, and its reognized in the "printers" menu.
but it says "printer may not be connected" 
for the URl it says :usb:/dev/usb/lp0
but i want it to be used wirelessly, so shouldnt it say the printers IP adress that i gave to set it up?
help please:???:

---

### Post by Walk on 2012-08-06
Type this in the URl

lpd://PRINTER IP ADDRESS/binary_p1






> **PakeJow said:**
> i cant get my printer to work over a network. the printers drivers installed correctly, and its reognized in the "printers" menu.
but it says "printer may not be connected" 
for the URl it says :usb:/dev/usb/lp0
but i want it to be used wirelessly, so shouldnt it say the printers IP adress that i gave to set it up?
help please:???:

---

### Post by f1ndingwalden on 2012-08-06
I had a similar problem but with a 32 bit program, this site helped a lot. [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

---

