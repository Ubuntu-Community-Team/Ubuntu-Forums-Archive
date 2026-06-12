---
title: "Epson sx600f printer"
date: 2008-12-24
forum: Hardware
---

### Post by jerrykenny on 2008-12-24
Help . . . . 

This is a new printer, the installation is using a driver downloaded from avasys, . . . this driver generates a ppd file for you.

Configuring via cups, then attempting to print gives the error message

Can't write page 1 header

The cups log is getting enormous. . . 

This may not be relevant, . . . but the installation of the 3rd party driver stalled at not finding  libltdl.so.3 . .  i'd overcome this by creating a link like this . .  sudo ln -s  /usr/lib/libltdl.so.7  /usr/lib/libltdl.so.3

---

### Post by cariboo on 2008-12-24
You should need any extra drivers, IF you go to System-->Administratiion-->Printing and install the printer following the prompts. According to [this]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_SX600FW"), all you need is the gutenprint driver.

Jim

---

### Post by jerrykenny on 2008-12-24
Yes but on the same page it says 

The properties of this printer are not yet entered into the database
This printer is only listed here because it is in the list of supported printers of the entries for the drivers shown below.

In other words it should work "in theory"  . . . looks like it hasnt actually been tested yet.

---

### Post by jerrykenny on 2008-12-25
Update . . . its sort of getting there . .  

I have it printing, it was probably printing at a much earlier stage in the proceedings, however, it WONT print the test-page.

If i just open a file (text or photo using gimp) it'll print ok

---

