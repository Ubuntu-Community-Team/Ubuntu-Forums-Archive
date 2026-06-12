---
title: "GLX Failure"
date: 2011-10-19
forum: Hardware
---

### Post by Ra'anan on 2011-10-19
Hi,

when I run glxgears I get the same output. It was working earlier :s

glxinfo | grep render
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  17
  Current serial number in output stream:  17

Anyone know how I can sort this out?

---

### Post by hwertz on 2011-10-19
"Me too".  I am running Ubuntu 10.10 on a Dell mini with a Poulsbo.  I am using the GMA500 PPA from ppa:gma500/ppa .  I tried running Secondlife and got the same error -- generally, SL has either not run or run too slow on here anyway, but I try now and then.  OK, fair enough.  So then just like OP, well,....
hwertz@rocketmower:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  18
  Current serial number in output stream:  18

     I just reinstalled all glx, mesa, and psb packages, just in case some package misinstalled.  No dice.:lolflag:

---

### Post by hwertz on 2011-10-24
FYI, the update I installed October 22nds updated xserver-xorg-core, OpenGL stuff now works again.  The ChangeLog says "debian/patches/212_CVE-2010-4818.patch: updated with missing commit to fix regression."  I guess this was at least one symptom of that regression.  Works now! :D

---

