---
title: "Lucent WinModem on T22?"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by IndieRockSteve on 2005-04-28
how do I install the drivers for this? I can't modprobe lt_modem or any of the other stuff I find when I search.

thanks!

---

### Post by odix on 2005-05-06
Hi,
The best way is to follow the description [here](http://linmodems.technion.ac.il/).

for short:
1.) install build-essentials, kernel-headers
2.) download the [driver (my this or newer), with my T22 it was ok](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-7alk.tar.bz2)
3.) unpack the driver (tar -xjvf <file>)
4.) change to the dir of the driver
5.) execute```
make clean && make
```
6.) follow the instruction in the README file at the point of "Copy them to ..."

you not have to edit modprobe.conf, use /etc/modprobe.d/aliases instead.
copy the file "<driverdir>/docs/ltmodem.rules to /etc/udev/rules.d/



regards

---

### Post by az on 2005-05-06
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

Scroll down to the lucent part...

---

### Post by odix on 2005-05-06
[QUOTE=azz][http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

Scroll down to the lucent part...[/QUOTE]

Thats nice, but the drivers (lt_modem, lt_serial) from the "restricted" package doesn't work with IBM T22, the new one (ltmodem,ltserial) do work and with the changes in aliases you don't have to put them in /etc/modules, they will be loaded automatically during hotplug init.

regards

---

### Post by az on 2005-05-06
[QUOTE=odix]Thats nice, but the drivers (lt_modem, lt_serial) from the "restricted" package doesn't work with IBM T22, the new one (ltmodem,ltserial) do work and with the changes in aliases you don't have to put them in /etc/modules, they will be loaded automatically during hotplug init.

regards[/QUOTE]

That is fantastic!  I do not own the hardware any more, so I cannot troubleshoot this very well.  The lucent modem package contains a lot of utilities and setup scripts while the restricted-modules only includes the modules.

Please file a bug report about this.

[https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=lucent&field0-0-1=component&type0-0-1=substring&value0-0-1=lucent&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=lucent&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=lucent](https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=lucent&field0-0-1=component&type0-0-1=substring&value0-0-1=lucent&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=lucent&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=lucent)


I cannot urge you enough to file a bug report and follow up on it.  Package: linux-restricted-modules.  Perhaps more than just the modules need to be included if support for this modem is to be included on the install cd.

---

### Post by odix on 2005-05-10
I will try to reproduce the steps to activate the internal modem (lucent)  on a secondary T22, the first I've "delivered" to my father, and a then I will file this to bugzilla

regards odiX

---

