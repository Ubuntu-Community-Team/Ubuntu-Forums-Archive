---
title: "Lenovo T400 Touchpad not working"
date: 2009-10-29
forum: Hardware
---

### Post by praveengarlapati on 2009-10-29
Hi,

I have recently upgraded to Karmic on my Lenovo T400 and found that the Touchpad is disabled.

I searched around and found that  I have to do the config 

Option "SHMConfig" "true" 

in my xorg.conf and so I did.

Also I did the below config in /etc/hal/fdi/policy/shmconfig.fdi

<?xml version="2.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
</match>
</device>
</deviceinfo>

But even after these configurations the issue is not solved.

Below is the output from Xorg.0.log

praveen@ubuntu:~$ cat /var/log/Xorg.0.log | grep Synaptics
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) Synaptics touchpad driver version 1.1.2
SynPS/2 Synaptics TouchPad The /dev/input/event* device nodes seem to be missing
Query no Synaptics: 000000
(--) SynPS/2 Synaptics TouchPad: no supported touchpad found
(EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"


So obviously it points that the Synaptics Touchpad has some issue.

Can somebody point me in the right direction to solve the issue ?

---

### Post by semicomatose on 2009-10-29
Got the same problem. IBM ThinkPad R40. Help!

-semi

---

### Post by geoffreynham on 2009-10-30
I have the same issue on the Lenovo R400...

---

### Post by geoffreynham on 2009-10-30
My touchpad is working again.  It seems my issue was that during the upgrade the grub bootloader was not updated to boot to the newest kernel, and the old kernel had issues.  Using the newest kernel fixed a lot of stuff, actually.

---

### Post by praveengarlapati on 2009-10-30
@geoffreynham: 
Thanks for the reply. Did you just run update-grub ?
How did you solve the issue ?

---

### Post by code4pay on 2009-11-01
I had the same issue on my compaq presario (and a bunch of video problems) read this and realised my grub was not listing the latest kernel.  I edited /boot/grub/menu.lst
and addded
[php]
title Ubuntu 9.10, kernel 2.6.31-14-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=741e34fa-ea6c-4aa9-9456-6ab5192867a4 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
[/php]basically you need to copy the an old entry and update the name of the kernel 
from kernel 2.6.28-13-generic to 2.6.31-14-generic every where it is mentioned.

then reboot.

---

