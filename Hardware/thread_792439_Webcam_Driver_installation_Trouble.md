---
title: "Webcam Driver installation Trouble"
date: 2008-05-12
forum: Hardware
---

### Post by dlawler on 2008-05-12
When i go to install the driver directly from the folder i get errors.
i'll list the entire terminal session so you can see what's up:

daniel@daniel-laptop:~/Desktop$ cd /home/daniel/r5u870-0.11.0/
daniel@daniel-laptop:~/r5u870-0.11.0$ sudo make && make install
make -C /lib/modules/2.6.22-14-generic/build M=/home/daniel/r5u870-0.11.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 2 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make -C /lib/modules/2.6.22-14-generic/build M=/home/daniel/r5u870-0.11.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 2 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=extra \
                -C /lib/modules/2.6.22-14-generic/build M=/home/daniel/r5u870-0.11.0 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [install] Error 2
daniel@daniel-laptop:~/r5u870-0.11.0$

---

### Post by hermes0710 on 2008-05-13
Try 
```

sudo make
sudo make install

```

---

