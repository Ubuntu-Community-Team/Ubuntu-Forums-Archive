---
title: "compiz with sandy bridge vga on lucid (10.04)"
date: 2011-08-09
forum: Hardware
---

### Post by alfred11 on 2011-08-09
hello,
i have the task to get compiz running on dell optiplexx 990 with intel sandy bridge chipset on ubuntu 10.04 lucid lynx.

the problem:
if i run "compiz" in the terminal i get the following error:

```

Unrecognized deviceID 102
compiz (core) - Fatal: No valid GL extensions string found.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
Launching fallback window manager

```

i run at least kernel linux-image-generic-lts-backport-maverick                            2.6.35.25.36 to get the NIC working.

initially the Xorg.log.0 says (warnings / errors):
```

II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(WW) intel(0): Disabling Xv because no adaptors could be initialized.

(II) intel(0): Initializing HW Cursor
(EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.

```

the first thing i did was updating the intel driver with the ppa from stefan glasenhardt: [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

after updating the intel driver my Xorg.log.0 looked much better
```

(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"

```

for tests i installed linux-image-generic-lts-backport-natty  2.6.38-10.46~lucid1 but the warnings stay the same and compiz still does not work.

lspci output
```

root@localhost:/var/log# lspci -nn | grep -i vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0102] (rev 09)

```

the whole Xorg.log.0 can be found on [http://nopaste.info/8b953ee124.html](http://nopaste.info/8b953ee124.html)


does anybody have any idea to get this working?

thanks
alfred

---

### Post by alfred11 on 2011-08-22
hello,
stefan glasen told me that also a backport of mesa is required. he did that and the files are available on launchpad

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

it works with kernel 2.6.38 which is available in ubuntu-updates reopository

regards
alfred

---

