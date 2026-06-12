---
title: "Gutsy  to Hardy upgrade, nvidia-xgl-new does not installs"
date: 2008-05-10
forum: Hardware
---

### Post by mrjobson on 2008-05-10
Hello firends!

I've got a problem that i am not able to resolve. I've tryed to use EnvyNG but it have the same problem.

```
aptitude purge nvidia-glx-new nvidia-settings
The following packages will be REMOVED:
  nvidia-glx-new{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 149620 files and directories currently installed.)
Removing nvidia-glx-new ...
Purging configuration files for nvidia-glx-new ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/nvidia/libGL.so.1.xlibmesa', not allowed
dpkg: error processing nvidia-glx-new (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

Then istallation is the same...

```
Unpacking nvidia-glx-new (from .../nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/nvidia/libglx.so.xserver-xorg-core' with
  different file `/usr/lib/xorg/modules/extensions/libglx.so', not allowed
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by mrjobson on 2008-05-10
i've tryed dpg -i --force-overwrite, but the only one thing helped - i've just renamed files, and everything worked ok! I don;t know why the aptitude could not do it for me...

---

