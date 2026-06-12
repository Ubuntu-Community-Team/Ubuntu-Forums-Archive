---
title: "canon pixma ip 3500"
date: 2008-10-20
forum: Hardware
---

### Post by chrischan on 2008-10-20
Hi!
Was anybody successfull in printing color with the printer "Canon PIXMA IP 3500" on Ubuntu 8.04? From [this 7.04 thread]("http://ubuntuforums.org/showthread.php?t=631448&highlight=canon+pixma+3500"), I followed the instructions from [Canon Australia]("http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&v%3afile=viv_qUQd06&v%3astate=root%7croot&opener=full-window&url=http%3a%2f%2fsupport-au.canon.com.au%2fcontents%2fAU%2fEN%2f0300055001.html&rid=Ndoc3&v%3aframe=redirect&&sid=6"), but the command /usr/sbin/lpadmin -p CanonIp3500 -m canonip3500.ppd -v cnij_usb:/dev/usblp0 -E

always gives me

lpadmin: „device-uri“ „cnij_usb:/dev/usblp0“ wrong!

Any hints?

---

### Post by Thelasko on 2008-10-20
Well this page says to go to [Cannon Europe and download the .deb file.]("http://software.canon-europe.com/products/0010487.asp")  Why don't you do that?

[Open printing]("http://openprinting.org/show_printer.cgi?recnum=Canon-pixma_ip3500") says it should work.

---

### Post by georgegerm on 2008-10-28
well because theres is nothing to download,,
the page is there but not the download:guitar:
that is the deb. download the one rpm is there
any one got it and it worked please share it

---

### Post by Thelasko on 2008-10-28
I didn't try to download the .deb file.  Try the RPM with [Alien.]("http://www.howtoforge.com/converting_rpm_to_deb_with_alien")

---

