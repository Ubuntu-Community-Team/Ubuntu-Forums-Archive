---
title: "internal hard drive fails to mount"
date: 2012-01-26
forum: Hardware
---

### Post by shmibs on 2012-01-26
while doing common place tasks, the hard drive in my laptop suddenly stopped responding. applications already open conitnued to run, but anything that tried to access the hard drive started to hang indefinitely. i rebooted, and was taken immediately to a message saying that the hard drive was not found. rebooting again took me to the grub menu, and trying to boot any kernel revisions from there yielded the same result.

i started up a mint 10 live usb, and can see the 160 GB Hard Disk: 154 GB Filesystem, but trying to mount it gives an "Error creating mountpoint: input/output error"

i tried starting up gparted, but for some reason it won't run:
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

now what?

---

### Post by wolfen69 on 2012-01-26
While in grub, go to system recovery, then repair. It sounds like something borked your system big time.

---

