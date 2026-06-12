---
title: "serial communication with linux kernel device driver that we write"
date: 2017-01-09
forum: Hardware
---

### Post by herhangibirhesap on 2017-01-09
[FONT=&amp]hi sorry bad english but I need to know that issue that I have been seaching for [/FONT]

[FONT=&amp]I want to send data from /dev/my_driver to my arduino.Is there any way to do this?[/FONT]

[FONT=&amp]For example :[/FONT]
[FONT=&amp]
echo "hello" > /dev/ttyUSB0 [/FONT]

how can I write my own device driver I can send data like this way?

---

### Post by herhangibirhesap on 2017-01-10
hi 

we are asked a device driver that send data to arduino 

I planed to write a virtual usb driver like /dev/ttyUSBx does.in this way I can send data by typing echo "hello" > /dev/myUsbDriver to arduino 

but when I tried this [http://opensourceforu.com/2011/12/data-transfers-to-from-usb-devices/](http://opensourceforu.com/2011/12/data-transfers-to-from-usb-devices/) and plug in arduino to usb there was no myUsbDriver in /dev folder?

maybe there is a better way I dont know for sending data to arduino via a normal device driver?

---

### Post by howefield on 2017-01-10
Duplicate threads merged.

---

