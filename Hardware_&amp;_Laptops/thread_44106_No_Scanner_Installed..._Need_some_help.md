---
title: "No Scanner Installed... Need some help"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by sonny on 2005-06-24
Hi, I have a Scanjet 3570c scanner, it is listed when a do lsusb, but it's not when I list with xsane, I've search the HP webpage but there's no firmware or software for Linux. Can anyone help me?, I don't know what else you have to know but let me know and I'll paste the results... Tanks in advance.

---

### Post by kleeman on 2005-06-24
It might be a permissions issue. Can you run it with "sudo xsane"?

If so see this howto:

Information about USB scanners:
================================

With Linux 2.4.* you could either use the kernel scanner module or libusb to
access USB scanners.  In Linux 2.6.4 the kernel scanner module was removed.
Therefore with this and later kernels libusb must be used.

While SANE automatically uses libusb when the library and its header file were
present during the build of sane-backends, setting permissions will require some
attention. So if scanimage -L lists your scanner as root but not as normal user
read on this text.

The device files used by libusb are located in /proc/bus/usb/
(e.g. /proc/bus/usb/001/003).  The exact file name can be found out by running
sane-find-scanner which would print "libusb:001:003" in this case.  While
setting permissions with e.g. "chmod a+rw /proc/bus/usb/001/003" works,
this change is not permanent.  The permissions will be reset when the scanner is
replugged or Linux is rebooted.

One solution to set permissions on-the-fly are the Linux hot-plug tools that
should come with any current distribution. Your distribution should have set up
the scripts to automatically change permissions correctly. Look for
"libsane.usermap" and "libusbscanner" in /etc/hotplug/usb. Usually you must just
add the users that are allowed to access the scanner to group "scanner". To make
that change active, the user must login again. For more details, see your
distribution's documentation e.g. for Debian: README.debian.gz.

---

