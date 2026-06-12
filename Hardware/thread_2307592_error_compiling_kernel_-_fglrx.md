---
title: "error compiling kernel - fglrx"
date: 2015-12-26
forum: Hardware
---

### Post by fede91 on 2015-12-26
hi to all, I'm stuck on a problem for days.

I've a wacom tablet and I had problem making it working. I had to resolved by patching a kernel with this patch: 

[URL="https://lkml.org/lkml/2015/11/20/690"]https://lkml.org/lkml/2015/11/20/690

[/URL]and installing the last version of input-wacom version 0.30.1

Now the tablet is working fine but I've problem with ati drivers.

I explain: while compiling the kernel I had this error:

```

ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/fglrx-core.0.crash'
Error! Bad return status for module build on kernel: 3.18.25 (x86_64)
```

fglrxinfo:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

I've tried purging and reinstalling the drivers.

sudo amdconfig --initial:

```
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-3

```

I've used both drivers from ubuntu center and the packages downloaded from the amd site.

If i try to use the xorg drivers all is working except the fact that the resolution of the display is lock at 1204X768

My system spec:

packard bell easynote tj75 with 8gb of ram

ATI mobile HD5470

The graphic tablet is a wacom ctl490dw (wacom intuos draw).

Kernel tried:

4.4 (working tablet but not fglrx)
4.2 (working talbet but not fglrx and usb mouse)
3.18.25 (working tablet but not fglrx)

I don't know what to try next

To note: if I use a not patched kernel it result in this bug:

[http://sourceforge.net/p/linuxwacom/mailman/message/34655931/](http://sourceforge.net/p/linuxwacom/mailman/message/34655931/)

---

