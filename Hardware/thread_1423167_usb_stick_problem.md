---
title: "usb stick problem"
date: 2010-03-06
forum: Hardware
---

### Post by highrik on 2010-03-06
Hi

Ubuntu (hardy heron) currently won't detect my usb stick which I have a bunch of files on.  If I put the stick in a windows xp system  it detects it but says it needs formating.  

any help to save my files would be much appreciated.

cheers
Rick

---

### Post by jerrrys on 2010-03-06
in terminal enter **lsusb** and see if its being detected.

---

### Post by highrik on 2010-03-06
When I typed lsusb in the terminal this was the output:

rick@highrik:~$ lsusb
Bus 002 Device 003: ID 5136:4678  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

hopefully the top one 'Bus 002 Device 003: ID 5136:4678' is my stick?

---

### Post by jerrrys on 2010-03-06
kubuntu must be different, here's how my PNY reads

[ATTACH]149221[/ATTACH]

---

### Post by highrik on 2010-03-06
Hehe.. I'm actually using ubuntu hardy heron.  Not sure why I had my flavor on Kubuntu:D

yes.. 'Bus 002 Device 004: ID 5136:4678' is definately my usb stick as it disappears when I remove it and retype lsusb in a terminal.  hmmmm... it being detected is good news  :).  Any idea where to go form here?

---

### Post by jerrrys on 2010-03-06
804 is also my primary and that command will pull up my usb and give me a desktop icon :confused:

---

### Post by jerrrys on 2010-03-06
im not sure if its in 804 synaptic, but this my help

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by highrik on 2010-03-06
Cheers.. I'll have a look at testdisk and see if I can get it to work :)

---

