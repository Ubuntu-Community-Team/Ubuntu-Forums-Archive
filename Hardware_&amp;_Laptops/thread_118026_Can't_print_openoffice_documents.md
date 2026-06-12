---
title: "Can't print openoffice documents"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by Elijah on 2006-01-16
Printer: Konica Minolta 2430-DL, half working


Error:
Paused: Print file was not accepted (client-error-document-format-not-supported)!

That's what I get at the printer administration for gnome whenever I use openoffice to print some files. It works on printing web pages for firefox and even test pages ... but what's important is to be able to print in openoffice ... 

What could be the problem here?? :confused: is there any way I could tell openoffice to use lpr command?

---

### Post by Elijah on 2006-03-16
*bump* 

anyone?

---

### Post by Elijah on 2006-03-17
This is not good. I just came home and tried using my Canon S100SP printer and it's the same problem! I could print test pages but not from openoffice. 

This printer of mine is already tested to work on most linux distro's, except for ubuntu which can only print test pages!!

---

### Post by Elijah on 2006-03-22
bah, fixed. Used socket://<ip>:9100 instead of ipp://<ip>/ipp ... this is for Minolta 2430DL, connected to a network. 

I haven't tested with my Canon yet, ... can't use socket & ip for that since it's just a usb printer ...

---

