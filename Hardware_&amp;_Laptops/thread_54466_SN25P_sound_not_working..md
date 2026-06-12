---
title: "SN25P sound not working."
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by duran on 2005-08-04
I tried to perform a fix as mentioned in: 

[http://www.ubuntuforums.org/showthread.php?t=27155&highlight=sn25p+sound](http://www.ubuntuforums.org/showthread.php?t=27155&highlight=sn25p+sound) 

but when I get to the 'sudo make' command, I get a lot of errors toward the end.  All this means to me is that there's some syntax error in vt1720_mobo.c.  Is that what it means, and where do I start?  Thanks for any help.

Here's a snip of what I get:

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
CC [M]  /usr/src/alsa-driver-1.0.9rc4a/pci/ice1712/vt1720_mobo.o
In file included from /usr/src/alsa-driver-1.0.9rc4a/pci/ice1712/vt1720_mobo.c:2 :
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:114: error:  syntax error at '#' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:114: error:  syntax error before ';' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:115: error:  syntax error at '#' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:115: error:  invalid lvalue in unary `&'
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:115: error:  initializer element is not constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:115: error:  (near initialization for `snd_vt1720_mobo_cards[4].name')
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:115: error:  syntax error before ';' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:115: error:  syntax error at '#' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:117: error:  `k8' undeclared here (not in a function)
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:117: error:  syntax error at '#' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:117: error:  initializer element is not constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:117: error:  (near initialization for `snd_vt1720_mobo_cards[4].chip_init')
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:117: error:  syntax error before ';' token
In file included from /usr/src/alsa-driver-1.0.9rc4a/pci/ice1712/vt1720_mobo.c:2 :
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:117:38: inv alid suffix "_init" on integer constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:118: error:  `k8' undeclared here (not in a function)
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:118: error:  syntax error at '#' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:118: error:  initializer element is not constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:118: error:  (near initialization for `snd_vt1720_mobo_cards[4].build_controls')
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:118: error:  syntax error before ';' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:118:43: inv alid suffix "_add_controls" on integer constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:119: error:  `k8' undeclared here (not in a function)
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:119: error:  syntax error at '#' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:119: error:  syntax error before ';' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:119:47: inv alid suffix "_eeprom" on integer constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:120: error:  `k8' undeclared here (not in a function)
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:120: error:  syntax error at '#' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:120: error:  initializer element is not constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:120: error:  (near initialization for `snd_vt1720_mobo_cards[4].eeprom_data')
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:120: error:  syntax error before ';' token
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:120:40: inv alid suffix "_eeprom" on integer constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:121: error:  initializer element is not constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:121: error:  (near initialization for `snd_vt1720_mobo_cards[4]')
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:122: error:  initializer element is not constant
/usr/src/alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712/vt1720_mobo.c:122: error:  (near initialization for `snd_vt1720_mobo_cards[5]')
make[4]: *** [/usr/src/alsa-driver-1.0.9rc4a/pci/ice1712/vt1720_mobo.o] Error 1
make[3]: *** [/usr/src/alsa-driver-1.0.9rc4a/pci/ice1712] Error 2
make[2]: *** [/usr/src/alsa-driver-1.0.9rc4a/pci] Error 2
make[1]: *** [_module_/usr/src/alsa-driver-1.0.9rc4a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [compile] Error 2

```

---

### Post by losing.virginia on 2005-08-07
I get the same thing. Anyone who can help?

---

