---
title: "ubuntu is from another dimension?"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by fackamato on 2005-03-14
using fglrx driver, ati card, 2.6.10-k7, i install the driver, i load it, xorg works fine. i reboot, xorg doesn't start, i get this: [www.tehjunkyard.net/xorg.log](www.tehjunkyard.net/xorg.log) . i modprobe -r fglrx.ko, I copy the fglrx.ko from fglrx package to /lib/modules/kernelversion/kernel/drivers/video/fglrx.ko and modprobe it again. now it works. reboot, doesn't work. I have to rmmod and copy the file again, and modprobe, and it works.
does ubuntu copy over the file or something? i have to do this every boot. i don't understand  :-|

**EDIT:**
29dfabdc2f414f61c895e065e85efc4e  /lib/modules/2.6.10-4-k7/kernel/drivers/video/fglrx.ko
29dfabdc2f414f61c895e065e85efc4e  /lib/modules/fglrx/build_mod/fglrx.ko

I do this:

```
modprobe -v -r fglrx ; cp /lib/modules/fglrx/build_mod/fglrx.ko /lib/modules/2.6.10-4-k7/kernel/drivers/video/fglrx.ko ; modprobe -v fglrx ; /etc/init.d/gdm stop ; /etc/init.d/gdm start
```

And guess what, xorg starts and is happy. WHAT THE BEEP IS WRONG?!?!  ](*,)  ](*,)

---

### Post by telmo on 2005-03-14
Ok... this is what i did, and it works great!
Do this as root...

(Ctrl+Alt+F1)
```
#/etc/init.d/gdm stop
#alien <driver package name>
#mv /lib/modules/<kernel version>/kernel/drivers/video/fglrx.ko $HOME
#dpkg --force-overwrite -i <driver package name>.deb
#rmmod fglrx
#cd /lib/modules/fglrx/build_mod
#sh make.sh
#cd ..
#sh make_install.sh
#cp fglrx.ko /lib/modules/<kernel version>/misc/
#depmod -ae
#fglrxconfig
#modprobe fglrx
#/etc/init.d/gdm start

$fglrxinfo
```

Hope it works for you!

BTW, Ubuntu must be from the planet COOL! ;)

---

### Post by fackamato on 2005-03-14
Thanks, but it's not a problem with the driver. It seems that the first time the fglrx module is loaded, something goes wrong:

It seems like the video card is not correctly loaded at boot time
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed


Reloading the same module, without copying anything, works. Any idea? Or is this an ATi bug?

**Edit:** I even changed /etc/init.d/gdm to this:

```
case "$1" in
  start)
# unload the fglrx module, and load it again
modprobe -v -r fglrx ; modprobe -v fglrx

```

But it doesn't work at boot. If I run /etc/init.d/gdm stop ; /etc/init.d/gdm start after I've logged in to the terminal everything works.

---

### Post by telmo on 2005-03-14
Sorry to hear that... 
No, i don't really how to help you...  :???:

---

### Post by trigg on 2005-03-15
[QUOTE=fackamato]Thanks, but it's not a problem with the driver. It seems that the first time the fglrx module is loaded, something goes wrong:

It seems like the video card is not correctly loaded at boot time
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed


Reloading the same module, without copying anything, works. Any idea? Or is this an ATi bug?

**Edit:** I even changed /etc/init.d/gdm to this:

```
case "$1" in
  start)
# unload the fglrx module, and load it again
modprobe -v -r fglrx ; modprobe -v fglrx

```

But it doesn't work at boot. If I run /etc/init.d/gdm stop ; /etc/init.d/gdm start after I've logged in to the terminal everything works.[/QUOTE]

Where is fglrx in your /etc/modules file?  Try putting it as the first module loaded and see if that fixes the problem.  I was having similar (but not exactly the same) issues, and when I changed the order of modules loaded it worked.

trigg

---

