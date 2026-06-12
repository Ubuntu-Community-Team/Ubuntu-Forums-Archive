---
title: "Charging the iPad"
date: 2010-06-08
forum: Hardware
---

### Post by whoopn on 2010-06-08
I am trying to charge the iPad on my Dell D630 running Ubuntu 10.04.  And it wont!

Here is what I need to know how to do:
Set the USB port to deliver 1100mA or close to it.  Normally USB ports deliver 500mA of power (which is not enough).

I seem to recall threads on these forums for USB power options but I cannot remember where the thread is or where those settings are in Ubuntu.

Could someone help me with this please?  Asus, MSI, and Gigabyte released drivers for this last week and its claimed on the following website that you can use the Asus drivers on any windows computer, so naturally I wanted this to work in linux :).  You can get them here: [http://dailyiphoneblog.com/2010/06/01/charge-the-ipad-from-any-computer-using-the-asus-ai-charger-software/](http://dailyiphoneblog.com/2010/06/01/charge-the-ipad-from-any-computer-using-the-asus-ai-charger-software/)

Any ideas would be great!  Thanks!    :popcorn:

---

### Post by Olostan on 2010-11-26
I've tried to use 'barry' sources (package that allows to charge blackberry devices, but failed.

As for now I do not see any other option, then use some VM with Windows and installed Asus iCharger tool to quick-charge iPad... no other solution for Ubuntu found.

---

### Post by tariqf on 2010-12-31
Hi I use a small program in ubuntu which allows you to enable ipad charging on any usb port. Works a treat on my ubuntu 11.04 test box. I have upped a 64-bit deb file to my wiki here [http://www.yourproblemsolved.com/software](http://www.yourproblemsolved.com/software) with link to the original source also.

---

### Post by miguelastico on 2011-03-19
> **tariqf said:**
> Hi I use a small program in ubuntu which allows you to enable ipad charging on any usb port. Works a treat on my ubuntu 11.04 test box. I have upped a 64-bit deb file to my wiki here [http://www.yourproblemsolved.com/software](http://www.yourproblemsolved.com/software) with link to the original source also.

Thanks man, it works perfectly on my 10.10@64!

---

### Post by ibo.ezhe on 2011-04-01
I had the same problem. I found a fix here:
[http://ubuntuguide.net/how-to-charge-ipad-on-ubuntu-linux-via-usb-ports]("http://ubuntuguide.net/how-to-charge-ipad-on-ubuntu-linux-via-usb-ports")

You should install this deb in case you have an 64-bit system: [http://www.yourproblemsolved.com/sites/default/files/ipad-charge-1.0_20101231-1_amd64.deb.zip]("http://www.yourproblemsolved.com/sites/default/files/ipad-charge-1.0_20101231-1_amd64.deb.zip")

In case of 32bit system, just follow these steps (found here):
[http://korenkov.info/ipad-ipad2-charge-ubuntu]("http://korenkov.info/ipad-ipad2-charge-ubuntu")

```

sudo apt-get install libusb-1.0-0 libusb-1.0-0-dev
wget --no-check-certificate https://github.com/downloads/mkorenkov/ipad_charge/ipad_charge_1.0.tar.gz
tar -xzf ipad_charge_1.0.tar.gz
cd ./ipad_charge_1.0
make
sudo make install

```

---

### Post by generallee5686 on 2011-04-13
For ipad 2 edit /etc/udev/rules.d/95-ipad_charge.rules and change SYSFS{idProduct}=="129a" to SYSFS{idProduct}=="129f"

---

### Post by ibo.ezhe on 2011-04-14
thanks to **generallee5686**'s solution for **ipad2** is now available [http://korenkov.info/ipad-ipad2-charge-ubuntu]("http://korenkov.info/ipad-ipad2-charge-ubuntu").

fixed "129f" key and published it at [GitHub]("https://github.com/mkorenkov/ipad_charge"). See ipad2 branch.

For **ipad2** you can use following code:

```

sudo apt-get install libusb-1.0-0 libusb-1.0-0-dev
wget --no-check-certificate https://github.com/downloads/mkorenkov/ipad_charge/ipad2_charge_1.0.tar.gz
tar -xzf ipad2_charge_1.0.tar.gz
cd ./ipad2_charge/
make
sudo make install

```

---

### Post by scurpio on 2011-05-02
Thank you! Followed the instructions in the above post and now I can charge my ipad 2 on my lenovo thinkpad x200 laptop running Ubuntu 11.04.

---

### Post by owenspa on 2011-05-15
> **ibo.ezhe said:**
> thanks to **generallee5686**'s solution for **ipad2** is now available [http://korenkov.info/ipad-ipad2-charge-ubuntu]("http://korenkov.info/ipad-ipad2-charge-ubuntu").

fixed "129f" key and published it at [GitHub]("https://github.com/mkorenkov/ipad_charge"). See ipad2 branch.



I had to change the udev rule product ID key to 12a2 for my iPad2, got the number from running "lsusb".

It now works wonderfully (ASUS P8H67-M LE motherboard), thanks.

---

### Post by fritz269 on 2011-05-16
I know this is an old post and it prob wont help but I have no problem charging my Garmin Garminfone with Android 2.1 although I do notice that it charges slower on the usb than the wall adapter.

---

### Post by ibo.ezhe on 2011-05-17
fritz269,
most likely this problem is connected to output power. I suppose, USB is not powerful enough compared to wall charge adapter.
Have you tested on other PCs/ OSes?

---

### Post by owenspa on 2011-05-17
> **owenspa said:**
> I had to change the udev rule product ID key to 12a2 for my iPad2, got the number from running "lsusb".

It now works wonderfully (ASUS P8H67-M LE motherboard), thanks.

An update.

It works wonderfully, provided I don't do anything.

I have iTunes running under VirtualBox using Kubuntu 10,10, KDE 4.6.  At (sofar) unpredictable times, the iPad goes into "not charging" mode while I'm accessing it via iTunes.

If I shutdown iTunes and VirtualBox, then reconnect the iPad, it starts
charging again.

---

### Post by ibo.ezhe on 2011-08-04
Kibodeaux, have you tried my solution (posted earlier)?

---

### Post by nrabett on 2011-09-13
> **owenspa said:**
> I had to change the udev rule product ID key to 12a2 for my iPad2, got the number from running "lsusb".

It now works wonderfully (ASUS P8H67-M LE motherboard), thanks.

This worked on an ASUS eee 1015PN, jailbroken iPad2.

---

### Post by Stelaninja on 2012-01-11
> **owenspa said:**
> I had to change the udev rule product ID key to 12a2 for my iPad2, got the number from running "lsusb".

It now works wonderfully (ASUS P8H67-M LE motherboard), thanks.

This also works with an HP Pavilion dv6. Not jailbroken iPad2.

---

### Post by wocsnia on 2012-03-19
The Product id for the "new" ipad (ipad 3) is 12a4. 

The udev rules need to be updated... On my machine:


```

aainscow@Morwenna:/etc/udev/rules.d$ cat 95-ipad_charge.rules 
ENV{DEVTYPE}=="usb_device", ACTION=="add", BUS=="usb", SYSFS{idVendor}=="05ac", SYSFS{idProduct}=="12a4", RUN+="/usr/bin/ipad_charge" 

```

---

### Post by kakashisensei on 2012-03-20
Ipad_charger for all ipads released till now: 

[https://github.com/f00barin/ipad_charge](https://github.com/f00barin/ipad_charge)


Cheers, 
kakashi_

---

### Post by ibo.ezhe on 2012-03-22
thank you, folks.

Util was updated: [http://korenkov.info/ipadcharge-util-updated](http://korenkov.info/ipadcharge-util-updated)
It supports more devices now (including iPad 3)

---

### Post by michaelchan0427 on 2012-03-27
Hi, I have the latest version but still having problems with charging the new iPad.

I saw this from kern.log:

```


Mar 27 10:37:41 HOSTNAME kernel: [88766.163759] gvfsd-afc[15176]: segfault at 0 ip           (null) sp 00007fff0cc86a48 error 14 in gvfsd-afc[400000+c000]


```

Could you please let me know if there is anything I can do to fix this?

thanks

---

### Post by njined on 2012-08-12
Hallo, downloaded the .deb or compiled it return the same error:
ipad_charge: no such device or an error occured
on Quantal, any hint ?
Thanks

---

### Post by elroy001 on 2012-08-22
Hi everyone! I found this page, that's the new link and directions.
How to install the iPad and iDevices Charger of USB port.

[https://github.com/mkorenkov/ipad_charge/wiki](https://github.com/mkorenkov/ipad_charge/wiki)

Regards from México! :p

---

### Post by e64462 on 2012-11-20
My problem is somewhat different than everyone else. I'm trying to actually stop my iphone from charging with this utility. I've tried ```
ipad_charge --off
```
But my iphone still charges. Any ideas?

---

