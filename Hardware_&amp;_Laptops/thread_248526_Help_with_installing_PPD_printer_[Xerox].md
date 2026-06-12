---
title: "Help with installing PPD printer [Xerox]"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by canopic on 2006-09-01
Hi! I need a little help.
I have already installed this printer with other flavours - Mandrake, Mepis, Fedora Core, but I don't know how to do it with Ubuntu6.06.
These other distros have all been installed with KDE, but with Ubu i need to use Gnome.
My Xerox install script advises my printer is compatible with Debian 2.2 and above, Red Hat 7.1 and above, SuSE 7.1 and above etc, etc.
Ubu is derived from Debian, right[?], so this gave me hope.
But pre-requisites are GTK+1.2 and higher, Ghostscript, and Glibc2.1 or higher, as well as CUPs of course. but Ubu is bleeding edge and uses later stuff - it doesn't even seem to make GTK+x.y or Glibcx.y available for any x.y versions - or am I not right?  I am only just starting to use Ubuntu and like the little i have seen, but it would be a real draw back if I can't use my printer.

Do I need to perservere with the Xerox installation script [perhaps editing some of the file names to reflect newer versions, or can I discard this script and use some other proceedure to install my PPD file and setup the printer?

I would really appreciate any helpful input even if you don't have all of the answers. 

What files [such as GTK, glibc, ghostscipt ] does a PPD printer installed under Ubuntu6.06 normally require?
Thanks heaps!

---

### Post by zxee on 2006-09-01
You must have GTK on your sytem do > which gtk
But I can't speak to all of that.
For setting up your printer you can check the official ubuntu guide [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)
and  linuxprinting.org [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)

---

### Post by halitech on 2007-03-03
depending on the make/model printer you have, it may just be a matter of going through the install like you would in windows and then browse to where you have the PPD files located.

---

### Post by geichel on 2008-01-08
The Xerox setup program drops the PPD files in /usr/Xerox/xpxx/ppd. Use System --> Administration --> Printing --> New Printer and point the wizard at the PPD file.

The setup program drops a log in /tmp.
[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC4150&Xlang=en_US&Xcntry=USA](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC4150&Xlang=en_US&Xcntry=USA)

---

