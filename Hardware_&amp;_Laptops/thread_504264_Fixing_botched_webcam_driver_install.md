---
title: "Fixing botched webcam driver install?"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by PaganHippie on 2007-07-18
I just bought an inexpensive Pixart web cam, and am trying to use easycam2 to install the driver (running Ubuntu 7.04 on a Pentium 4).  It recognises the cam, runs all the way through the install and then gives me an error message (in French!) to the effect that *make install* failed, while in my terminal window I get:

> angus@talisker:~$ lauchcam2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libgstreamer0.8-0 libmetakit2.4.9.3c2 python-imaging python-metakit
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ln: creating symbolic link `/lib/modules/2.6.20-16-generic/build/linux-headers-2.6.20-16-generic' to `/usr/src/linux-headers-2.6.20-16-generic': File exists
ERROR: Module spca5xx does not exist in /proc/modules
mkdir: cannot create directory `/lib/modules/2.6.20-16-generic/kernel/drivers/usb/media-back': File exists
mknod: `/dev/video0': File exists
mknod: `/dev/video1': File exists
ln: creating symbolic link `/dev/video' to `/dev/video0': File exists
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
        drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
mkdir -p /lib/modules/2.6.20-16-generic/kernel/drivers/usb/media/
rm -f /lib/modules/2.6.20-16-generic/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/2.6.20-16-generic/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/2.6.20-16-generic/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory
make: *** [install] Error 1
angus@talisker:~$ 


What I know about *make* would fit in a matchbox without taking the matches out first, but it looks to me like /proc/modules is supposed to be a directory; looking in /proc shows that it is in fact a file, and an empty file at that.

My questions are:  what have I done wrong, and how can I fix it?

---

### Post by paulphillips on 2007-07-19
I could be wrong, but this is my analysis...

/proc/modules simply shows what kernel modules (hardware drivers) are loaded on your system.  Its saying that spca5xx is not there.  I don't know anything about launchcam2 or easycam2, so not sure how it works.

I presume spca5xx corresponds to your webcam hardware?

The last error is saying that it can't find the kernel module file to copy into your kernel module area.  Has it been built (compiled?) yet?  Maybe search launchcam or easycam in forums.

---

### Post by PaganHippie on 2007-07-19
Thanks for the reply.

From what I can tell watching the output of *easycam* in the terminal window while it's running, it's supposed to build and then install the appropriate webcam driver.  The build part seems to go OK, but the install chokes as described above.

I'll keep looking.  Lot of trouble for a $10 webcam, I must say.  :frown:

---

### Post by medya on 2007-07-22
I have exactly the same problem ... would somebody help us ?

---

### Post by paulphillips on 2007-07-22
You say it's built the kernel module file ("*.ko")  - if you can locate it, perhaps you could try manually copying it across to the location specified in your log file?

---

### Post by PaganHippie on 2007-07-23
Sounds like it's worth a try.  I'll let you know.

---

### Post by medya on 2007-07-23
what do u mean paulphilips ?

---

### Post by PaganHippie on 2007-07-28
Upon further examination, it seems that the error was actually in *make* rather than *make install* after all, so the module spca5xx.ko was never created in the first place.  :frown:  So...

I don't suppose anyone knows how to build the module in question by hand?  I'm not afraid of the command line and have certainly compiled source code before.  Alternately, if anyone has successfully created this module under feisty and could send me a copy, I'm sure I could find a way to shoe-horn it into the right location and get this cam working.

Anyone?

---

