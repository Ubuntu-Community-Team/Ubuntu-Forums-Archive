---
title: "cannot compile fglrx"
date: 2008-07-22
forum: General Help
---

### Post by KOTAPAKA on 2008-07-22
```
dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
		cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
	fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
		mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.25.10sim.postinst; \
	fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /usr/src/linux-headers-2.6.25.10sim SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.25.10sim'
/usr/src/linux-headers-2.6.25.10sim/arch/x86/Makefile:41: /usr/src/linux-headers-2.6.25.10sim/arch/x86/Makefile_32.cpu: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.25.10sim/arch/x86/Makefile_32.cpu'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25.10sim'
make: *** [build] Error 2

```
This is the output. I have no idea what can be wrong. It went ok with the kernel from the repoes but with my custom kernel compiling fails. I do it with module-assistant. Any ideas what I might have turned off in the kernel?

---

### Post by ajgreeny on 2008-07-22
Not that I fully understand this compiling business, but have you installed the package** build-essentials**?

---

### Post by chalewa on 2008-07-22
yea what are you trying to compile?


if you are trying to build the new 8.7 packages, there should be no compiling required...

---

### Post by KOTAPAKA on 2008-07-24
Why? I just installed the 8.7 one and I did compile the fglrx module.

---

### Post by danwood76 on 2008-07-24
You do compile a kernel module in the install.

There are probably compatibility issues with building it with the 2.6.25 kernel as they are normally quite slow to keep up with kernel releases (theres only a couple of people who actually work on fglrx)

Why are you using 2.6.25 anyway? the stable 2.6.26 is out if you are really cutting edge.

---

### Post by KOTAPAKA on 2008-07-24
Well when I compiled mine the latest stable was 2.6.25-10. So what now? I have the .config for my old kernel. Can I use it for the new 2.6.26 compile?

---

### Post by danwood76 on 2008-07-24
Yeah, when you import the config it will ask you qestions about all the new features added.
Or if doing the Xconfig will dump all the differnces to the terminal.

The question is why are you using the 2.6.25 and not the default ubuntu one?
Fglrx only officially supports up to 2.6.24 so you may have trouble getting it to work with later versions than that.

---

