---
title: "Catalyst Hybrid graphics installation issues"
date: 2011-09-25
forum: Hardware
---

### Post by iofthestorm on 2011-09-25
I've got an HP Envy 14-1000 laptop with both Intel HD (Core i5 integrated, non Sandy Bridge) graphics and ATI Radeon 5650. For the longest time, switchable graphics drivers did not exist but according to the release notes, Catalyst 11.5 for Linux added support for switchable graphics. In July, I was on Ubuntu 10.10 amd64 and installed Catalyst 11.6, and switchable graphics worked more or less perfectly. Then I had some issues with some programs so I decided to try upgrading to 11.8, and since then I've been unable to get it to work at all. Right now I'm on a fairly fresh install of 11.04, and I'm trying to install fglrx again. I think the issue lies with alternatives somehow but I'm not sure exactly what the issue is. I'm going to paste some logs here for record so that hopefully someone can help me figure it out, or in the case that I figure it out it's documented.

```
$ sudo dpkg -i *.deb
Selecting previously deselected package fglrx.
(Reading database ... 252691 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.881-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.881-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.881-0ubuntu1_amd64.deb) ...
Setting up fglrx (2:8.881-0ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/mesa/ld.so.conf because link group gl_conf is broken.
Loading new fglrx-8.881 DKMS files...
Building only for 2.6.38-11-generic
Building for architecture x86_64
Building initial module for 2.6.38-11-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-11-generic/updates/dkms/

depmod........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.881-0ubuntu1) ...
Setting up fglrx-dev (2:8.881-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

```

Going to reboot again, see if it works. Will post back with results. If not, has anyone been able to get switchable Intel/ATI graphics to work on 11.04 or 10.10 or even 10.04? Thanks!

Edit: To clarify, I was using the instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) with no luck.

On a whim I tried letting the ATI installer run instead of just generating debs and amazingly, it worked. So maybe other people with hybrid graphics who are having issues should try this instead of making debs. I think basically this installation method will break each time you upgrade your kernel, but as long as it works for now I'm happy.

---

### Post by fuern on 2011-10-04
Cool. Any idea if this will work on the oneiric 11.10 beta?

---

### Post by mordanda on 2011-10-10
I would also be interested if anyone is reporting success with the ATI installer in 11.10 64-bit.  I've been unable to get either fglrx or vgaswitcheroo working in the beta.  I've been able to get both switching methods up and running in previous versions of Ubuntu.

If you can report success can you give us a quick step by step?

Dan

---

