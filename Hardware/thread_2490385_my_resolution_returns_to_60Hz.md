---
title: "my resolution returns to 60Hz"
date: 2023-09-01
forum: Hardware
---

### Post by yann20 on 2023-09-01
Hello everyone.
I have ubuntu 22.04 with a gtx1060 6GB graphics card. Drivers 535.86.05.
I'm writing to you because my resolution returns to 60Hz as soon as I switch off my screen. I've set the display to 165HZ, which is the maximum refresh rate.
I've saved my conf in /etc/X11/xorg.conf.
Any idea please?
Thanks a lot.

05:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] [10de:1c03] (rev a1) (prog-if 00 [VGA controller])
05:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] [10de:1c03] (rev a1) (prog-if 00 [VGA controller])
root@yann-B450-AORUS-ELITE:~# lspci -vnn | grep -A 12 '\''[030[02]\]' | grep -Ei "vga|3d|display|kernel"
05:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106 [GeForce GTX 1060 6GB] [10de:1c03] (rev a1) (prog-if 00 [VGA controller])
root@yann-B450-AORUS-ELITE:~# ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:02.1/0000:01:00.2/0000:02:04.0/0000:05:00.0 ==
modalias : pci:v000010DEd00001C03sv000010DEsd000011D7bc03sc00i00
vendor   : NVIDIA Corporation
model    : GP106 [GeForce GTX 1060 6GB]
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-535 - distro non-free recommended
driver   : nvidia-driver-525-server - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-525 - distro non-free
driver   : nvidia-driver-535-server - distro non-free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
Linux yann-B450-AORUS-ELITE 6.2.0-31-generic #31~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Aug 16 13:45:26 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 544mm x 303mm
   1920x1080     60.00*+ 165.00   143.98   119.88   100.00    59.94    50.00    29.97    25.00    23.98  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024    119.96    75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1024x768     143.93   119.99    75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-1 disconnected (normal left inverted right x axis y axis)
ii  libnvidia-cfg1-535:amd64                   535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-535                       535.86.05-0ubuntu0.22.04.1                  all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-535:amd64                535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA libcompute package
ii  libnvidia-compute-535:i386                 535.86.05-0ubuntu0.22.04.1                  i386         NVIDIA libcompute package
ii  libnvidia-decode-535:amd64                 535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-535:i386                  535.86.05-0ubuntu0.22.04.1                  i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-535:amd64                 535.86.05-0ubuntu0.22.04.1                  amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-535:i386                  535.86.05-0ubuntu0.22.04.1                  i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-535:amd64                  535.86.05-0ubuntu0.22.04.1                  amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-535:amd64                   535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-535:i386                    535.86.05-0ubuntu0.22.04.1                  i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-535:amd64                     535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-535:i386                      535.86.05-0ubuntu0.22.04.1                  i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  nvidia-compute-utils-535                   535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA compute utilities
ii  nvidia-dkms-535                            535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA DKMS package
ii  nvidia-driver-535                          535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA driver metapackage
ii  nvidia-firmware-535-535.86.05              535.86.05-0ubuntu0.22.04.1                  amd64        Firmware files used by the kernel module
ii  nvidia-kernel-common-535                   535.86.05-0ubuntu0.22.04.1                  amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-535                   535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.17.1                                    all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            510.47.03-0ubuntu1                          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-535                           535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18.2                                      all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-535              535.86.05-0ubuntu0.22.04.1                  amd64        NVIDIA binary Xorg driver
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom                                        Version                                     Architecture Description
+++-==========================================-===========================================-============-=========================================================================================================================================================================
rc  privoxy                                    3.0.33-1build1                              amd64        Privacy enhancing HTTP Proxy
rc  transmission-gtk                           3.00-2ubuntu2                               amd64        lightweight BitTorrent client (GTK+ interface)

---

### Post by yann20 on 2023-09-01
I switched from a DisplayPort cable to an HDMI cable. 
On the HDMI, I stay at 165 Hz.

---

### Post by Autodave on 2023-09-01
You can also try going back to the 525 nVidia driver: there have been tons of issues with the 535 driver.

---

### Post by yann20 on 2023-09-02
Thanks, I'll take a look.

---

