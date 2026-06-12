---
title: "Printer Help"
date: 2010-03-08
forum: Hardware
---

### Post by vw_man72@hotmail.com on 2010-03-08
Hello all. I am new to Ubuntu and am having a hard time with my printers. I have 2 printers. ONe for black and white and one for color.

The first - Kyocera FS-1920. I use this printer for black and white documents. It will print but instead of it being my document it prints only 2 lines on the top of the page and they are only letters, numbers and symbols. I'm guessing my software is incorrect.

The second - I have a Dell A920. It shows being connected but will not do anything. 

Any help would be awesome. Thanks in advance!

MIke

---

### Post by sgosnell on 2010-03-08
You need the proper drivers.  Try the manufacturers' websites.  Linux drivers for those may not exist, but I haven't looked.

---

### Post by Objekt on 2010-03-09
Here's a helpful link: [http://www.linuxfoundation.org/collaborate/workgroups/openprinting]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting")

There, you can look up what support exists for your printer under Linux.

You're in luck.  According to the website, your Kyocera FS-1920 is fully supported, with a .ppd driver available.  

Unfortunately, hardly any Dell printers have Linux drivers, including yours.

To use the Dell printer, one workaround is to run a virtualized Windows machine under Ubuntu, using Virtualbox or another virtualization program.  You can use the Windows-only printer from the virtual Windows machine.  It is inconvenient, but it does work.  I have done it for a while with my Canon Multipass F60 (again, no Linux drivers exist).

---

