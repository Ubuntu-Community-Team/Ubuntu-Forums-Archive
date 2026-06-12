---
title: "What kernel modules??"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by kubuntu2k6 on 2006-03-12
Hey! wanted to setup an initrd on my BOOT partition, to initialize the encrypted ROOT partition/filesystem on boot. So created one and copied over all the needed binaries and libs, script, created devices etc... Using the modular ubuntu kernel, obviously need to copy some kernel modules to the initrd. This is where things get messed up when it comes to ext3. I've copied all ide, ext3, and jbd modules I could find to the initrd, still it spits out lots of ext3 errors at boot like this one...

4294670.206000 ext3: Unknown symbol *
modprobe: FATAL: Error inserting ext3
Unknown symbol in module or unknown parameter.

Then when trying to mount I get the error:
mount: ... type ext3 not supported

Any ideas what kernel modules is needed, that I might have missed? Thanks.

---

