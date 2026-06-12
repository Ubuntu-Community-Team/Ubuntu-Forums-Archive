---
title: "Ubuntu 14.04 spontaneously reboots usually overnight at random times"
date: 2014-10-08
forum: Hardware
---

### Post by sub13 on 2014-10-08
My 14.04 system spontaneously reboots pretty much every day usually overnight. It is connected to a UPS with USB so the system is aware of the charge state. I have unplugged it just now for 5 minutes and it is depleting at a reasonable rate and my OS knows it is on batteries and has X minutes left. 

Looking at the time when the reboots occur, I see nothing ominous in the syslog or kern.log before the reboot. Is there anywhere else I can look for clues?

I may switch back to 12.04 (multi boot) to see if it goes away. I was getting crashes initially after installing 14.04 with nouveau. So I ran 12.04 for a week with no reboots/problems. Finally I switched to nvidia in 14.04 (offical via apt-get) and system behaved such that it would be up for weeks which is what I have come to expect in GNU/Linux over the > 15 years I have been using this OS.

With my current problem, there seems to be no evidence of a crash. At least Ubuntu is not asking about sending crash reports as it did when I was getting graphics driver crashes which I could also see in the system log. Overnight scenario:  Account locked with home on a hard nfs mount (no autofs), network manager used to manage connection.

---

### Post by ian-weisser on 2014-10-08
Smells like a hardware fault or overheating to me.

---

### Post by weatherman2 on 2014-10-08
Overheating is my first guess too.  It's possible the wrong driver is loaded in 14.04 and doesn't allow the CPU and/or graphics card to run in a power-saving mode and is always running at full speed.

If possible (flash drive install?), I'd install lm-sensors in both 14.04 and 12.04 and compare temperature readings - or in 14.04 see how hot things read.

---

### Post by sub13 on 2014-10-14
Thanks
sudo apt-get -y install lm-sensors
sudo sensors-detect
# Saying yes to monitoring anything related to my video card hangs the system (3 times)


sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +45.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:       +41.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:       +46.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:       +42.0°C  (high = +80.0°C, crit = +100.0°C)

will setup a cron job....

dpkg -l | egrep -i "(nvidia|cuda)"
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
ii  cuda                                                  6.5-14                                              amd64        CUDA meta-package
ii  cuda-6-5                                              6.5-14                                              amd64        CUDA 6.5 meta-package
ii  cuda-command-line-tools-6-5                           6.5-14                                              amd64        CUDA command-line tools
ii  cuda-core-6-5                                         6.5-14                                              amd64        CUDA core tools
ii  cuda-cublas-6-5                                       6.5-14                                              amd64        CUBLAS native runtime libraries
ii  cuda-cublas-dev-6-5                                   6.5-14                                              amd64        CUBLAS native dev links, headers
ii  cuda-cudart-6-5                                       6.5-14                                              amd64        CUDA Runtime native Libraries
ii  cuda-cudart-dev-6-5                                   6.5-14                                              amd64        CUDA Runtime native dev links, headers
ii  cuda-cufft-6-5                                        6.5-14                                              amd64        CUFFT native runtime libraries
ii  cuda-cufft-dev-6-5                                    6.5-14                                              amd64        CUFFT native dev links, headers
ii  cuda-curand-6-5                                       6.5-14                                              amd64        CURAND native runtime libraries
ii  cuda-curand-dev-6-5                                   6.5-14                                              amd64        CURAND native dev links, headers
ii  cuda-cusparse-6-5                                     6.5-14                                              amd64        CUSPARSE native runtime libraries
ii  cuda-cusparse-dev-6-5                                 6.5-14                                              amd64        CUSPARSE native dev links, headers
ii  cuda-documentation-6-5                                6.5-14                                              amd64        CUDA documentation
ii  cuda-driver-dev-6-5                                   6.5-14                                              amd64        CUDA Driver native dev stub library
ii  cuda-drivers                                          340.29-1                                            amd64        CUDA Driver meta-package
ii  cuda-license-6-5                                      6.5-14                                              amd64        CUDA licenses
ii  cuda-misc-headers-6-5                                 6.5-14                                              amd64        CUDA misc headers
ii  cuda-npp-6-5                                          6.5-14                                              amd64        NPP native runtime libraries
ii  cuda-npp-dev-6-5                                      6.5-14                                              amd64        NPP native dev links, headers
ii  cuda-repo-ubuntu1404                                  6.5-14                                              amd64        CUDA repo configuration files.
ii  cuda-runtime-6-5                                      6.5-14                                              amd64        CUDA Runtime 6.5 meta-package
ii  cuda-samples-6-5                                      6.5-14                                              amd64        CUDA example applications
ii  cuda-toolkit-6-5                                      6.5-14                                              amd64        CUDA Toolkit 6.5 meta-package
ii  cuda-visual-tools-6-5                                 6.5-14                                              amd64        CUDA visual tools
ii  libcuda1-340                                          340.29-0ubuntu1                                     amd64        NVIDIA CUDA runtime library
ii  nvidia-340                                            340.29-0ubuntu1                                     amd64        NVIDIA binary driver - version 340.29
ii  nvidia-340-dev                                        340.29-0ubuntu1                                     amd64        NVIDIA binary Xorg driver development files
ii  nvidia-340-uvm                                        340.29-0ubuntu1                                     amd64        NVIDIA Unified Memory kernel module
ii  nvidia-libopencl1-340                                 340.29-0ubuntu1                                     amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-modprobe                                       340.29-0ubuntu1                                     amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-opencl-icd-340                                 340.29-0ubuntu1                                     amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       340.29-0ubuntu1                                     amd64        Tool for configuring the NVIDIA graphics driver

---

