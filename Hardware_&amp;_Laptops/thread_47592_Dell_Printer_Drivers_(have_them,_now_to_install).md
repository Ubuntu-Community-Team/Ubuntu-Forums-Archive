---
title: "Dell Printer Drivers (have them, now to install?)"
date: 2005-07-09
forum: Hardware &amp; Laptops
---

### Post by brim4brim on 2005-07-09
Hi I have a Dell A920 printer and I've gotten the Lexmark Z600 compatible drivers in a .sh file. 

Now for the problem they are designed for Red Hat and when I use the command line and sh on the file I get nothing and no driver appears in the list for printers.

I read on the web from people with similar problem with this printer that they managed to convert this driver to a debian compatible with a tool.  Now the only problem is they failed to mention the tool!

So does anyone know of anything that will do this?  Thanks in advance!

---

### Post by adwait on 2005-07-09
If they are in an rpm file, you can use alien <foo.rpm> and then install using dpkg -i foo.deb.

---

### Post by brim4brim on 2005-07-09
[QUOTE=adwait]If they are in an rpm file, you can use alien <foo.rpm> and then install using dpkg -i foo.deb.[/QUOTE]

Okay thanks, the original problem was they weren't in RPM format but the download only gave me a .sh file and a readme which was weird so I just looked again and found a compatible .rpm version and am going to try to install it now.

---

### Post by brim4brim on 2005-07-11
[QUOTE=adwait]If they are in an rpm file, you can use alien <foo.rpm> and then install using dpkg -i foo.deb.[/QUOTE]

I have the .deb but I get an error:

dpkg: error processing z600llpddk.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 z600llpddk.deb

---

### Post by brim4brim on 2005-07-11
[QUOTE=brim4brim]I have the .deb but I get an error:

dpkg: error processing z600llpddk.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 z600llpddk.deb[/QUOTE]
 Okay I know I can get these files out of the .RPM using the archiver but is the dir structure in the file comparable to where they should go in Linux and how can I make/compile the files.

---

