---
title: "Touchpad not working on Lenovo V330"
date: 2018-10-23
forum: Hardware
---

### Post by vishalgarg-bluebash on 2018-10-23
I got a Lenovo V330 and installed Ubuntu 16.04. Everything works, except for the touchpad.

When I was looking at solution*** [installing the latest mainline kernel solved this  ]("https://ubuntuforums.org/showthread.php?t=2394494")***problem

[SIZE=3]** acpi-id of my touchpad is i2c-ELAN061E:00**[/SIZE]

I checked ACPI ID is in at the end of elan_i2c_core.c of the latest mainline kernel[B]. But not able to find it 
[URL="https://elixir.bootlin.com/linux/v4.19/source/drivers/input/mouse/elan_i2c_core.c"]
https://elixir.bootlin.com/linux/v4.19/source/drivers/input/mouse/elan_i2c_core.c[/URL][/B]

[COLOR=#800000]if there are no prebuild kernel with your acpiid, you must add your id  to elan_i2c_core.c file, patch and build your kernel packages manual.[/COLOR]

Not sure I how to add this patch any help??

---

### Post by ntpndcmb on 2018-10-23
I had same problem on lenovo ideapad 330

Solution:
1. install ubuntu 18.04
2.  download kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18.16/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18.16/)
linux-headers-4.18.16-041816-generic_4.18.16-041816.201810200431_amd64.deb
linux-headers-4.18.16-041816-lowlatency_4.18.16-041816.201810200431_amd64.deb
linux-headers-4.18.16-041816_4.18.16-041816.201810200431_all.deb
linux-image-unsigned-4.18.16-041816-generic_4.18.16-041816.201810200431_amd64.deb
linux-image-unsigned-4.18.16-041816-lowlatency_4.18.16-041816.201810200431_amd64.deb
linux-modules-4.18.16-041816-generic_4.18.16-041816.201810200431_amd64.deb
linux-modules-4.18.16-041816-lowlatency_4.18.16-041816.201810200431_amd64.deb
3. dpkg -i *.deb
 
You can install this kernel on ubuntu 16.04, but there are problems with depends.

---

