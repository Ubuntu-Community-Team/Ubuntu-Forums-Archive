---
title: "Epson Stylus CX5400 scanner no longer recognised in Edgy"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by lyskerrys on 2007-02-11
Hi All,

After the latest Edgy upgrade (kernel etc), my Epson Stylus CX5400 is no longer recognised by XSane.  I can print OK but the scanner is no longer recognised - any ideas please?!

---

### Post by myke on 2007-02-16
My Canon LiDE60 is recognized but both Kooka and Xsane crash on launch and I never even get to a program screen.   Sucks.  Use the scanner regularly and now have to do so under XP.  I assume it's due to something with the kernel upgrade as it didn't start until then.

---

### Post by myke on 2007-02-16
Different scanner ... same problem ... this is what fixed mine  >>>

For some reason ... & I don't know why ... after the kernel upgrade, it apprantly affected a setting with my Samsung printer which in turn affected the scanner software even though the printer never stopped working.   After poking around the forums a while, I found this thread:

[http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697]("http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697")

I used the chmod solution and commenting out one line in a root file and now both kooka & xsane are working again.

Specifically, this is what was suggested and what fixed my problem & hey ... I don't know what the kernel upgrade had to do with it but I'm just glad the solution turned out to be relatively simple:

you'll find xsane now executes as root. (This is also true if you have a multifunction printer, but see below instead of this step.) To fix this, since you don't want to run xsane as root, do the following:
a: in a terminal, type "sudo chmod -s /usr/bin/xsane"
b: sudo edit /etc/sane.d/dll.conf, and comment out (add a "#") in front of the line that says "smfp" (probably the last line).
If you only do (a) and not (b), xsane will crash.

Good luck, and let me know if you have success and/or failure, and I'll try to modify accordingly.

---

### Post by jdmpike on 2007-02-18
I chmod'd /usr/bin/xsane, but when I went to edit /etc/sane.d/dll.conf, I didn't have an smfp entry to comment out.

I assume not having it listed would be the same thing as having it commented out?

Anyway, Xsane still cannot find my scanner.

Thanks for the ideas, I will be happy to try anything else you can think of!

-jdmpike

---

### Post by natewlew on 2007-02-18
I seem to have the same problem with my cx5400 on edgy.  I can print I just can't scan.  I have tried to run sudo xsane but it does not help.

---

### Post by jdmpike on 2007-02-19
Does anyone have any ideas where we can start debugging? I really need my scanner to work so I can digitize all of my 2006 tax documents!

Seriously though, does anyone have any thoughts on this - I have no idea how to start debugging, I guess tonight I will tail /var/log while trying to start xsane.

Need some help on this one for sure!

---

### Post by lyskerrys on 2007-03-16
> **jdmpike said:**
> Does anyone have any ideas where we can start debugging?

I'm thinking of giving OS X a try... ;-)

---

### Post by mlaverdiere on 2007-03-25
Hi,

This is a known problem.  See this bug report:  [https://launchpad.net/ubuntu/+source/sane-backends/+bug/67659](https://launchpad.net/ubuntu/+source/sane-backends/+bug/67659)

Here's the quick and temporary fix proposed in the bug report's thread (work for me):

Grab dapper libsane from:
 [http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane_1.0.17-1ubuntu4_i386.deb](http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane_1.0.17-1ubuntu4_i386.deb)
 then as root
 dpkg -i sane-backends/libsane_1.0.17-1ubuntu4_i386.deb
Then to prevent the package changing, do
 aptitude hold libsane


Hope this help.

---

### Post by Riggs on 2007-05-24
> **mlaverdiere said:**
> Hi,

This is a known problem.  See this bug report:  [https://launchpad.net/ubuntu/+source/sane-backends/+bug/67659](https://launchpad.net/ubuntu/+source/sane-backends/+bug/67659)

Here's the quick and temporary fix proposed in the bug report's thread (work for me):

Grab dapper libsane from:
 [http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane_1.0.17-1ubuntu4_i386.deb](http://www.mirror.ac.uk/mirror/archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/libsane_1.0.17-1ubuntu4_i386.deb)
 then as root
 dpkg -i sane-backends/libsane_1.0.17-1ubuntu4_i386.deb
Then to prevent the package changing, do
 aptitude hold libsane


Hope this help.

This worked perfectly for me :)  Thanks for the info.

---

