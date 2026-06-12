---
title: "Kernel 4.11 breaks right click on Touchpad DELL 3542 (Synaptic)"
date: 2017-05-21
forum: Hardware
---

### Post by ukbeast on 2017-05-21
Kernel 4.10 recognises touchpad as DLL0651:00 06CB:2985 and am able to use right-click using the physical button.
Kernel 4.11 recognises touchpad as Synaptics s3203 but the right click button does not physically work.

I had the same issue on Opensuse tumbleweed when they updated their kernel to 4.11.

I have copied  xinput list-props from both kernels and found that I am losing capabilities. (The numbers represent kernel version)

Thanks   
[ATTACH]275227[/ATTACH] [ATTACH]275228[/ATTACH]

---

### Post by prijindal on 2017-05-24
I am facing the same problem after updating from 4.10 to 4.11 on arch linux.
Possibly a bug with touchpad drivers

---

### Post by wildmanne39 on 2017-05-24
@prijindal if you want help with your issue please start your own thread here:
[https://ubuntuforums.org/forumdisplay.php?f=321](https://ubuntuforums.org/forumdisplay.php?f=321)
Thanks

---

### Post by ukbeast on 2017-05-24
I looked on [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc1/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc1/CHANGES) and found 

"[COLOR=#000000]HID: rmi: Make hid-rmi a transport driver for synaptics-rmi4"
[/COLOR]"[COLOR=#000000]HID: rmi: Handle all Synaptics touchpads using hid-rmi"[/COLOR]

Perhaps this is what caused this bug to occur for [COLOR=#000000][FONT=monospace]hid_rmi? [/FONT][/COLOR]https://lkml.org/lkml/2017/3/28/1234

---

