---
title: "Suspend/Hibernate Problems with NVIDIA restricted drivers"
date: 2010-07-02
forum: Hardware
---

### Post by disciple3d on 2010-07-02
Hi there,

I'm having some problems with suspend/resume when testing my Marvin Linux PCs ([www.marvincomputers.co.uk](www.marvincomputers.co.uk)).  

I think it is related to NVIDIA drivers, but it doesn't actually produce any errors in the log - rather /var/log/pm-suspend.log shows lots of 'success' entries, and then tries to suspend, and wakes up again immediately.  Can anyone provide any information on what is causing this insomnia?  It's a NVIDIA Geforce 210 PCIe graphics card.. here are the versions and a bit of the output from thee log:

```
ii  nvidia-current            195.36.24-0ubuntu1~10.04  NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-dev        195.36.24-0ubuntu1~10.04  NVIDIA binary Xorg driver development files
ii  nvidia-current-modaliases 195.36.24-0ubuntu1~10.04  Modaliases for the NVIDIA binary X.Org driver
ii  linux-image-generic       2.6.32.23.24              Generic Linux kernel image
ii  pm-utils                  1.3.0-1ubuntu2            utilities and scripts for power management

```


```
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul  2 12:51:29 BST 2010: performing suspend
Fri Jul  2 12:51:35 BST 2010: Awake.
Fri Jul  2 12:51:35 BST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Fri Jul  2 12:51:36 BST 2010: Finished.
```

The main thing I wanted to ask though is - what package should I file the bug report under?  I can't seem to find this - is it pm-utils, or something else?

Cheers,

Chris

---

### Post by disciple3d on 2010-07-02
Oh, I should add, it's doing exactly the same with hibernate - but I figure, I'll probably have to fix suspend before hibernate will work too ;)

---

### Post by clrg on 2010-07-02
Well, since this is a closed source driver, I don't think there's much a developer can to in order to fix the issue.

Have you tried the latest driver from NVidia's homepage? Maybe the problem is already fixed, but hasn't made its way to the repositories yet.

---

### Post by disciple3d on 2010-07-02
I don't know for sure that's what it is - and since I am trying to fix for an OEM build, I don't want to install drivers outside of the Ubuntu repos if I can help it.

If I can confirm it really is an NVIDIA driver issue, then I will report it to them.  Any idea how to track that down though?

thanks,

Chris

---

### Post by clrg on 2010-07-02
Well, on my machine, there is /var/log/nvidia-installer.log which contains messages emitted during module compilation. Maybe yours contains a clue

Edit: With an older version of the kernel, I experienced problems with standby/hibernation too. My solution was not to use either of them. My laptop boots in less than 20 seconds- "so why bother?" I thought. I know its not a solution, but if standby/hibernation is not important to you, just don't use them.

---

### Post by disciple3d on 2010-07-15
I've not solved this yet, but I'll keep looking! :)  Thanks for your help.  I will post a reply if I get any further with it.

---

### Post by feffer on 2011-01-01
Don't know if you've ever resolved this. Here's my experience fwiw. Dell 8600 laptop using nvidia drivers: altered xorg.conf according to [this link]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend") and suspend now works fine. I don't use hibernate as plain booting is as fast. On a new Dell 9100 xps desktop tried the same fix and it doesn't work. Results are the same as yours: pm-suspend.log shows the system go down, pause and then come back up. I assume it is a bug in the nvidia driver not being up-to-date with the new Dell x58 intell mobo (64 bit).

Regards,
feffer

---

