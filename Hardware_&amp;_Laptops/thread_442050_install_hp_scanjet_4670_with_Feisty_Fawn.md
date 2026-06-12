---
title: "install hp scanjet 4670 with Feisty Fawn"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by ammmom on 2007-05-13
[INDENT]*I originally posted this on the absolute beginners' board, but I didn't get any responses.  I'm a three-day beginner, from XP.  TIA for any responses.*[/INDENT]

Hi, I'm trying to install hp scanjet 4670 with Feisty Fawn. I looked through some previous threads. When I click on "xsane image scanner" I get "no devices available.

I went to terminal and tried to follow some previous directions. This is what I've gotten so far:
ammmom@ammmom-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c512 Logitech, Inc.
Bus 002 Device 003: ID 04f9:0028 Brother Industries, Ltd
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 03f0:3005 Hewlett-Packard
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp.
Bus 001 Device 001: ID 0000:0000
ammmom@ammmom-desktop:~$ sudo chmod a+w /dev/bus/usb/001/005
Password:
ammmom@ammmom-desktop:~$

---

### Post by wmichaelb on 2007-05-23
Ammon: I faced this same problem with Dapper, and learned that the problem is that Xsane will not recognize many HP scanners, including this one. The TWAIN driver is not standard because of the way the scanner is designed. See [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html). Unfortunately, I know of no way out of this one other than another scanner that is supported.

---

### Post by diddler on 2007-05-26
I have a Scanjet 4470c which oddly enough is not listed at all on the xsane site as being either supported OR unsupported.  I have to guess it's unsupported because it doesn't show up in the xsane window.  Boy, I am getting sorry I removed XP from my system.  It seems that every day Linux shows itself less and less capable, BUT there is no going back to Microcrap! 

Is xsane the ONLY way to get scanners to work with Ubuntu?

---

### Post by ammmom on 2007-05-27
> **wmichaelb said:**
> Ammon: I faced this same problem with Dapper, and learned that the problem is that Xsane will not recognize many HP scanners, including this one. The TWAIN driver is not standard because of the way the scanner is designed. See [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html). Unfortunately, I know of no way out of this one other than another scanner that is supported.
thanks Michael.  I gave up on my home HP scanner and gave it away.  I have another HP and a fujitsu scansnap s500 in my office.  Hopefully, I'll be able to set up a dual boot there.  I've read that the scansnap works with Ubuntu [http://www.sane-project.org/man/sane-fujitsu.5.html]("http://www.sane-project.org/man/sane-fujitsu.5.html") I really *love* the scansnap so if I can get that working I'll be happy.

---

