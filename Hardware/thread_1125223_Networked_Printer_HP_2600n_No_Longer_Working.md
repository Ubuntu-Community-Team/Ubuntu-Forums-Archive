---
title: "Networked Printer HP 2600n No Longer Working"
date: 2009-04-14
forum: Hardware
---

### Post by bearslumber on 2009-04-14
Hi,

My HP 2600n Printer connected to my local network at address 192.168.1.4 has lately mysteriously stopped printing from Ubuntu. 

This is strange because it has been printing without any problems since I first installed it.

When it stopped working, I used System->Administration->Printing and deleted the printer.

I then reinstalled it as follows:
```
System->Administration->Printing->New->Printer
```
 and it gave me ```
HP Color Laserjet 2600n 192.168.14
``` select connection in the ```
New Printer
``` dialog box with IP 192.168.1.4 and port 9100. The IP is certainly correct. My vista machine pints perfectly with this IP address setting.

I selected this and after searching for drivers I chose ```
HP Color Laserjet 2600n Foomatic/foo2hp [en] (recommended)
```.

I chose the remaining default settings and the result was the following printer was installed ```
HP-Color-Laserjet-2600n
```

Still nothing printed.

So I opened the properties dialog box and selected ```
print test page
```. This went off and gave all the signs that it was printing, but it did not and the printer state reported```
 idle - /usr/lib/cups/filter/foomatic-rip failed
```.

And I still can't print.

Boohoooooo[-o<

Any help would be greatly appreciated.

Regards

Bearslumber

---

### Post by bearslumber on 2009-05-19
Hi,

I got this working. I upgraded to Jaunty. That recognised my printer and downloaded the coirrect drivers automatically and presto.

Thanks for reading.

Bearslumber

---

### Post by mastergunner on 2009-10-17
I upgraded as well but mine does not work.

---

