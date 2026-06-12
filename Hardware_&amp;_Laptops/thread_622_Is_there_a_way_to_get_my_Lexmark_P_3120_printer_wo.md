---
title: "Is there a way to get my Lexmark P 3120 printer working?"
date: 2004-10-14
forum: Hardware &amp; Laptops
---

### Post by Flawed on 2004-10-14
The only inbuilt driver that seems to be able to communicate with my printer is the Lexmark 3200 one, but all  it can make my printer do is make noises and spit out blank pages. Are there any other drivers I should try? Lots of thanks in advance and congrats on putting together such a fine distro, by the way. :)

---

### Post by spaaz9 on 2004-10-14
[http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-3200](http://linuxprinting.org/show_printer.cgi?recnum=Lexmark-3200)

---

### Post by Flawed on 2004-10-15
Hmm, so I guess this means the 3200 driver is the proper one for my P 3120?

---

### Post by spaaz9 on 2004-10-15
I've looked around, and apparently there is no driver for the p3120, and no one has been able to get it to work properly.  Lexmark is really bad about supporting Linux.  I know.  I have a Z23, and it is a paperweight under Linux.  Your best bet is to get a new printer, or try to get them to release a binary driver for that printer, but they don't have much interest in doing that from my experience with them.

---

### Post by adbak on 2004-10-15
Hey.  I had a similar problem with the Ubu version of CUPS not noticing my printer.  Luckily my Linux friend-guru told me to add ```
deb ftp&#58;//ftp.nerim.net/debian-marillat/ unstable main
``` to my ```
/etc/apt/sources.list
```.  I then updated apt, searched for CUPS, and installed the new ones.  You might also wanna update gimp-print* as well.

Then try setting up your printer again.  It should work after that.

---

