---
title: "nvidia-detector fails  to detect GeForce GT545 card"
date: 2011-11-23
forum: Hardware
---

### Post by emreakbas on 2011-11-23
Hi, 

I did a fresh install of Kubuntu 10.04 on a Dell Alienware desktop machine which has a GeForce GT545 graphics card. 

Anytime I do an install or update, apt-get is giving me this log: 

```

run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-35-generic /boot/vmlinuz-2.6.32-35-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True)
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __init__
    self.printSelection()
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 408, in printSelection
    driver = self.selectDriver()
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 328, in selectDriver
    choice = self.driversForCards[self.driversForCards.keys()[0]][0]
IndexError: list index out of range
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-35-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-35-generic (--configure):
 subprocess installed post-installation script returned error exit status 2

```


Obviously, nvidia-detector fails to detect my card. lscpi gives: 

```

$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation Device 1241 (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation Device 1241 (rev a1)

```

I manually installed the appropriate NVIDIA drivers (ver 275) and X works fine but each time I do an install or upgrade, apt acts like if I updated my kernel: 

```

Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-33.70 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-33.70 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2

```, and I get a "system should be rebooted" message. How can I fix this?

---

### Post by BicyclerBoy on 2011-11-23
AFAIK..the nvidia modaliases package helps identify video card..I think this may have been integrated into driver package..

The error logs suggests that the last nVidia driver update failed (missing headers) & the script is retrying to complete the kernel/boot image update.

Part of the nVidia kernel module must be complied against the current kernel (headers package).
This means that the driver must be re-compiled with every kernel update, and a new boot image created.

If you get the driver as a managed package from a ppa, you can forget about rebuilding..

The driver version you need can be found in xorg-edgers or ubuntu-x-swat ppas.

I run the driver 280 (290 just released) on a 10.04 system.

---

### Post by emreakbas on 2011-11-28
Adding ubuntu-x-swat  and an update/upgrade/reboot solved the problem. Thank you very much.

---

