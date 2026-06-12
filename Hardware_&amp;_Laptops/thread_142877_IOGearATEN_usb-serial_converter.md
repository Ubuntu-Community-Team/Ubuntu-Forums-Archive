---
title: "IOGear/ATEN usb-serial converter"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by StevenB on 2006-03-11
I have an IOGear usb to serial converter, which I am trying to get to work on linux.  It is identical to the ATEN product here: [http://www.aten.com/products/productItem.php?pcid=20050107104554001&psid=20050117102915002&pid=2005022316346005]("http://www.aten.com/products/productItem.php?pcid=20050107104554001&psid=20050117102915002&pid=2005022316346005")
The linux driver (for RedHat) is a .zip file containing a .c file and a makefile.
When I follow the readme and type in "make inst", it says:
make: *** No rule to make target `pl2303.c', needed by `pl2303.o'.  Stop.

Do I just need to compile the file directly, and if so, what do I do with it from there?
Or, will Ubuntu find it and be able to use it if I just plug it in?  How do I test it?
Thanks!

---

