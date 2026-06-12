---
title: "Printer makes a lot of noise but isn't printing"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by MadMax2 on 2009-03-15
I have just installed 8.10 and have a  HP Deskjet 3325. WhenI print a test page there is no ink on the page. I tried some yellow and nothing there either. A message says the ink is low but I would expect a faint (something). I dabed the cartridge on some paper and got black.

Will linux run it from the install CD?
Thanks
Max

---

### Post by gjoellee on 2009-03-15
I'va got a HP C5180 Photosmart, and it makes a lot of noise sometimes, it says it is maintaining itself (maybe that is what your printer is doing as well). Now I wonder....how the heck can a printer maintain itself?

However, have you installed HPLIP, or to you use CUPS?

---

### Post by MadMax2 on 2009-03-15
I looked in synaptic passage manager and I seem to have HPLIP, and CUPS.

The printer is printing but no ink is coming out (I think there is ink in there). I'll test it on my wifes windows laptop later.

---

### Post by MadMax2 on 2009-03-15
I ran HP Check:

Checking for dependency: cups-devel- Common Unix Printing System development files... 
error: NOT FOUND!
Checking for dependency: dbus - Message bus system... 
error: NOT FOUND![ **Installed?**]
Checking for dependency: gcc - GNU Project C and C++ Compiler...

error: NOT FOUND!**[installed?]**
Checking for dependency: libcrypto - OpenSSL cryptographic library...

error: NOT FOUND!
Checking for dependency: libjpeg - JPEG library...

error: NOT FOUND
Checking for dependency: libnetsnmp-devel - SNMP networking library development files...

error: NOT FOUND!
Checking for dependency: libtool - Library building support services...

error: NOT FOUND!
Checking for dependency: python-devel - Python development files...

error: NOT FOUND!

I tried to down load python devel but it was rejected by Archive manager.
Thanks
Max

---

