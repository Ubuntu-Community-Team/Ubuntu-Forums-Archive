---
title: "AMDGPU-PRO Not Working"
date: 2017-01-03
forum: Hardware
---

### Post by bookerv on 2017-01-03
hey guys. i have the problem that i cannot run the amd-gpu-pro driver because of an dkms error. i tried amdgpu 16.40/16.50 on kernels 4.4-4.9 (yes, all of them) and i have the same error under every combination:



ERROR (dkms apport): kernel package linux-headers-4.9.0-040900-generic is not supported
Error! Bad return status for module build on kernel: 4.9.0-040900-generic (x86_64)
Consult /var/lib/dkms/amdgpu-pro/16.50-362463/build/make.log for more information.

but it doenst matter if its 4.4, 4.5, 4.6, 4.7, 4.8 or 4.9. i tried to reconfigure dkms but same error. if you guys want more infos i got a LOT of outputs but it seems that is the core of the problem: the dkms doesnt work quite right.

any idea how to fix that?

---

### Post by QIII on 2017-01-03
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2347795](https://ubuntuforums.org/showthread.php?t=2347795)

---

### Post by bookerv on 2017-01-05
Thanks for making a specialized thread for it but i fixed my problem.

Turns out i hit major errors with the dkms tree in 4.x-4.9. so you can use that and install the amdgpu-pro driver but it can go wrong. why there is that issue, i dont know. but i guess you can manually fix the dkms with a newer kernel but i couldnt.

The fix goes like this:

run Kernel 4.4

you install the driver

cd amdgpu-pro-16.50-362463


./amdgpu-pro-install -y 




sudo dpkg-reconfigure amdgpu-pro-dkms // this is the part that is super important. 




sudo -i for root  // this gets better perfomance 
echo -e "high" > /sys/class/drm/card0/device/power_dpm_force_performance_level // because it raises the power limit to high and gets more fps

so, yeah. i'd say solved. but then again. i dont get the full power of the RX480 so if there are people who know to get more juice outta that card and driver, please share.

---

