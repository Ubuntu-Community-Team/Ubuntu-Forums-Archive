---
title: "Epson Drivers"
date: 2016-08-03
forum: Hardware
---

### Post by Lurch310 on 2016-08-03
Firstly, I am relatively new to Ubuntu, so have been tediously following installation instructions as seen below.

john@john-Inspiron-1110:~/Downloads/john$ sudo dpkg -i epson-inkjet-printer-201214_1.0.0-1lsb3.2_i386.deb
[sudo] password for john: 
dpkg: error processing archive epson-inkjet-printer-201214_1.0.0-1lsb3.2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 epson-inkjet-printer-201214_1.0.0-1lsb3.2_i386.deb
john@john-Inspiron-1110:~/Downloads/john$ 

The driver deb file is in Home/Downloads/john
My Epson WF-1030 is not listed and the suggested available drivers make a pig's breakfast of printing if they work at all.
I am running 16.04 LTS on a Dell Inspiron 11.
Why must this be so difficult?

---

### Post by QIII on 2016-08-04
Hello!

Generally, it's not that difficult.  But sometimes support from OEMs for Linux is not the best.  There's not much we can do about that.

Your message seems to indicate that the .deb file you are trying to install from doesn't exist.  That's pretty straight forward.  What isn't often straight forward is finding out if you've make an esoteric typo or something.  I hate to say it, but that bites me all the time.

In the terminal, navigate to the directory where you believe the downloaded .deb to be.  Issue the "dir" command to list the files there.

Copy the .deb file name to your clipboard and then reissue the install command after replacing what you think the file name is with the contents of your clipboard.

Let us know how you manage.

Cheers!

---

