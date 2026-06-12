---
title: "Switch from nvidia drivers to nouveau - problems with resolution &amp; display detection"
date: 2019-02-20
forum: Hardware
---

### Post by flashkiller on 2019-02-20
Hello,

I just switched back from the proprietary nvidia driver back to nouveau.

After restarting I'm stuck with a resolution of 800x600 and my secondary display is not being detected.

Here are some infos from my system:

OS: Ubuntu 18.10
Graphics card: Nvidia GTX 460

```
lshw -C display
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GF104 [GeForce GTX 460]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f4000000-f5ffffff memory:e8000000-efffffff memory:f0000000-f3ffffff ioport:e000(size=128) memory:c0000-dffff


less /var/log/Xorg.0.log |grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.132] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[    25.132] (EE) open /dev/dri/card0: No such file or directory
[    25.132] (EE) open /dev/dri/card0: No such file or directory
[    25.134] (EE) Screen 0 deleted because of no matching config section.
[    25.146] (II) Initializing extension MIT-SCREEN-SAVER

ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000E22sv000010B0sd00000801bc03sc00i00
vendor   : NVIDIA Corporation
model    : GF104 [GeForce GTX 460]
driver   : nvidia-driver-390 - distro non-free recommended
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

spci | grep -E "VGA|3D"
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1)

xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 0mm x 0mm
   800x600       75.00* 


```

I also checked if there is /etc/X11/xorg.conf file, but there is no such file.

I'd really appreciate any help.

Thanks in advance

---

### Post by mastablasta on 2019-02-20
nouveau drivers are reverse engineered and while they work well on some chips they don't work so well on others. for good performance it is advised to use nvidia proprietary drivers instead.

if you are an opensource only person, then it is best to use an AMD or Intel GPU chip.

xorg.conf can be created. also make sure you have xorg session and not wayland. 

more info: 
how to switch: [https://askubuntu.com/questions/1032357/how-to-switch-from-nvidia-to-nouveau-drivers-on-ubuntu-18-04](https://askubuntu.com/questions/1032357/how-to-switch-from-nvidia-to-nouveau-drivers-on-ubuntu-18-04)

nouveau driver troubleshooting and other info:
[https://nouveau.freedesktop.org/wiki/](https://nouveau.freedesktop.org/wiki/)
[https://nouveau.freedesktop.org/wiki/TroubleShooting/](https://nouveau.freedesktop.org/wiki/TroubleShooting/)

binary driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by flashkiller on 2019-02-20
Thanks for the fast reply, problem solved.

I just had to install "nouveau-firmware" and after a reboot everything works (resolution & display-detection) again.

I find it too bad that a switch back using "Software & Update" to nouveau did not automatically install this.
This should in my opinion be included in a future update as this would make usage of Ubuntu easier for non-educated users.

Thanks again for the help.

---

