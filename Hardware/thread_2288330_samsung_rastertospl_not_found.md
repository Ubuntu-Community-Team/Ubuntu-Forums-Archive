---
title: "samsung rastertospl not found"
date: 2015-07-26
forum: Hardware
---

### Post by fachat on 2015-07-26
Hi there,

I am desperate because updating vom 14.10 to 15.04 has broken my printer. I'm using a Samsung CLP-365 colour laser printer. When I try to print something, I get an error message

 [Job 208] File "/usr/libexec/cups/filter/rastertospl" not available: No such file or directory

in the cups debug logs (/var/log/ups/error_log file) and in the print queue. I have downloaded the current Samsung universal driver and installed it, but did not work.

In fact I can, as normal user, even run /usr/libexec/cups/filter/rastertospl" and it gives me a normal usage message.

In another post here this was suggested:
> have you tried this method: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)
Yes, I have now uninstalled the Samsung universal driver and installed these repositories, but to no avail.
It seems still the rastertospl filter is still referenced, but suldr only supplies rastertosamsungpl, so I 
set a symbolic link. No help.

I noticed that in the apparmor profile the filter directories were written as "/usr/lib/cups/filter" - on my system /usr/libexec points there.
So I tried editing the apparmor profile /etc/apparmor.d/usr.sbin/cupsd to include the libexec path, but didn't work. 
I tried to teardown apparmor profiles with "/etc/init.d/apparmor teardown", but didn't help (even after restart of cupsd).

I think I'm really stuck right now. If anyone has an idea what is happening, it is greatly appreciated!

Many thanks in advance!
André

---

### Post by dino99 on 2015-07-26
can you check if /usr/libexec/cups/filter/rastertospl exist, and right-click it to know about its rights

your printer should works out of the box with the 'printer-driver-foo2zjs' driver from the ubuntu archive (avoid all non genuine ubuntu packages).
if that driver was already installed, then purge it (right click and select complete removal, from 'synaptic') then reinstall it

---

### Post by fachat on 2015-07-31
> **dino99 said:**
> can you check if /usr/libexec/cups/filter/rastertospl exist, and right-click it to know about its rights

your printer should works out of the box with the 'printer-driver-foo2zjs' driver from the ubuntu archive (avoid all non genuine ubuntu packages).
if that driver was already installed, then purge it (right click and select complete removal, from 'synaptic') then reinstall it

Hi there, this is what I see in /usr/libexec/cups/filter/

-rwxr-xr-x 1 root root  72116 Apr  9  2012 rastertosamsungspl
-rwxr-xr-x 1 root root 121016 Apr  9  2012 rastertosamsungsplc
lrwxrwxrwx 1 root root     18 Jul 26 14:08 rastertospl -> rastertosamsungspl
lrwxrwxrwx 1 root root     19 Jul 26 14:09 rastertosplc -> rastertosamsungsplc

Before and after re-installing printer-driver-foo2zjs as recommended, the printer driver for the printer was set to "Samsung CLP - 365 Foomatic/foo2qpdl (recommended)".

Trying to print after the re-installation still gives the error message 'File "/usr/libexec/cups/filter/rastertospl" not available: No such file or directory' in the printer box.

Note that I am using a remote raw printer with a local driver.

Any ideas?
André

---

### Post by fachat on 2015-07-31
Also note that I get the same error message when using a different driver, "Samsung CLP - 360 Series (SPL-C).

---

### Post by fachat on 2015-08-01
I might have run into a very stupid problem - it looks as if the remote printer server was modified to use a Samsung driver instead of the raw driver. 
Setting it back to RAW printing started to work again!

It is strange, however, because it used to work before the update of the client to kubuntu 15.04 - and still works (i.e. worked, not tested with the RAW setting yet) with a non-updated 14.04LTS machine.

It would be nice, though, if cups would write out errors from the remote server as such - and not in a way that you think it's an error on the local machine!

André

---

### Post by ebnodb on 2016-07-03
I just got my Samsung Printer working and here are the steps that worked:

1) Download Linux Printer Driver fro your Samsung Printer model from Samsung Website.
2) ULD_Linux_V1.00.06.tar.gz will appear in your Downloads folder.
3) Extract the file and you should see a file called uld.
4) Create a folder called "SamsungPrinter" in the Documents folder.
5) Copy the uld to the documents folder.
6) Open a command prompt.
7) cd to /Documents/SamsungPrinter/uld
8) type sudo ./install.sh
9) Follow instructions
10) Hook up printer
11) Go to system Settings
12) Click on Printers
13) Go through steps to add your printer. The driver should be in place, and Ubuntu should find it.

---

### Post by oldos2er on 2016-07-04
Old thread closed.

---

