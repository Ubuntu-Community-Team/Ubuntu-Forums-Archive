---
title: "Installing on a different partition"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by tibasic on 2009-06-01
Hey Everyone,

How can I install an application onto another partition and run it from there?

What do I mean?
Ok, just for kicks, let say I have "/dev/sda1" mounted to "/"
"/dev/sda2" is mounted to "/partition2"

Would I use "dpkg --instdir=/partition2 -i myProgram.deb"?

Also I'm assuming to run this program I would have to run:
"/partition2/bin/myProgram.sh"

I would like to be able to install programs onto an usb drive so I can just stick my drive into any computer and run a program without have to install, run it, uninstall, etc...

(I know that /dev/sda2 is not by any means a usb device)

---

### Post by tibasic on 2009-06-01
No one?

---

### Post by mcduck on 2009-06-02
Sorry, that won't work as programs aren't installed into any single directory in Linux.

Different components go to different directories based on the purpose of those files, for example icons & graphics go to /usr/share/pixmaps and /usr/share/icons, executable files to /usr/share/bin, documentation to /usr/share/doc and so on.

---

### Post by tibasic on 2009-06-03
Is there such a thing as a portable executable on Linux?

On Mac pretty much any .app file can run from anywhere on the system.
On Windows things can be installed onto remote drives and run.

Is there no equivalent to this on Linux?

---

### Post by linux_tech on 2009-06-03
To compile c code in linux, install the GNU compiler and several other utilities for compiling sources, use:
```
sudo aptitude install build-essential
```

Then use use gcc to compile your code from a command line or if you want to cross compile then try cygwin

---

### Post by mcduck on 2009-06-03
> **tibasic said:**
> Is there such a thing as a portable executable on Linux?

On Mac pretty much any .app file can run from anywhere on the system.
On Windows things can be installed onto remote drives and run.

Is there no equivalent to this on Linux?

Some distributions (Slax, for example) use packages like that, most don't because that wastes a lot of disk space and resources.

---

