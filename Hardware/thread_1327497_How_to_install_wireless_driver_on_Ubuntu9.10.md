---
title: "How to install wireless driver on Ubuntu9.10"
date: 2009-11-15
forum: Hardware
---

### Post by SeverusSnape on 2009-11-15
[SIZE=3]Hello,[/SIZE]
 
[SIZE=3]I've sony notebook that has ralink wireless card part number rt2860. I've downloaded the driver but I don't know how to install it on my notebook.[/SIZE]
[SIZE=3]I'd like to ask you how to install wireless driver?[/SIZE]
 
 
[SIZE=3]Regards.[/SIZE]

---

### Post by webbdawg on 2009-11-15
If you wireless is not working in 9.10 make sure you first install the Network Manager widget. I know kind of weird.

Right click on the desk top or task bar and look for the widget control panel.

Click the add widget

It took me over a week to find out this is what I needed to do after upgrading to 9.04 and I understand it is an issue still in 9.10

---

### Post by coffeecat on 2009-11-15
I believe that ralink chipset works out of the box with 9.10 and you don't need to install any driver. And you don't need to install Network Manager as the last poster suggested. NM comes with a default installation. :confused:

Try this:

Go to the Network Manager icon towards the right on the upper panel. It's between the sound icon and the Empathy icon (looks like an envelope). Before you configure a connection, the NM icon looks fairly nondescript. Click on the icon. Does your wireless network show? If so, click on it and put in your WPA/WEP passcode where prompted.

---

### Post by SeverusSnape on 2009-11-15
I'd like to thank you both webbdawg and coffeecat, but I think that the wireless driver dosen't install because the wireless led dosen't work at all.
P.S. my wireless network dosen't appear in NM.
 
Please I need more suggestions. 
 
Thank you.

---

### Post by coffeecat on 2009-11-15
Double-check that you haven't accidentally switched the wireless switch to the off position. I've done this myself on my Sony laptop.

---

### Post by SeverusSnape on 2009-11-15
I've checked that Mr. coffeecat and the wireless led dosen't work.
I wrote "sudo sh install.sh" in termenal then a window appeard and I was asked to enter the bath folder and I kept the defult written bath "/root/ralink", after that another window appeard to me and I was asked to enter "Web UI port number" and also I kept defult value "8080"
 
How can I fill the values correctly.
 
Regards.

---

