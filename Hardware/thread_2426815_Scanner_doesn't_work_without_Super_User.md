---
title: "Scanner doesn't work without Super User"
date: 2019-09-13
forum: Hardware
---

### Post by Hyenaz on 2019-09-13
Hello

I am using the program Vuescan to access a scanner that otherwise is not suppoted in Ubuntu - the Canon G2501.

I can only scan if I run the program Vuescan as super user.

If I run without elevated privileges I get an error message

 6) If you have a USB scanner, try running VueScan as root to see if it's a libusb device protection problem.

I don't know how to resolve this. I know I have to edit /lib/udev/rules.d/60-libsane.rules but I don't know how.

Can anyone help me, and save this scanner from becoming e-waste?

Thank you!

---

### Post by TheFu on 2019-09-14
I don't know that specific program or device, but running a program with sudo will often break permissions for config files, which will make it require running with sudo forever until those permissions are fixed.

It was likely a simple Unix file permissions issue that has been made worse now.  With my scanners, I usually just add my userid to the same group that the scanner uses (sane) to access the scanner device file in /dev/, logout/login (to get a fresh session), and any scanning program can be used from that point on.

---

