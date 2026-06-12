---
title: "asus eee over clock every startup"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by markp1989 on 2007-12-19
i installed the suport for over clocking, using this program, and every time i boot i have to press fn + f6 to enable over clocking, does any one have any ideas how to enable it automatically every boot? [http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

---

### Post by darrenm on 2007-12-21
Currently reloading my EEE so can't check if it works but it looks like you just take out the acpi_fakekey $KEY_PROG in /etc/init.d/eee-overclock.sh

Don't know why he puts all those steps in though. All you need to do is put p4_clockmod into /etc/modules and reboot

---

### Post by markp1989 on 2007-12-21
> **darrenm said:**
> Don't know why he puts all those steps in though. All you need to do is put p4_clockmod into /etc/modules and reboot

i did that , and it enabes cpu freq scaling and over clocking , and its better as the clock speed can go alot lower then it could go before, so i asume that it wil save battery power?

thanks!

---

### Post by darrenm on 2007-12-21
> **markp1989 said:**
> i did that , and it enabes cpu freq scaling and over clocking , and its better as the clock speed can go alot lower then it could go before, so i asume that it wil save battery power?

thanks!

Theres mass debate about whether it does actually save power or not as the Celeron in the EEE doesn't actually drop any lower on clock speed even though the kernel thinks it does. I'm not really sure, haven't done any testing on battery life or performance or anything,

---

### Post by imabuddha on 2008-01-10
> **markp1989 said:**
> i installed the suport for over clocking, using this program, and every time i boot i have to press fn + f6 to enable over clocking, does any one have any ideas how to enable it automatically every boot?
open a terminal and enter this command:
sudo ln -sf /etc/init.d/eee-overclock.sh /etc/rc2.d/S10eee-overclock
:)

---

