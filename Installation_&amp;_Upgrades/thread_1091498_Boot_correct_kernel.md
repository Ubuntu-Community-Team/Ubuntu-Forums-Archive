---
title: "Boot correct kernel"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by dragoslav_zaric on 2009-03-09
Hello,

I had generic kernel 2.6.27-7 and it worked fine. Then I installed
2.6.28 that had errors during
install, but system anyway booted to 2.6.28. When I did apt-get
install of some app in this bad
2.6.28 kernel I got error messages that something is wrong. So I
entered boot menu and booted
to old 2.6.27-7 kernel and when I tried to do apt-get install of some
app, the system again looked at
2.6.28 like current kernel !!

So I looked where does files of current kernel are copied and there
are few folders (files):
/boot/vmlinuz*VERSION*
/boot/initrd*VERSION*
/boot/System-map*VERSION*
/boot/config-*VERSION*
/lib/modules
and also menu list in /boot/grub/menu.lst

So, when you have more kernels, let's say 4 working and one bad
kernel, when the system
boots selected kernel, should the system copy all files from selected
kernel to all places where
current running system kernel should be ?? That way you will always
have correct kernel running
whole system, and all installed modules for that kernel could be
loaded looking at modinfo of modules
or modules could be sorted into folders for each kernel version.

greet

---

### Post by Neo_The_User on 2009-03-09
Can you sum that up for me? I don't understand.

---

### Post by dragoslav_zaric on 2009-03-09
Ok,

I installed bad kernel and I wanted to get back to old so I pressed escape during the boot and select old good generic kernel. But when I wanted to install something with apt-get install, the system tried to install application in bad kernel, even though I booted into good generic kernel.

OK ?

---

### Post by Neo_The_User on 2009-03-09
Oh I get it. Try installing DKMS.

```

sudo apt-get install dkms

```

Restart your computer and whatever was installed in the bad kernel would be automatically built for all the other kernels (on start-up)

---

### Post by dragoslav_zaric on 2009-03-09
I already have dkms installed,

thanks anyway :)

---

### Post by Neo_The_User on 2009-03-09
eh I'm the wrong guy to ask. Sorry.

---

