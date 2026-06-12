---
title: "Compiling Drivers"
date: 2015-01-31
forum: Hardware
---

### Post by snares on 2015-01-31
I have a Ceton Infinitv 6 Tuner card I need to compile drivers for. I run the make command and the errors start flying. Not sure what will resolve this. 

```
 CC [M]  /home/g-rock/Downloads/ceton_infinitv_linux_driver/ctn91xx_reset.o
/home/g-rock/Downloads/ceton_infinitv_linux_driver/ctn91xx_driver.c: In function ‘ctn91xx_print_compilation’:
/home/g-rock/Downloads/ceton_infinitv_linux_driver/ctn91xx_driver.c:17:1: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
     INFO("driver compiled at %s on %s", __TIME__, __DATE__);
 ^
/home/g-rock/Downloads/ceton_infinitv_linux_driver/ctn91xx_driver.c:17:1: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/g-rock/Downloads/ceton_infinitv_linux_driver/ctn91xx_driver.o' failed
make[2]: *** [/home/g-rock/Downloads/ceton_infinitv_linux_driver/ctn91xx_driver.o] Error 1
make[2]: *** Waiting for unfinished jobs....
Makefile:1345: recipe for target '_module_/home/g-rock/Downloads/ceton_infinitv_linux_driver' failed
make[1]: *** [_module_/home/g-rock/Downloads/ceton_infinitv_linux_driver] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-30-generic'
Makefile:38: recipe for target 'ctn91xx_module' failed
make: *** [ctn91xx_module] Error 2

```

this is after the make command is run. THe README file says all I need is make, gcc, perl, kernel-devel and kernel-headers; which, as near as I can tell, I have installed. Any guidance would be appreciated. Thank yo.

---

### Post by computermaster1 on 2015-02-15
I had the same problem, here is how i solved it:

It turns out the driver you get from cetons website was last complied in 2013 but if you goto the github page they made it is up to date and compiles properly,

1. goto [https://github.com/ceton/infinitv_pcie](https://github.com/ceton/infinitv_pcie) and download the master zip
2. unzip the files to the same directory you unzipped the one from ceton make sure to OVERWRITE all the files with the ones from github
3. install as in the readme file

---

### Post by snares on 2015-05-30
I gave up in February and then MS announced they were going to be stopping support for MediaCenter so I decided better to get it working now rather than later. I tried what you said and it work perfectly. Really all you need to do is download the github zip unzip and the follow the README, Thank you for the help!

---

