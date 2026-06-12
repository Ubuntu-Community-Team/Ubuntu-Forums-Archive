---
title: "Making a .deb from 2 sources."
date: 2008-10-27
forum: General Help
---

### Post by foldor on 2008-10-27
OK here is the how it is. I have a program that has a command line interface that I have successfully compiled, and I also have a GUI successfully compiled for the program. They are separate binaries and have separate makefiles. I'd also like to include some files that would go into the users home directory, but are not binaries. Is there a way to get a .deb that installs both programs, puts a link to the GUI binary, along with its icon in the menu, and sticks the extra files in the users home directory?

---

### Post by koenn on 2008-10-27
a .deb is nothing but an archive 
you can put pretty much any thing you want in it, including conf files or other stuff that needs to go in specific directories. You could just compile your source and put the binaries in the package by hand in stead of using the 'build a .deb from source" tools
you can also include scripts that run automatically before or after the archive is unpacked (by apt or dpkg)
read this to get you started:
[http://users.telenet.be/mydotcom/howto/linux/package.htm](http://users.telenet.be/mydotcom/howto/linux/package.htm)

---

