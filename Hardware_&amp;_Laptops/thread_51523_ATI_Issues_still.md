---
title: "ATI Issues still"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by tbasten on 2005-07-24
](*,) 

Ok, i still cant get glx working for ii. Something like that. Like i would like to get direct rendering working. I do glxgears and i get 90fps. i do fgl_gears and i get the following

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32

```

---

### Post by tbasten on 2005-07-24
```
tbasten@Dyna:~ $ glxinfo | grep 'rendering'
direct rendering: No

```

Um anything need to help assist in the solving of my problem

---

### Post by tbasten on 2005-07-24
```
tbasten@Dyna:~ $ grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

```
tbasten@Dyna:~ $ grep EE /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): DRIScreenInit failed!
```

For the full log file, [here](http://www.geocities.com/basten11285/Xorg.0.log) it is

#edit - Stuffed link up

---

