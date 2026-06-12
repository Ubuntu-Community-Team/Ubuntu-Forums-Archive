---
title: "Installing GrSecurity"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by ph8 on 2006-01-21
Hi there,

I'm trying to install grsecurity, I grabbed the gradm2 package which installed the kernel-patch-grsec2 package - I don't know where to go from here! I rebooted but uname -a doesn't reveal a grsec'd kernel!

All help appreciated.

ph8

---

### Post by revellion on 2006-12-25
The easiest way i've found to build a GRSecurity powered Ubuntu system has been as follows

```

-- Grab the latest patches at grsec site.

-- Grab the matching linux-kernel source from www.kernel.org

Unpack the kernel.org kernel

-- Environment ~/build

tar xvjf linux-x.x.x.y

cd linux-x.x.x.y

cp ../grsecurity-*****.gz .

gunzip grsecurity-*****

patch -p1 < grsecurity-*****

cp /boot/config-`uname -r` .config

make

make install

make modules_install

mkinitramfs -o /boot/initrd.img-x.x.x.y-grsec x.x.x.y-grsec

-- Edit GRUB Menu.lst as appropriate.

nano /boot/grub/menu.lst

-- Reboot into the -grsec kernel

-- Install gradm2 tools from the grsec site. (recommended above the in repository gradm2 which is a bit dated (2.1.8 versus GRSEC site 2.1.9)


```

---

### Post by boogachamp on 2007-05-30
Has anyone else tried this?

---

### Post by mrf76 on 2008-02-12
I just try suggested method and it's working (almost ;-)). I was building 2.6.23.14-grsec kernel and some external SCSI storage was not recognize after reboot. Probably something wrong only in my kernel config. 

BTW: This latest kernel bug in vmslice GRSEC wont stop anyway:

[http://www.milw0rm.com/exploits/5092](http://www.milw0rm.com/exploits/5092)

---
Ubuntu 7.10 Gutsy Server: 2.6.22-14-server

---

### Post by pipes on 2008-02-13
A potential easier option may be to use the cr0 kernel security packages (which include protection for the vmsplice bug: 

[http://kernelsec.cr0.org/](http://kernelsec.cr0.org/)


> **revellion said:**
> The easiest way i've found to build a GRSecurity powered Ubuntu system has been as follows

```

<snip>
cp /boot/config-`uname -r` .config

make

make install

make modules_install
<snip>

```

Uh, you may wish to run make menuconfig to ensure that GRSEC is actually enabled :) 

If you are confused at which settings to use refer to the docs here: 

[http://grsecurity.net/quickstart.pdf](http://grsecurity.net/quickstart.pdf)

---

