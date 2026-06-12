---
title: "No external displays working with Ubuntu 18.10"
date: 2019-03-09
forum: Hardware
---

### Post by takeawaydave on 2019-03-09
I have a Dell Precison 7510 and 2 external Dell Displays. Each has DP and HDMI. 

The Dell has mDP, USB-C and HDMI. However having tried all combos no external display works.

The laptop is running on the NVidia card in Performance Mode (via PRIME Profile)

How can I get the displays hooked up?

---

### Post by takeawaydave on 2019-03-09
Probably time to move back to Windows . .. such basic stuff that should just work at least in version 18.

---

### Post by Autodave on 2019-03-09
Have you installed the Nvidia driver?  If so, what one and where did you obtain it from.  If you have not installed one yet, go to Additional Drivers and install the recommended one.

You may also want to go to 18.04 since it is a long term release (LTS) and will be more stable than 18.10.

  	 	 	 	   Every 2 years, a long term service release is made.  18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.

---

### Post by takeawaydave on 2019-03-09
Autodave - first of all thanks for the reply - having a bad day and getting very annoyed...

Actually on 18.04 not 18.10.

I go the NVidia driver from Software & Updates > Additional Drivers.

nvidia-driver-390

Here the kernel log

[https://pastebin.com/4nYjjV9r](https://pastebin.com/4nYjjV9r)

and:

```
root@precision:~# lsmod | grep nv
nvidia_uvm            757760  0
nvidia_drm             40960  4
nvidia_modeset       1048576  1 nvidia_drm
nvidia              14376960  314 nvidia_uvm,nvidia_modeset
drm_kms_helper        172032  2 nvidia_drm,i915
nvme                   36864  0
drm                   401408  17 drm_kms_helper,nvidia_drm,i915
nvme_core              61440  6 nvme
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
```

---

### Post by takeawaydave on 2019-03-09
[https://pastebin.com/VTjKYZ7k](https://pastebin.com/VTjKYZ7k)

This is what appears in the kernel log when plugging in an external display with mDP.

---

### Post by takeawaydave on 2019-03-09
From all accounts it looks like the Nvidia driver is quite broken on Unubuntu 18.04 - any suggestions ?

---

### Post by him610 on 2019-03-09
> Nvidia driver is quite broken on Unubuntu 18.04 - any suggestions ?
Maybe it is broken on your machine; not on my machine.
Suggest you remove all traces of Nvidia from your machine, reboot, then reinstall the current Nvidia drivers from Additional Drivers. Only attempt to connect and configure one monitor at a time. Once you get one monitor properly configured so that it displays as expected using  HDMI or DisplayPort then try adding the second monitor.

FWIW, we had a fairly new DisplayPort only monitor (don't remember the brand) that we could not configure properly in Windows10 or Xubuntu 18.04. We wound up giving it away.

---

### Post by takeawaydave on 2019-03-10
> **him610 said:**
> Maybe it is broken on your machine; not on my machine.
Suggest you remove all traces of Nvidia from your machine, reboot, then reinstall the current Nvidia drivers from Additional Drivers. Only attempt to connect and configure one monitor at a time. Once you get one monitor properly configured so that it displays as expected using  HDMI or DisplayPort then try adding the second monitor.

FWIW, we had a fairly new DisplayPort only monitor (don't remember the brand) that we could not configure properly in Windows10 or Xubuntu 18.04. We wound up giving it away.

Cheers for the response - I think the problem actually lies with the NVIDIA Driver and the M1000M GPU:

[https://askubuntu.com/questions/839643/nvidia-quadro-m1000m-on-dell-precision-5510-14-04-lts-black-screen](https://askubuntu.com/questions/839643/nvidia-quadro-m1000m-on-dell-precision-5510-14-04-lts-black-screen)

Any idea how I can start testing different versions of the drivers ? I currently have the following available nvidia-driver-390,396,410,415,418 but would like to test some of the older ones.

---

### Post by Autodave on 2019-03-10
Have you installed *synaptic *yet?  If not, do that.  When you go into synaptic, for your search type *nvidia.*  You will then scroll down the list to the Nvidia drivers: quite a few of them there.

---

### Post by takeawaydave on 2019-03-10
I install the nvidia-367 package but unable to get it loaded:

```
david@precision:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd000013B1sv00001028sd000006D9bc03sc00i00
vendor   : NVIDIA Corporation
model    : GM107GLM [Quadro M1000M]
driver   : nvidia-driver-415 - third-party free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-410 - third-party free
driver   : nvidia-driver-396 - third-party free
driver   : nvidia-driver-418 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

david@precision:~$ sudo apt install nvidia-367
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-367 is already the newest version (375.82-0ubuntu3).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@precision:~$ 
```

How can I try and clear out the new stuff and add just the old ?

---

### Post by takeawaydave on 2019-03-10
Is there any way to install an old nvidia-driver via apt ? 

If I try nvidia-367 I get nvidia-390 packages:

```
david@precision:~$ sudo apt install nvidia-367
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dkms libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390
  libnvidia-compute-390:i386 libnvidia-decode-390 libnvidia-decode-390:i386
  libnvidia-encode-390 libnvidia-encode-390:i386 libnvidia-fbc1-390
  libnvidia-fbc1-390:i386 libnvidia-gl-390 libnvidia-gl-390:i386
  libnvidia-ifr1-390 libnvidia-ifr1-390:i386 libwayland-client0:i386
  libwayland-server0:i386 nvidia-375 nvidia-384 nvidia-compute-utils-390
  nvidia-dkms-390 nvidia-driver-390 nvidia-kernel-common-390
  nvidia-kernel-source-390 nvidia-prime nvidia-utils-390
  xserver-xorg-video-nvidia-390
Suggested packages:
  menu
The following NEW packages will be installed:
  dkms libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390
  libnvidia-compute-390:i386 libnvidia-decode-390 libnvidia-decode-390:i386
  libnvidia-encode-390 libnvidia-encode-390:i386 libnvidia-fbc1-390
  libnvidia-fbc1-390:i386 libnvidia-gl-390 libnvidia-gl-390:i386
  libnvidia-ifr1-390 libnvidia-ifr1-390:i386 libwayland-client0:i386
  libwayland-server0:i386 nvidia-367 nvidia-375 nvidia-384
  nvidia-compute-utils-390 nvidia-dkms-390 nvidia-driver-390
  nvidia-kernel-common-390 nvidia-kernel-source-390 nvidia-prime
  nvidia-utils-390 xserver-xorg-video-nvidia-390
0 upgraded, 28 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/84.6 MB of archives.
After this operation, 362 MB of additional disk space will be used.
Do you want to continue? [Y/n] n   
Abort.
```

Which are the same as:

```
david@precision:~$ sudo apt install nvidia-390
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dkms libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390
  libnvidia-compute-390:i386 libnvidia-decode-390 libnvidia-decode-390:i386
  libnvidia-encode-390 libnvidia-encode-390:i386 libnvidia-fbc1-390
  libnvidia-fbc1-390:i386 libnvidia-gl-390 libnvidia-gl-390:i386
  libnvidia-ifr1-390 libnvidia-ifr1-390:i386 libwayland-client0:i386
  libwayland-server0:i386 nvidia-compute-utils-390 nvidia-dkms-390
  nvidia-driver-390 nvidia-kernel-common-390 nvidia-kernel-source-390
  nvidia-prime nvidia-utils-390 xserver-xorg-video-nvidia-390
Suggested packages:
  menu
The following NEW packages will be installed:
  dkms libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390
  libnvidia-compute-390:i386 libnvidia-decode-390 libnvidia-decode-390:i386
  libnvidia-encode-390 libnvidia-encode-390:i386 libnvidia-fbc1-390
  libnvidia-fbc1-390:i386 libnvidia-gl-390 libnvidia-gl-390:i386
  libnvidia-ifr1-390 libnvidia-ifr1-390:i386 libwayland-client0:i386
  libwayland-server0:i386 nvidia-390 nvidia-compute-utils-390 nvidia-dkms-390
  nvidia-driver-390 nvidia-kernel-common-390 nvidia-kernel-source-390
  nvidia-prime nvidia-utils-390 xserver-xorg-video-nvidia-390
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,108 B/84.6 MB of archives.
After this operation, 362 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```

---

### Post by takeawaydave on 2019-03-12
Bump - Any suggestions on how to load the legacy driver ?

---

