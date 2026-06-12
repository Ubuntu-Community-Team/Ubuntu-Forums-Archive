---
title: "Asus Notebook BackLight"
date: 2011-10-14
forum: Hardware
---

### Post by venomcode on 2011-10-14
I just recently installed 11.10 and my hotkeys work but my keyboard backlights wont turn on. It worked on 11.04 after installing a WMI driver, but it wont work for 11.10. Please help my notebook model is ASUS G73Sw

---

### Post by venomcode on 2011-10-14
Well, the drivers work for a bit on 11.10 but out of no where just stop working. I downloaded something called acpi4asus-dkms-master-d89d043 , but does anyone know if there is an update for this package to make it stable for the Asus G73SW Notebook?

---

### Post by venomcode on 2011-10-18
OK, since no one has responded, i had to do the research myself. I got the keyboard backlight working on my ASUS G73SW Notebook on Ubuntu 11.10

First step is to install the driver.

[http://98.139.168.220/babelfish/translate_url_content?.intl=us&lp=fr_en&trurl=http%3a%2f%2fgit.iksaif.net%2f%3fp%3dacpi4asus-dkms.git%3ba%3dsnapshot%3bh%3dmaster%3bsf%3dtgz](http://98.139.168.220/babelfish/translate_url_content?.intl=us&lp=fr_en&trurl=http%3a%2f%2fgit.iksaif.net%2f%3fp%3dacpi4asus-dkms.git%3ba%3dsnapshot%3bh%3dmaster%3bsf%3dtgz)

then I followed the steps here.

[http://ubuntuforums.org/showthread.php?t=1605498](http://ubuntuforums.org/showthread.php?t=1605498)


Then I edited a file.
 **/etc/rc.local** add following information to it before the end of the file (before exit the 0):   

```
echo 0x00050021 > /sys/kernel/debug/asus-nb-wmi/dev_id echo 0x82 > /sys/kernel/debug/asus-nb-wmi/ctrl_param cat /sys/kernel/debug/asus-nb-wmi/devs
```

That fixed it for me. I'm sure this works for all G series ASUS Notebooks.

---

### Post by cnotiog on 2011-10-26
You hero! Just installed 11.10 last night and was trying to figure out this problem just now. Only a couple more things to get sorted now!

Cheers.

---

### Post by roblach on 2012-02-10
I know this is an old post but i really need to get my backlit keyboard working on my G73Sw. How do i install this package? acpi4asus-dkms-master-d86caf9.tar.gz

---

