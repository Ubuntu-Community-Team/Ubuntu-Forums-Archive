---
title: "sound not working on acer aspire one d250"
date: 2010-07-13
forum: Hardware
---

### Post by katiedidit on 2010-07-13
I just started using Ubuntu yesterday, so I was trying to make the front mic work on it following these instructions:

[https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne/AOD250#Fixing](https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne/AOD250#Fixing) the microphone

Not only did the instructions not make my mic work, but now the sound isn't working. Does anyone have any idea how I can fix this?!

Thanks a lot!

---

### Post by katiedidit on 2010-07-13
I am getting this error message while trying to fix the mic if it helps:

/home/katie/alsa-driver-1.0.20/pci/asihpi/hpios_linux_kernel.c: In function ‘HpiOs_DelayMicroSeconds’:
/home/katie/alsa-driver-1.0.20/pci/asihpi/hpios_linux_kernel.c:34: error: implicit declaration of function ‘schedule_timeout_uninterruptible’
make[4]: *** [/home/katie/alsa-driver-1.0.20/pci/asihpi/hpios_linux_kernel.o] Error 1
make[3]: *** [/home/katie/alsa-driver-1.0.20/pci/asihpi] Error 2
make[2]: *** [/home/katie/alsa-driver-1.0.20/pci] Error 2
make[1]: *** [_module_/home/katie/alsa-driver-1.0.20] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [compile] Error 2
katie@katie-laptop:~/alsa-driver-1.0.20$

---

