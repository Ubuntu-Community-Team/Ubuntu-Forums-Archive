---
title: "Building the ibm-acpi module"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by Jingo on 2005-10-14
I have problems building the ibm-acpi module.

```
make -C /lib/modules/2.6.12-9-686/build SUBDIRS=/home/johannes/dep-packages/ibm-acpi-0.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CC [M]  /home/johannes/dep-packages/ibm-acpi-0.11/ibm_acpi.o
/home/johannes/dep-packages/ibm-acpi-0.11/ibm_acpi.c:1756: error: conflicting types for 'device_add'
include/linux/device.h:317: error: previous declaration of 'device_add' was here/home/johannes/dep-packages/ibm-acpi-0.11/ibm_acpi.c:1756: error: conflicting types for 'device_add'
include/linux/device.h:317: error: previous declaration of 'device_add' was heremake[2]: *** [/home/johannes/dep-packages/ibm-acpi-0.11/ibm_acpi.o] Error 1
make[1]: *** [_module_/home/johannes/dep-packages/ibm-acpi-0.11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
make: *** [default] Error 2
```

Any ideas?

---

### Post by squido on 2005-11-08
See:
[http://mail.matrix.de/pipermail/linux-thinkpad/2005-August/028163.html](http://mail.matrix.de/pipermail/linux-thinkpad/2005-August/028163.html)

Here's a (stupid) patch:

---------SNIP--------
*** ibm_acpi.c  2005-03-17 02:06:16.000000000 -0800
--- ../ibm-acpi-0.11.good/ibm_acpi.c    2005-11-08 08:41:42.000000000 -0800
***************
*** 1752,1758 ****
        return 0;
  }

! static int device_add(struct acpi_device *device)
  {
        return 0;
  }
--- 1752,1758 ----
        return 0;
  }

! static int ibmacpi_device_add(struct acpi_device *device)
  {
        return 0;
  }
***************
*** 1770,1776 ****
        memset(ibm->driver, 0, sizeof(struct acpi_driver));
        sprintf(ibm->driver->name, "%s/%s", IBM_NAME, ibm->name);
        ibm->driver->ids = ibm->hid;
!       ibm->driver->ops.add = &device_add;

        ret = acpi_bus_register_driver(ibm->driver);
        if (ret < 0) {
--- 1770,1776 ----
        memset(ibm->driver, 0, sizeof(struct acpi_driver));
        sprintf(ibm->driver->name, "%s/%s", IBM_NAME, ibm->name);
        ibm->driver->ids = ibm->hid;
!       ibm->driver->ops.add = &ibmacpi_device_add;

        ret = acpi_bus_register_driver(ibm->driver);
        if (ret < 0) {
---------SNIP--------

---

### Post by pepeke on 2005-12-01
I had the same problem, solved it quick and dirty

(I always link my current source/headers with /usr/src/linux, maybe you have  to replace /usr/src/linux with /usr/src/linux-headers-$(uname -r) in the next line)

sudo vi /usr/src/linux/include/linux/device.h
search for 
extern int device_add(struct device * dev);
change device into acpi_device like so
extern int device_add(struct **acpi_device** * dev);
 

now compile the module
I don't know if I broke anything else so better change device.h back to original version in order to avoid future trouble.

modprobe -k ibm_acpi experimental=1 
works and I can control my fan (which is why I wanted to recompile ..)
hope this helps/works for you

---

### Post by Toshi38 on 2005-12-19
I too am having trouble with installing the ibm-acpi-0.11 (I am very new to linux), Here is what I do and the error I get: 

stephen@laptop-ubuntu:~/Desktop$ tar xvzf ibm-acpi-0.11.tar.gz
ibm-acpi-0.11/
ibm-acpi-0.11/Makefile
ibm-acpi-0.11/CHANGES
ibm-acpi-0.11/README
ibm-acpi-0.11/config/
ibm-acpi-0.11/config/sbin/
ibm-acpi-0.11/config/sbin/service
ibm-acpi-0.11/config/usr/
ibm-acpi-0.11/config/usr/local/
ibm-acpi-0.11/config/usr/local/sbin/
ibm-acpi-0.11/config/usr/local/sbin/idectl
ibm-acpi-0.11/config/usr/local/sbin/laptop_mode
ibm-acpi-0.11/config/usr/sbin/
ibm-acpi-0.11/config/etc/
ibm-acpi-0.11/config/etc/acpi/
ibm-acpi-0.11/config/etc/acpi/actions/
ibm-acpi-0.11/config/etc/acpi/actions/blank.sh
ibm-acpi-0.11/config/etc/acpi/actions/eject.sh
ibm-acpi-0.11/config/etc/acpi/actions/video.sh
ibm-acpi-0.11/config/etc/acpi/actions/radio.sh
ibm-acpi-0.11/config/etc/acpi/actions/undock.sh
ibm-acpi-0.11/config/etc/acpi/actions/battery.sh
ibm-acpi-0.11/config/etc/acpi/actions/dock.sh
ibm-acpi-0.11/config/etc/acpi/actions/rescan.sh
ibm-acpi-0.11/config/etc/acpi/events/
ibm-acpi-0.11/config/etc/acpi/events/dock
ibm-acpi-0.11/config/etc/acpi/events/radio
ibm-acpi-0.11/config/etc/acpi/events/blank
ibm-acpi-0.11/config/etc/acpi/events/sleep
ibm-acpi-0.11/config/etc/acpi/events/undock
ibm-acpi-0.11/config/etc/acpi/events/eject
ibm-acpi-0.11/config/etc/acpi/events/hibernate
ibm-acpi-0.11/config/etc/acpi/events/rescan
ibm-acpi-0.11/config/etc/acpi/events/video
ibm-acpi-0.11/config/etc/acpi/events/ac
ibm-acpi-0.11/config/etc/hibernate/
ibm-acpi-0.11/config/etc/hibernate/sleep.conf
ibm-acpi-0.11/config/etc/hibernate/hibernate.conf
ibm-acpi-0.11/LICENSE
ibm-acpi-0.11/ibm_acpi.c
stephen@laptop-ubuntu:~/Desktop$ cd ibm-acpi-0.11
stephen@laptop-ubuntu:~/Desktop/ibm-acpi-0.11$ make
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/home/stephen/Desktop/ibm-acpi- 0.11 modules
make: *** /lib/modules/2.6.12-10-686/build: No such file or directory.  Stop.
make: *** [default] Error 2
stephen@laptop-ubuntu:~/Desktop/ibm-acpi-0.11$


any help would be appreciated
Stephen Lau

---

### Post by Hari Seldon on 2006-02-03
A small up because I just want to make my T43p's fan be quietter but I get the same error as Toshi38. This is a little annoying as it is really is the major problem  with this laptop and I just love my Ubuntu (I just don't want to go into a Debian or a Gentoo installation because of that :( )

Is this new ibm acpi module will be included in the Dapper release ?

---

### Post by rklump on 2006-02-09
@Toshi38

I get the same problem with my Ubuntu 5.10 (IBM T42): 
```
**jesper@MAT29:/usr/local/ibm-acpi-0.11$** make
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/usr/local/ibm-acpi-0.11 modules
make: *** /lib/modules/2.6.12-10-686/build: No such file or directory.  Stop.
make: *** [default] Error 2
```
I have the 0.8 version running but I would like to do something about the fan noise (which is really anoying me). 

Is it necessary mess with the kernel to get it to work?

---

### Post by Hari Seldon on 2006-02-28
Isn't there somewhere on the net a howto build and install this damn upgrade O_o ?

I mean, even if I'm neither a newb nor a w4rlôrd$ on linux, I can't make this damn module to work (because I lack comprehension on how things are linked).

So far, I've   : 

-downloaded the ibm-api-0.11 archive
-unflatted it
-got the linux-header-2.6.10-386 source tree
-modified the ibm-acpi.c (I've also tried to modify the .h as mentionnend upper in the thread)
-built succesfully the module
-added it with modprobe
-... and nothing more is happening and I really don't know what to do, what to test or else.

So if somenone made it work like it seems, could they explain how they did it because this fan is driving me mad.

Thanks a lot :)

---

### Post by alsac on 2006-03-08
Could someone send me their "acpi/events" please?

these files in particulars: 
/etc/acpi/events/
/etc/acpi/events/dock
/etc/acpi/events/radio
/etc/acpi/events/blank
/etc/acpi/events/sleep
/etc/acpi/events/undock
/etc/acpi/events/eject
/etc/acpi/events/hibernate
/etc/acpi/events/ac

to my e-mail in the profile. I think I messed them up and I'd like to see someone's with a working set.

Thanks very much.  :p

---

### Post by kderose on 2006-09-04
I get exactly the same problem!  Has anyone figured out what the fix is???  I would love any help I can get...this has been driving me crazy!  

Thanks!  :-)

---

