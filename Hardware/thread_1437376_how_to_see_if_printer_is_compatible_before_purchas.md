---
title: "how to see if printer is compatible before purchasing?"
date: 2010-03-23
forum: Hardware
---

### Post by monicamaria on 2010-03-23
Hello,

I installed Ubunto 9.1 but my Lexmark p4350 will not work with it.  I checked the forums but nothing worked.  I have been looking online at some HP Printers and was wondering if there is a way to see if it would be compatible with Ubunto before I purchase one.

I wrote down the model numbers and checked to see if it was on the list that came up in system/administration/printing under new printer configuration.  If the printer is listed does that mean it is compatible?  Is there another way to find out?

Thanks for any help,
Monica

---

### Post by diesch on 2010-03-23
If the printer is listed there there is at least some support for it - but that doesn't necessary mean it is really usable.

A good source of information about printers in general is [http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting)

If a printer is listed as supported there it at least can be made working with Ubuntu, if it is not listed there or listed as unsupported it most likely doesn't work  - at least not now.


For HP printers you can look at [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html) You can see the version of HPLIP that comes with your Ubuntu version by 
looking for the package *hplip* in Synapitcs or by
typing
```
apt-cache show hplip|grep ^Version:
``` at the command line.

---

### Post by monicamaria on 2010-03-23
I went to the link and found a couple of the printers listed.

Thank you for the help.

Monica

---

### Post by irishrick on 2010-03-23
I have yet to find a HP printer that Ubuntu does not support. Lexmark on the other hand has few although I have seen some work arounds which partially work.  There are a few tips in this thread [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) that you could try.

---

