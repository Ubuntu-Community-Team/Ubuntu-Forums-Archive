---
title: "HOWTO: Setup the Epson CX6600"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by Haegin on 2005-05-31
I set one of these up earlier and it was a bit of a struggle for me (as a linux n00b) so I thought I would post what to do for anybody else who needs to know.
Where I have given something to type into a terminal it is formatted as code and where I have given text to type into a file it is in quotes. Don't enter the quotes when you type it in, just enter the stuff in between.

1. Plug it in and turn it on (make sure all the tapes and tags are taken off first, the USB port is inside)

2. Fill it with ink and paper as instructed in the little guide you get with it

3. Navigate to System -> Administration -> Printing

4. Select "New Printer" in the window that appears

5. Select it in the list of detected printers (I can't help if its not detected, sorry)

6. Click "Forward"

7. Change the Model to the "Stylus CX-6400" and click "Apply" (Leave the drive as the gimp-print default)

8. You now have a printer working! Yay! Shame scanning isn't so easy to do...

This scanning section was put together from material on the [www.clasohm.com](www.clasohm.com) blog ([permalink to article](http://www.clasohm.com/blog/one-entry?entry%5fid=12616) ). I assume you have a default linux installation with sane and xsane installed. (Obviously I assume you are using sane as your scanning program)

9. Shove the following through a terminal:
```
sudo gedit /etc/hotplug/usb/libsane.usermap
``` 
Search for "0x04b8 0x0813" and if it doesn't appear in the document add the following to the end:
"libusbscanner 0x0003 0x04b8 0x0813 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000"

10. Save and close back to the terminal.

11. Shove another line through the terminal:
```
sudo gedit /etc/sane.d/epson.conf
``` 
Then add the following to the end of the file: "usb 0x04b8 0x0813".

12. Check that you have specified the correct backend in /etc/sane.d/dll.conf (It should be epson) If it is not there, add it on a new line. [Thanks to Glenn Sommer for this]

**Troubleshooting**
If your scanner still does not work:
1. Try entering "sane-find-scanner" into a terminal. It should say something about an unknown flatbed scanner. If it manages this then try "scanimage -L" in a terminal. If this comes up with no scanners found then the scanner is only appearing to root users. If you type "sudo scanimage -L" then your scanner should appear. To fix this enter "lsusb". It should output something like the following:
```

billgates@linuxBase:~$ lsusb
Bus 003 Device 004: ID 0457:0151 Silicon Integrated Systems Corp.
Bus [COLOR="Red"]003[/COLOR] Device [COLOR="Red"]003[/COLOR]: ID 04b8:0813 Seiko Epson Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:0a01 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

```
In the example above my scanner is the second device. Note down the two red numbers (bus id and device id) and enter the following:
```

sudo chmod 666 /proc/bus/usb/<bus_id>/<device_id>

```
(Make sure you fill in the bus id and device id)
Note - this is a temporary fix only which will be lost when you restart! I have created a script to change the permissions and then launch xsane but you will need to edit it to use your bus and device ids. It needs to be placed in /usr/local/bin (or somewhere similar - thats the best place imho) and given executable permissions. You can then create a launcher or edit the xsane menu entry to run "xsane-launcher". I attached the file...

Your scanner should now work, if it doesn't go eat a mars bar (compulsory) and email me (hjmills@gmail.com) (optional)

---

### Post by mmmmm on 2005-07-26
Thank you for the HOWTO... sudo gedit /etc/sane.d/epson.conf ... did the trick for me

---

### Post by xenium on 2005-11-06
I have an Epson Stylus CX4600 that I cant get the scanner working on Breezy. When I try scanimage -L i get a message that says no scanners were detected but when I run sudo scanimage -L I get (device `epson:libusb:001:004' is a Epson CX4600 flatbed scanner). Im assuming that this is a permissions problem but i dont know how to fix this. Any help would be appreciated.:D

---

### Post by Haegin on 2005-11-06
Hi, I have a similar permissions problem at the moment and I can't remember how I did it the first time but to scan stuff I use "sudo xsane" - it comes up with a warning but it works fine. This obviously isnt great - ill try and find a fix.

---

### Post by slam on 2005-11-25
Very nice Howto, but several things to add:

1) Printing

The CX6600 does not work properly with all it's nice functions with the CX6400 drivers. However, the next update of gutenprint (former gimprint) comes with a cups-driver for the CX6600 included. Don't install and use the commercial drivers from Avasys - no need for them, and quite problematic on a Debian system.

2) Scanning

Perfect, probably the most simple solution to get the scanner running. Just don't forget to

```
sudo /usr/sbin/saned restart
```

after changing the config files. After that xsane should work out of the box. If you need further functionality search for libsane-extras and change the epson backend against the epkowa backend.

Also be carefull with future updates to sane, some of them are known to interrupt scanning for several Epson multifunctionals.

Greetings,
Chris

---

### Post by Haegin on 2005-11-25
Thanks for the feedback - glad it helped. How do I get the new drivers? The gutenprint.sf.net site is down at the moment. Can I install them from synaptic?

Thanks

---

### Post by teaker1s on 2005-12-13
running epson iscan program and I've altered sane so now I can Scan with
iscan
sane 
sane through gimp

with sane I removed sane extra libs -if you don't you will have a terrible time with alien
sudo alien -di- iscan-1.18.0-1.c2.i386.rpm

to run iscan 'iscan'
edit the epkowa.conf in sane so it has this line
usb  0x04b8 0x0813
I've yet to get the cx6600 driver to work but cx 8300 works as well as cx6400

---

### Post by obuengineer on 2006-08-21
I get an error when I try to add this line to libsane.usermap:

libusbscanner 0x0003 0x04b8 0x0813 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000

It says it can't save the file.  I don't remember the exact error message at the moment.  However, when I run sane-find-scanner it finds the scanner.  But scanimage -L does not work.  I tried using your script to run xsane in root mode, but xsane could not find any scanners as before.  You should know that I'm running ubuntu as a virtual machine within windows, so I'm not sure if this could be the problem.  Other hardware seems to work just fine, so I'm inclined to think it's not an issue.

I'm a linux newbie, so it's very frustrating that simple things seem to take so much effort to get to work.  It makes me want to just stick to windows until hardware and software installation in linux become simpler.

---

### Post by Haegin on 2006-08-21
Try opening the file as root using sudo if you are not already. If you are more familiar with gedit or another text editor use that instead of nano.

---

### Post by ricegf on 2007-08-04
> **obuengineer said:**
> I get an error when I try to add this line to libsane.usermap... It says it can't save the file.

The error message is *literally* true, but not particularly helpful. A better error message would read, "The /etc/hotplug/usb folder does not exist. Create?  /Yes/  /No/".  That is, the reason you can't save the file is that Ubuntu doesn't create the hotplug or usb folders on installation, and the editor doesn't know how to create them on save.  

You'll need to help the editor by using these commands *before* editing:

sudo mkdir /etc/hotplug
sudo mkdir /etc/hotplug/usb

Now edit the file, and all will be well.  I followed these directions on Fiesty Fawn, and my cx6600 is scanning nicely with the above change.

> **obuengineer said:**
> I'm a linux newbie, so it's very frustrating that simple things seem to take so much effort to get to work.

I agree with you, this should be a lot easier than it is. If this isn't fixed in Gutsy Gibbon, I'll create a simple script you can run to set it all up from a generic install, and post it here. Promise.  :)

---

### Post by Haegin on 2007-08-04
There is an updated version of this guide for all versions of Ubuntu since 6.06 (Dapper) located here: [http://hjmills.co.uk/computers/linux/cx6600.php](http://hjmills.co.uk/computers/linux/cx6600.php).

That uses UDev not hotplug so it works as intended. Please try that guide and it should work.

---

### Post by NT4.0 on 2008-02-19
I had the same problem. I got it working, finally! I found by sane-find-scanner that mine was at 04b8:082b. Adding "usb 0x04b8 0x082b" to /etc/sane.d/epson.conf solved the problem. Thanks a lot!

---

### Post by NT4.0 on 2008-02-19
test - please delete

---

### Post by kriukov on 2008-02-19
To make it work under a non-root account, this page helped:

[http://ubuntuforums.org/archive/index.php/t-166944.html](http://ubuntuforums.org/archive/index.php/t-166944.html)

"Open /etc/udev/rules.d/40-permissions.rules as root and change usb device subsystem to mode=0666"

---

