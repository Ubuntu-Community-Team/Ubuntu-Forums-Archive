---
title: "TouchPad tab gone after update (ubuntu 12.04)"
date: 2013-11-08
forum: Hardware
---

### Post by abdorefky on 2013-11-08
TouchPad tab gone after update . i have ubuntu 12.04 
i am using Dell inspiron 5520 . the touchpad was working just fine . 
**xinput list : **
```
abdo@ABDO:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys
```

---

### Post by abdorefky on 2013-11-09
any help ?? this caused by Ubuntu updates .

---

### Post by abdorefky on 2013-11-10
```
abdo@ABDO:/$ sudo dkms build -m psmouse-alps -v 1.3

Creating symlink /var/lib/dkms/psmouse-alps/1.3/source ->
                 /usr/src/psmouse-alps-1.3

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.5.0-43-generic -C /lib/modules/3.5.0-43-generic/build M=/var/lib/dkms/psmouse/alps-1.3/build/src psmouse.ko....(bad exit status: 2)
ERROR (dkms apport): binary package for psmouse-alps: 1.3 not found
Error! Bad return status for module build on kernel: 3.5.0-43-generic (x86_64)
Consult /var/lib/dkms/psmouse-alps/1.3/build/make.log for more information.


```


make.log
```
DKMS make.log for psmouse-alps-1.3 for kernel 3.5.0-43-generic (x86_64)
Sun Nov 10 15:17:36 EET 2013
make: Entering directory `/usr/src/linux-headers-3.5.0-43-generic'
scripts/Makefile.build:44: /var/lib/dkms/psmouse/alps-1.3/build/src/Makefile: No such file or directory
make[1]: *** No rule to make target `/var/lib/dkms/psmouse/alps-1.3/build/src/Makefile'.  Stop.
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-3.5.0-43-generic'

```

---

### Post by abdorefky on 2013-11-10
i tried that too 

```

abdo@ABDO:/usr/src/psmouse-alps-1.3$ sudo bash ./alps.sh dkms_build_alps
Must run dkms_install_cp or dkms_install_symlink before this
/usr/src/psmouse-alps-1.3/dkms.conf must have PACKAGE_VERSION set to alps-1.3

------------------------------
Deleting module version: alps-1.3
completely from the DKMS tree.
------------------------------
Done.
/usr/src/psmouse-alps-1.3/dkms.conf must have PACKAGE_VERSION set to alps-1.3
This places the psmouse.ko dlkm in /lib/modules/3.5.0-43-generic/updates/dkms

Creating symlink /var/lib/dkms/psmouse/alps-1.3/source ->
                 /usr/src/psmouse-alps-1.3

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.5.0-43-generic -C /lib/modules/3.5.0-43-generic/build M=/var/lib/dkms/psmouse/alps-1.3/build/src psmouse.ko.....(bad exit status: 2)
ERROR (dkms apport): binary package for psmouse: alps-1.3 not found
Error! Bad return status for module build on kernel: 3.5.0-43-generic (x86_64)
Consult /var/lib/dkms/psmouse/alps-1.3/build/make.log for more information.
Build failed
DKMS make.log for psmouse-alps-1.3 for kernel 3.5.0-43-generic (x86_64)
Sun Nov 10 15:40:45 EET 2013
make: Entering directory `/usr/src/linux-headers-3.5.0-43-generic'
  CC [M]  /var/lib/dkms/psmouse/alps-1.3/build/src/psmouse-base.o
  CC [M]  /var/lib/dkms/psmouse/alps-1.3/build/src/synaptics.o
  CC [M]  /var/lib/dkms/psmouse/alps-1.3/build/src/alps.o
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:136:32: error: ‘ALPS_PROTO_V6’ undeclared here (not in a function)
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_process_packet_v1_v2’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:191:44: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_process_bitmap’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:347:3: warning: left shift count >= width of type [enabled by default]
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_process_packet’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:827:44: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_handle_interleaved_ps2’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:898:38: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_process_byte’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:979:44: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_poll’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:1365:10: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:1371:10: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:1374:35: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:1374:54: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_hw_init_v1_v2’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:1392:44: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_hw_init’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:1859:44: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c: In function ‘alps_init’:
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:1925:6: error: ‘struct alps_data’ has no member named ‘i’
/var/lib/dkms/psmouse/alps-1.3/build/src/alps.c:1925:2: warning: statement with no effect [-Wunused-value]
make[1]: *** [/var/lib/dkms/psmouse/alps-1.3/build/src/alps.o] Error 1
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-3.5.0-43-generic'


```

---

### Post by abdorefky on 2013-11-10
this version looks older , installing working but no touchpad tab 

```
abdo@ABDO:~$ cd /usr/src/psmouse-alps-dst-0.4/
abdo@ABDO:/usr/src/psmouse-alps-dst-0.4$ sudo bash ./install.sh
[sudo] password for abdo: 
MAIN: Driver source files by Dave Turvene. Install script by garyF.
MAIN: Removing previous versions of psmouse-alps-dst...
Error! There are no instances of module: psmouse
alps-dst-0.4 located in the DKMS tree.
MAIN: Building current driver from source files...

Creating symlink /var/lib/dkms/psmouse/alps-dst-0.4/source ->
                 /usr/src/psmouse-alps-dst-0.4

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.5.0-43-generic -C /lib/modules/3.5.0-43-generic/build M=/var/lib/dkms/psmouse/alps-dst-0.4/build/src psmouse.ko.....
cleaning build area....

DKMS: build completed.
MAIN: Installing the driver

psmouse:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.5.0-43-generic/updates/dkms/

depmod.......

DKMS: install completed.
rmmod psmouse, wait=no
insmod /lib/modules/3.5.0-43-generic/updates/dkms/psmouse.ko proto=imps 
MAIN: Done installing. Go to System Settings > Mouse and Touchpad to configure :-)
```

---

### Post by abdorefky on 2013-11-10
i tried that code too .. i dont understand any of this 
```
abdo@ABDO:~$ sudo dkms remove psmouse/alps-dst-0.4 --all
[sudo] password for abdo: 

-------- Uninstall Beginning --------
Module:  psmouse
Version: alps-dst-0.4
Kernel:  3.5.0-43-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

psmouse.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-43-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: alps-dst-0.4
completely from the DKMS tree.
------------------------------
Done.
abdo@ABDO:~$ sudo dkms build psmouse/alps-dst-0.4

Creating symlink /var/lib/dkms/psmouse/alps-dst-0.4/source ->
                 /usr/src/psmouse-alps-dst-0.4

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.5.0-43-generic -C /lib/modules/3.5.0-43-generic/build M=/var/lib/dkms/psmouse/alps-dst-0.4/build/src psmouse.ko.....
cleaning build area....

DKMS: build completed.
abdo@ABDO:~$ sudo dkms install psmouse/alps-dst-0.4

psmouse:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.5.0-43-generic/updates/dkms/

depmod....

DKMS: install completed.
abdo@ABDO:~$ sudo rmmod psmouse && sudo modprobe -v psmouse
insmod /lib/modules/3.5.0-43-generic/updates/dkms/psmouse.ko proto=imps 
abdo@ABDO:~$

```

---

### Post by abdorefky on 2013-11-10
Solved finaly .... 


> 
Finally got it working! Its beautiful I want to cry :smile:

The 2nd Gen Series 9 13" X3C uses the Elantech Touchpad which has always  been incorrectly reconized as a PS/2 Mouse, after a lot of reading I  have finally managed to fix by doing the following:

1. Plug in a USB mouse.

2. Remove any /etc/modprobe.d/psmouse.conf, /etc/modprobe.d/psmouse.modprobe stuff you might have done.

3. Install the driver:

 	Code:
 	cd /usr/src/
sudo wget [http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2](http://planet76.com/drivers/elantech/psmouse-elantech-v6.tar.bz2)
sudo tar jxvf psmouse-elantech-v6.tar.bz2
sudo dkms add -m psmouse -v elantech-v6
sudo dkms build -m psmouse -v elantech-v6
sudo dkms install -m psmouse -v elantech-v6 
4. Reboot, move your trackpad around till it the cursor moves.

5. Check your input list:
 	Code:
 	xinput list 



QUOTE from : 
[http://ubuntuforums.org/showthread.php?t=2111236](http://ubuntuforums.org/showthread.php?t=2111236)

---

