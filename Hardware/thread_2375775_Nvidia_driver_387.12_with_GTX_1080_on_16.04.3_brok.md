---
title: "Nvidia driver 387.12 with GTX 1080 on 16.04.3 broke when some packages updated"
date: 2017-10-27
forum: Hardware
---

### Post by Kimos on 2017-10-27
I am running Ubuntu 16.04 and have been using an Nvidia GTX 1080 and the Nvidia binary drivers for months without issue. But today:

```

sudo aptitude update
sudo aptitude safe-upgrade
```

I didn't watch closely what was upgraded unfortunately. On restart my Nvidia binary graphics drivers stopped working.

I have tried uninstalling and purging the packages. I added the PPA and installed the newest drivers from there. I also then force installed older versions (384 and 375). I tried booting to older kernel versions from GRUB too.

It appears I have no `xorg.conf` file and it is loading the failsafe with `nouveau`. But generating a new file fails, details below.

It has been a long while since I have had to troubleshoot graphics drivers and I'm out of ideas. Here's everything I think may be useful:

```

~ uname -a                  
Linux onyx 4.4.0-97-generic #120-Ubuntu SMP Tue Sep 19 17:28:18 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

```

~ aptitude search nvidia | grep "^i"
i   nvidia-387                      - NVIDIA binary driver - version 387.12     
i A nvidia-opencl-icd-387           - NVIDIA OpenCL ICD                         
i A nvidia-prime                    - Tools to enable NVIDIA's Prime            
i A nvidia-settings                 - Tool for configuring the NVIDIA graphics d
```

```

~ modprobe -r nvidia
rmmod: ERROR: Module nvidia_uvm is not currently loaded
rmmod: ERROR: Module nvidia is in use by: nvidia_modeset
modprobe: FATAL: Error running remove command for nvidia
```

```

~ inxi -Fxz
Graphics:  Card: NVIDIA Device 1b80 bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: fbdev (unloaded: vesa) FAILED: nouveau
           Resolution: 1024x768@76.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 4.0, 256 bits)
           GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
```

```

~ sudo X -configure
X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
Current Operating System: Linux onyx 4.4.0-97-generic #120-Ubuntu SMP Tue Sep 19 17:28:18 UTC 2017 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-97-generic.efi.signed root=UUID=2cc2b13d-0c79-47e8-868e-88057e58ab5e ro quiet splash vt.handoff=7
Build Date: 13 October 2017  01:57:05PM
xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
  Before reporting problems, check http://wiki.x.org
  to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
  (++) from command line, (!!) notice, (II) informational,
  (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 26 22:41:39 2017
List of video drivers:
  amdgpu
  ati
  intel
  nouveau
  qxl
  radeon
  vmware
  vesa
  fbdev
  modesetting
(++) Using config file: "/home/kevin/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
(EE) Server terminated with error (2). Closing log file.
```

```

~ vi /var/log/Xorg.0.log
[     3.868] (II) LoadModule: "glx"
[     3.869] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.876] (II) Module glx: vendor="X.Org Foundation"
[     3.876]    compiled for 1.18.4, module version = 1.0.0
[     3.876]    ABI class: X.Org Server Extension, version 9.0
[     3.876] (==) AIGLX enabled
[     3.876] (==) Matched nvidia as autoconfigured driver 0
[     3.876] (==) Matched nouveau as autoconfigured driver 1
[     3.876] (==) Matched nvidia as autoconfigured driver 2
[     3.876] (==) Matched nouveau as autoconfigured driver 3
[     3.876] (==) Matched modesetting as autoconfigured driver 4
[     3.876] (==) Matched fbdev as autoconfigured driver 5
[     3.876] (==) Matched vesa as autoconfigured driver 6
[     3.876] (==) Assigned the driver to the xf86ConfigLayout
[     3.876] (II) LoadModule: "nvidia"
[     3.876] (WW) Warning, couldn't open module nvidia
[     3.876] (II) UnloadModule: "nvidia"
[     3.876] (II) Unloading nvidia
[     3.876] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     3.876] (II) LoadModule: "nouveau"
```

```

~ dkms status
bbswitch, 0.8, 4.4.0-97-generic, x86_64: installed
nvidia-387, 387.12, 4.4.0-97-generic, x86_64: installed
```

```

~ ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00001B80sv00001462sd00003362bc03sc00i00
driver   : nvidia-384 - distro non-free
driver   : nvidia-387 - third-party free recommended
driver   : nvidia-378 - third-party free
driver   : nvidia-381 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin
```

```

~ nvidia-settings 
ERROR: Error querying enabled displays on GPU 0 (Missing Extension).
ERROR: Error querying connected displays on GPU 0 (Missing Extension).

** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should have been installed along
       with this driver at /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be prepopulated or validated, and
       will not be listed in the help text. Please see the README for possible values and descriptions.
```

```

~ cat /etc/modprobe.d/* | grep nouveau
# do not automatically load nouveau as it may prevent nvidia from loading
blacklist nouveau
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau offoptions vmwgfx enable_fbdev=1
```

---

### Post by efflandt on 2017-10-27
I don't have aptitude installed, but safe-upgrade is similar to apt or apt-get upgrade in that it only upgrades existing packages and might not include packages with changing dependencies. So that may have broken something by retaining something incompatible with some other upgrade. Web searching a Debian manual for aptitude, under **safe-upgrade** says:

"It is sometimes necessary to remove one package in order 	      to upgrade another; this command is not able to upgrade 	      packages in such situations.  Use the [full-upgrade]("https://aptitude.alioth.debian.org/doc/en/rn01re01.html#manpageFullUpgrade") 	      command to upgrade as many packages as possible."

Similarly I always though it was smarter for apt or apt-get to use **dist-upgrade** instead of **upgrade** because upgrade may hold packages back that have dependency changes and dist-upgrade is smarter about coordinating everything. But I normally simply use Ubuntu Software Updater, so I did not really pay attention to that other than for Debian on a Raspberry Pi.

---

### Post by Kimos on 2017-10-27
I found there's an apt log that has the packages that changed. Narrows it a bit, but it's a huge list. I can start reverting some of these I guess:

```

Start-Date: 2017-10-26  18:13:54
Requested-By: kevin (1000)
Install: primus-libs:amd64 (0~20150328-1, automatic), primus-libs:i386 (0~20150328-1, automatic), libcuda1-384:amd64 (384.90-0ubuntu0.16.04.1, automatic), primus:amd64 (0~20150328-1, automatic), python-enum34:amd64 (1.1.2-1, automatic), python-cryptography:amd64 (1.2.3-1ubuntu0.1, automatic), python-cffi-backend:amd64 (1.5.2-1ubuntu1, automatic), python-ipaddress:amd64 (1.0.16-1, automatic), primus-libs-ia32:i386 (0~20150328-1, automatic), python-pyasn1:amd64 (0.1.9-1, automatic), bumblebee:amd64 (3.2.1-10, automatic), python-idna:amd64 (2.0-3, automatic), xserver-xorg-legacy-hwe-16.04:amd64 (2:1.19.3-1ubuntu1~16.04.4, automatic), bbswitch-dkms:i386 (0.8-3ubuntu1, automatic), nvidia-opencl-icd-384:amd64 (384.90-0ubuntu0.16.04.1, automatic), nvidia-384:amd64 (384.90-0ubuntu0.16.04.1, automatic), socat:amd64 (1.7.3.1-1, automatic)
Upgrade: libmpx0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libgcc-5-dev:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libgles2-mesa:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libcurl3:amd64 (7.47.0-1ubuntu2.3, 7.47.0-1ubuntu2.4), mysql-client-5.7:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), libgnutls-openssl27:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), mysql-server-5.7:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), libmysqlclient-dev:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), libsystemd0:amd64 (229-4ubuntu19, 229-4ubuntu20), libsystemd0:i386 (229-4ubuntu19, 229-4ubuntu20), adobe-flash-properties-gtk:amd64 (1:20170912.1-0ubuntu0.16.04.1, 1:20171025.1-0ubuntu0.16.04.1), libpulsedsp:amd64 (1:8.0-0ubuntu3.3, 1:8.0-0ubuntu3.4), grub-common:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), libcuda1-375:amd64 (375.66-0ubuntu0.16.04.1, 384.90-0ubuntu0.16.04.1), pulseaudio:amd64 (1:8.0-0ubuntu3.3, 1:8.0-0ubuntu3.4), cpp-5:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libglapi-mesa:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libglapi-mesa:i386 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), mysql-server:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), dolphin-emu-data-master:amd64 (5.0+git-r201709062349-c97a799-32~ubuntu16.04.1, 5.0+git-r201710261918-802fda2-33~ubuntu16.04.1), libicu55:amd64 (55.1-7ubuntu0.2, 55.1-7ubuntu0.3), libicu55:i386 (55.1-7ubuntu0.2, 55.1-7ubuntu0.3), binutils:amd64 (2.26.1-1ubuntu1~16.04.4, 2.26.1-1ubuntu1~16.04.5), mysql-client:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), libitm1:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), gnome-software:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6), slack-desktop:amd64 (2.8.0, 2.8.2), google-chrome-stable:amd64 (61.0.3163.91-1, 62.0.3202.75-1), libpython3.5:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.3), python3.5:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.3), libxatracker2:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), plymouth-label:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), python3.5-minimal:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.3), grub2-common:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), udev:amd64 (229-4ubuntu19, 229-4ubuntu20), libcilkrts5:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libegl1-mesa:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), plymouth-theme-ubuntu-text:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), libasan2:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libc++1:amd64 (3.7.0-1, 3.7.0-1ubuntu0.1), libquadmath0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), dkms:amd64 (2.2.0.3-2ubuntu11.3, 2.2.0.3-2ubuntu11.5), initramfs-tools-bin:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), libudev1:amd64 (229-4ubuntu19, 229-4ubuntu20), libudev1:i386 (229-4ubuntu19, 229-4ubuntu20), libgbm1:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), adobe-flashplugin:amd64 (1:20170912.1-0ubuntu0.16.04.1, 1:20171025.1-0ubuntu0.16.04.1), libplymouth4:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), gcc-5-base:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), gcc-5-base:i386 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), mysql-client-core-5.7:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), libstdc++-5-dev:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libtsan0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), grub-efi-amd64-bin:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), libubsan0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libpulse0:amd64 (1:8.0-0ubuntu3.3, 1:8.0-0ubuntu3.4), libpulse0:i386 (1:8.0-0ubuntu3.3, 1:8.0-0ubuntu3.4), g++-5:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), ubuntu-software:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6), chromium-browser:amd64 (61.0.3163.100-0ubuntu0.16.04.1306, 62.0.3202.62-0ubuntu0.16.04.1308), libgfortran3:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libpulse-mainloop-glib0:amd64 (1:8.0-0ubuntu3.3, 1:8.0-0ubuntu3.4), systemd-sysv:amd64 (229-4ubuntu19, 229-4ubuntu20), chromium-codecs-ffmpeg-extra:amd64 (61.0.3163.100-0ubuntu0.16.04.1306, 62.0.3202.62-0ubuntu0.16.04.1308), libwayland-egl1-mesa:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), gcc-5:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libpam-systemd:amd64 (229-4ubuntu19, 229-4ubuntu20), distro-info-data:amd64 (0.28ubuntu0.3, 0.28ubuntu0.5), liblsan0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), systemd:amd64 (229-4ubuntu19, 229-4ubuntu20), libgomp1:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libwebkit2gtk-4.0-37:amd64 (2.16.6-0ubuntu0.16.04.1, 2.18.0-0ubuntu0.16.04.2), mysql-common:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), libgl1-mesa-dri:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libgl1-mesa-dri:i386 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), grub-efi-amd64:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), libosmesa6:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libosmesa6:i386 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libmysqlclient20:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), plymouth:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), pulseaudio-module-x11:amd64 (1:8.0-0ubuntu3.3, 1:8.0-0ubuntu3.4), libgl1-mesa-glx:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libgl1-mesa-glx:i386 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), grub-efi-amd64-signed:amd64 (1.66.12+2.02~beta2-36ubuntu3.12, 1.66.14+2.02~beta2-36ubuntu3.14), gir1.2-webkit2-4.0:amd64 (2.16.6-0ubuntu0.16.04.1, 2.18.0-0ubuntu0.16.04.2), libgnutls30:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), libgnutls30:i386 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), unattended-upgrades:amd64 (0.90ubuntu0.7, 0.90ubuntu0.8), pulseaudio-module-bluetooth:amd64 (1:8.0-0ubuntu3.3, 1:8.0-0ubuntu3.4), libicu-dev:amd64 (55.1-7ubuntu0.2, 55.1-7ubuntu0.3), wget:amd64 (1.17.1-1ubuntu1.2, 1.17.1-1ubuntu1.3), mesa-vdpau-drivers:amd64 (17.0.7-0ubuntu0.16.04.1, 17.0.7-0ubuntu0.16.04.2), libpython3.5-stdlib:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.3), linux-firmware:amd64 (1.157.12, 1.157.13), libatomic1:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libcc1-0:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), plymouth-theme-ubuntu-logo:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), icu-devtools:amd64 (55.1-7ubuntu0.2, 55.1-7ubuntu0.3), dolphin-emu-master:amd64 (5.0+git-r201709062349-c97a799-32~ubuntu16.04.1, 5.0+git-r201710261918-802fda2-33~ubuntu16.04.1), chromium-browser-l10n:amd64 (61.0.3163.100-0ubuntu0.16.04.1306, 62.0.3202.62-0ubuntu0.16.04.1308), ansible:amd64 (2.3.2.0-1ppa~xenial, 2.4.1.0-1ppa~xenial), libpython3.5-minimal:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.3), libstdc++6:amd64 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), libstdc++6:i386 (5.4.0-6ubuntu1~16.04.4, 5.4.0-6ubuntu1~16.04.5), pulseaudio-utils:amd64 (1:8.0-0ubuntu3.3, 1:8.0-0ubuntu3.4), curl:amd64 (7.47.0-1ubuntu2.3, 7.47.0-1ubuntu2.4), gnome-software-common:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6), libjavascriptcoregtk-4.0-18:amd64 (2.16.6-0ubuntu0.16.04.1, 2.18.0-0ubuntu0.16.04.2), mysql-server-core-5.7:amd64 (5.7.19-0ubuntu0.16.04.1, 5.7.20-0ubuntu0.16.04.1), spotify-client:amd64 (1:1.0.49.125.g72ee7853-111, 1:1.0.64.407.g9bd02c2d-26), initramfs-tools-core:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), libcurl3-gnutls:amd64 (7.47.0-1ubuntu2.3, 7.47.0-1ubuntu2.4), nvidia-375:amd64 (375.66-0ubuntu0.16.04.1, 384.90-0ubuntu0.16.04.1), initramfs-tools:amd64 (0.122ubuntu8.8, 0.122ubuntu8.9), libwebkit2gtk-4.0-37-gtk2:amd64 (2.16.6-0ubuntu0.16.04.1, 2.18.0-0ubuntu0.16.04.2), gir1.2-javascriptcoregtk-4.0:amd64 (2.16.6-0ubuntu0.16.04.1, 2.18.0-0ubuntu0.16.04.2)
Remove: xserver-xorg-legacy:amd64 (2:1.18.4-0ubuntu0.7), nvidia-prime:amd64 (0.8.2), libxnvctrl0:amd64 (361.42-0ubuntu1), screen-resolution-extra:amd64 (0.17.1), libjansson4:amd64 (2.7-3), bbswitch-dkms:amd64 (0.8-3ubuntu1), nvidia-opencl-icd-375:amd64 (375.66-0ubuntu0.16.04.1), nvidia-settings:amd64 (361.42-0ubuntu1)
End-Date: 2017-10-26  18:20:03

```

---

### Post by ajgreeny on 2017-10-27
Just for information:

For a complete dependency check during upgrade using **apt** or **apt-get**, you need to use either **apt full-upgrade** or if you prefer apt-get you must use **apt-get dist-upgrade**.

The two apt variations (full vs dist) of the command are not interchangeable, but as far as I can make out the two commands do the same job; I'm sure someone will tell us both if I have got that wrong in any way.

---

### Post by Kimos on 2017-10-27
I'm going to say this is solved, but I don't actually know what the problem is. I just figured out how to go back to the older version that works.

I needed to put back `nvidia-375`, but the original packages I had aren't available anymore. So I downloaded them as debs:

```

wget https://launchpad.net/ubuntu/+archive/primary/+files/nvidia-opencl-icd-375_375.66-0ubuntu0.16.04.1_amd64.deb
wget https://launchpad.net/ubuntu/+archive/primary/+files/nvidia-375_375.66-0ubuntu0.16.04.1_amd64.deb
```

Then installed the specific older versions of the dependencies:
```

sudo aptitude install xserver-xorg-legacy:amd64=2:1.18.4-0ubuntu0.7 dkms:amd64=2.2.0.3-2ubuntu11.3
```

Then manually install the debs:
```

sudo dpkg -i nvidia-375_375.66-0ubuntu0.16.04.1_amd64.deb nvidia-opencl-icd-375_375.66-0ubuntu0.16.04.1_amd64.deb

```

I'm going to try pinning the versions so they don't get updated next time.

---

