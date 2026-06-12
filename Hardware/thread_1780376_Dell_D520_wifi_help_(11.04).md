---
title: "Dell D520 wifi help (11.04)"
date: 2011-06-11
forum: Hardware
---

### Post by ibookg497 on 2011-06-11
Hi everyone.

I just installed ubuntu 11.04 on my dell latitude D520 laptop with a broadcom WIFI card (it says the proprietary driver is the Broadcom STA wireless driver) and ubuntu shows that the device driver is in use.  My question is how to I use it?  My hardware WIFI light is off and I cannot use the key combination to turn it back on.  I am actually not sure how to connect to wifi... CAN SOMEONE PLEASE HELP!:(

---

### Post by superduperlinuxperson on 2011-06-11
hold on let me find the website on how i did it

---

### Post by superduperlinuxperson on 2011-06-11
got it!
If you do not have any other means of Internet access on your computer, you will have to install b43-fwcutter and patch  packages from the install media. After that you will need to setup  firmware manually (without the firmware automatically downloading and  being set up). 
**Setp 1.** 
b43-fwcutter is located on the Ubuntu install media under **../pool/main/b/b43-fwcutter/** and patch is located under **../pool/main/p/patch/** **or** both in the official repositories online.  
Double click on the package to install **or** in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) navigate to the folder containing the package and issue the following command:  

:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*
**Step 2.** 
On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
**Step 3.**  
Copy  the downloaded files to your home folder and execute the following  commands consecutively in a terminal to extract and install the  firmware: 

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

---

### Post by ibookg497 on 2011-06-11
Thanks for the help, but I have internet acces through ethernet.  How do I do it through internet?  Also, could you please be a little more specific about the instructions?  This is my first day using linux, so sorry if I sound like a noob...

---

### Post by ibookg497 on 2011-06-11
I just found b43-fwcutter on ubuntu software center... now what?

---

### Post by ibookg497 on 2011-06-11
Ok.  I just looked on windows and it showed that I have a broadcom 440x 10/100 integrated controller.  This is for ethernet.  Then it showed that I have a dell wireless 1390 WLAN Mini PCI Card.  So i do not think I even have a broadcom wifi card!

---

### Post by ibookg497 on 2011-06-11
correction, it is a Broadcom BCM4311 802.11b/g WLAN (rev 01)

---

### Post by superduperlinuxperson on 2011-06-12
congratulations!!!!!!!!!!!!! your card is supported!

this works with or without internet access
so just run those on a terminal.... and you should be good!
thanks
btw you can connect to your wifi on the top bar where the on sympol is and the battery; the one with the concave bars is the one

---

### Post by superduperlinuxperson on 2011-06-12
actually, you know what, just run this after you copied the files to your home folder
~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

---

### Post by superduperlinuxperson on 2011-06-12
also check if your hardware switch for the wifi is on(it could on the front or the side

---

### Post by ibookg497 on 2011-06-12
Ok I already downloaded fwcutter from ubuntu software center.  Do I still have to install a patch?  Where would I get that from on the software center?

---

### Post by superduperlinuxperson on 2011-06-12
no you dont need the patch

---

