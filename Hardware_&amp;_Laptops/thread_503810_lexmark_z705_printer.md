---
title: "lexmark z705 printer"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by vbdanl on 2007-07-18
Hi.  I was wondering if anyone has successfully installed a lexmark z705 printer in ubuntu?  I followed the directions for installing the 600 driver, and got it to print, but it cuts off the print on the left side of the page.  it looks like the paper needs to be moved to the left about an inch or so.  it printed fine with w98, so i know its not the printer or paper alignment tabs (hdwe).
i tried to install a 700 series driver from the lexmark site, but after installing it, i don't see z705 or any other z700 series printer as a selection when installing the driver through admin.
i expect i will get it working sooner or later.. just wanted to know if someone else actually has one that works with ubuntu feisty..
thanks

---

### Post by vbdanl on 2007-07-27
bump
still no luck getting it to work..

---

### Post by w4ett on 2007-07-27
According to this site:

[http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)

there is a separate diver for the z705.  The link also contains the driver and instructions.

---

### Post by vbdanl on 2007-07-27
I actually tried to use those exact instructions.  created a .deb file from the .rpm, then tried to install with dpkg.  i thought it installed, but i don't get z700 or z705 as a printer option from the list of CUPS supported printers as it suggests.  Not sure if I did something wrong or what else I need to do..

---

### Post by vbdanl on 2007-07-27
Here is what i get when i downloaded the .rpm files, converted them to .deb packages with alien (--script):

dan@Antec:~$ sudo dpkg -i z700llpddk_2.0-2_i386.deb
(Reading database ... 119790 files and directories currently installed.)
Preparing to replace z700llpddk 2.0-1 (using z700llpddk_2.0-2_i386.deb) ...
Unpacking replacement z700llpddk ...
Setting up z700llpddk (2.0-2) ...

dan@Antec:~$ cd Desktop
dan@Antec:~/Desktop$ sudo dpkg -i lexmark-z700-cups-driver_1.1.1-2_i386.deb
Selecting previously deselected package lexmark-z700-cups-driver.
(Reading database ... 119790 files and directories currently installed.)
Unpacking lexmark-z700-cups-driver (from lexmark-z700-cups-driver_1.1.1-2_i386.deb) ...
Setting up lexmark-z700-cups-driver (1.1.1-2) ...
/var/lib/dpkg/info/lexmark-z700-cups-driver.postinst: 2: /etc/init.d/cups: not found
dpkg: error processing lexmark-z700-cups-driver (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 lexmark-z700-cups-driver

What do I need to do to fix the errors?
thanks.

---

### Post by w4ett on 2007-07-28
To me, it looks like you did everything right....it might be a broken package....I've  seen this same error referred to in these forums with other app packages (samba in particular)...I'm not a printer guy (I got an HP, worked out of the box)...you might try finding an alternative download site (maybe MFG website) and re-attempt the install..

---

### Post by vbdanl on 2007-07-30
I ended up installing the two z700 packages by compiling the source code, using the .configure, make, and make install scripts that came with them.  i can choose z700 ppd file when i setup a new printer.  everything appears to work, except it will not print anything.  no test page, no file print, nothing comes out.  if i press the feed button, it will shoot out a blank page.  i tried unplugging the usb cable and using a different port, and have rebooted.  still will not print.  went back to the ":136" cups website and tried to download cups software again, but couldn't remember how i originally got past the username and password prompts.  i tried every valid password and username i have, but still did not get past the prompts.  not sure if re-installing the cups stuff was going to help or not..  have added cupsys to group shadow entry, but that also did not help anything.  seems like i should be close.. any ideas?

---

