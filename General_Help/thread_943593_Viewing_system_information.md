---
title: "Viewing system information"
date: 2008-10-10
forum: General Help
---

### Post by Kaolccips on 2008-10-10
First off let me just say that I'm completely new to Linux OS and this forum.. So hello and I apologize if this is in the wrong section.

I'm looking for a way to view all my system info on Ubuntu (CPU/RAM/GPU) and I'm having a little trouble finding something.  I tried to install HSInfo but I was unable to get it working and received an error when I tried to use it.

So is there any commands or a linux app that I can use to view this information?


Thanks,
Kaolccips

---

### Post by tang0delta on 2008-10-10
System >> Administration >> System Monitor >> System Tab?

Dunno if this is what you want but for me it shows my Processors, RAM, HDD Space, ubuntu version and kernel and desktop environment...

Otherwise, I never have any interest in looking at this stuff so I dont know anything about any applications that can tell you this info. Hope this helps

---

### Post by Zill on 2008-10-10
Open a terminal (menu Applications, Accessories, Terminal) and enter the following code at the prompt...
```
sudo lshw -html > ~/Desktop/hardware.html
```
This will create a file called hardware.html on your Desktop. Click on this file to view it in your default web browser.

---

### Post by Yellow Pasque on 2008-10-10
If you want way too much information about your BIOS, RAM, PCI slots, use:
```
sudo dmidecode
```

---

