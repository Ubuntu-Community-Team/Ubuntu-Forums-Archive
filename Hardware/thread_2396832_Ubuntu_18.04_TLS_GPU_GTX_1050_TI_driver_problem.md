---
title: "Ubuntu 18.04 TLS GPU GTX 1050 TI driver problem"
date: 2018-07-21
forum: Hardware
---

### Post by xman176 on 2018-07-21
Hello,
I download and install ubuntu 18.04 TLS 'Bionic Beaver' on my Laptop. I don't have any problem with installation. But when I first start ubuntu, the display froze after 1 or 2 minutes.
I tried to switch to another tty but with out result. If I start computer and change to tty2 berfore froze, system writing some messages about nouveau. If I run ubuntu in recovery mode it work normal with out freezing.

Now I run on ubuntu but I add to grub parameter nomodeset. It does not freeze but I cant connect display by HDMI cable. I tried to find some solution of this problem on the internet but with out result.
I tried this solutions:
Reinstall GPU driver (Download driver from official web side, using nvidia-390 or nvidia-396)
Disable nouveau in startup (That help to get longer time with out freezeng GUI)
Repair nvidia-setting, (If use command nvidia-detector result of application is none)

I have laptop Acer Nitro 5 (i7-8750H, 16GB RAM, nvidia 1050Ti).


Thanks for any help.

---

### Post by Bashing-om on 2018-07-21
Hello xman176, Welcome to the forum :)

In 18.04 IF you are have Wayland as the desktop environment - nvidia graphics is a work in progress.
Let's look at what we are working with.
post back - Between code tags - the outputs of terminal commands:
```

ps -efly | grep Xorg
systemctl status gdm
echo $XDG_SESSION_TYPE
dpkg -l | grep -i nvidia
lsmod | grep nouveau

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once we know we can develop that plan of action.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2018-07-21
Can you hear the fan working properly? Are you sure it's not overheating?

---

### Post by xman176 on 2018-07-22
Hello,
Yes I hear fan, it is working properly. I have a new laptop and I using dual boot ubuntu and Windows. In windows I don't have any problems.

---

### Post by xman176 on 2018-07-22
Hello,
I send result of all commands. 

```

stepan@stepan-NTB:~$ ps -efly | grep Xorg
S  root      1026  1024  0  80   0 48256 314000 -     16:46 tty1      00:00:00 /usr/lib/xorg/Xorg vt1 -displayfd 3 -auth  /run/user/120/gdm/Xauthority -background none -noreset -keeptty -verbose  3
S root      1448  1446  7  80   0 129004 336753 -    16:46  tty2     00:00:09 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth  /run/user/1000/gdm/Xauthority -background none -noreset -keeptty  -verbose 3

```

```

stepan@stepan-NTB:~$ systemctl status gdm
&#9679; gdm.service - GNOME Display Manager
   Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabled)
   Active: active (running) since Sun 2018-07-22 16:46:44 CEST; 4min 7s ago
  Process: 936 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)
 Main PID: 943 (gdm3)
    Tasks: 3 (limit: 4915)
   CGroup: /system.slice/gdm.service
           &#9492;&#9472;943 /usr/sbin/gdm3

&#269;ec 22 16:46:44 stepan-NTB systemd[1]: Started GNOME Display Manager.
&#269;ec  22 16:46:45 stepan-NTB gdm-launch-environment][949]:  pam_unix(gdm-launch-environment:session): session opened for user gdm by  (uid=0)
&#269;ec 22 16:46:45 stepan-NTB gdm-launch-environment][949]: pam_unix(gdm-launch-environment:session): session closed for user gdm
&#269;ec 22 16:46:45 stepan-NTB gdm3[943]: GdmDisplay: display lasted 0,281007 seconds
&#269;ec 22 16:46:45 stepan-NTB gdm3[943]: Child process -970 was already dead.
&#269;ec 22 16:46:45 stepan-NTB gdm3[943]: Child process 949 was already dead.
&#269;ec 22 16:46:45 stepan-NTB gdm3[943]: Unable to kill session worker process
&#269;ec  22 16:46:45 stepan-NTB gdm-launch-environment][1007]:  pam_unix(gdm-launch-environment:session): session opened for user gdm by  (uid=0)
&#269;ec 22 16:46:52 stepan-NTB gdm-password][1280]:  pam_unix(gdm-password:auth): authentication failure; logname= uid=0  euid=0 tty=/dev/tty1 ruser= rhost=  user=stepan
&#269;ec 22 16:47:00 stepan-NTB gdm-password][1425]: pam_unix(gdm-password:session): session opened for user stepan by (uid=0)

```

```

stepan@stepan-NTB:~$ echo $XDG_SESSION_TYPE
x11

```

```

stepan@stepan-NTB:~$ dpkg -l | grep -i nvidia
ii   libnvidia-cfg1-396:amd64                    396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA binary  OpenGL/GLX configuration library
ii   libnvidia-common-390                        390.77-0ubuntu0~gpu18.04.1          all          Shared files used by  the NVIDIA libraries
ii  libnvidia-common-396                        396.24.10-0ubuntu0~gpu18.04.1       all          Shared files used by  the NVIDIA libraries
rc  libnvidia-compute-390:amd64                390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                 390.77-0ubuntu0~gpu18.04.1          i386         NVIDIA libcompute package
ii  libnvidia-compute-396:amd64                396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386                 396.24.10-0ubuntu0~gpu18.04.1       i386         NVIDIA libcompute package
ii   libnvidia-decode-396:amd64                  396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA Video Decoding  runtime libraries
ii  libnvidia-decode-396:i386                   396.24.10-0ubuntu0~gpu18.04.1       i386         NVIDIA Video Decoding  runtime libraries
ii  libnvidia-encode-396:amd64                  396.24.10-0ubuntu0~gpu18.04.1       amd64        NVENC Video Encoding  runtime library
ii  libnvidia-encode-396:i386                   396.24.10-0ubuntu0~gpu18.04.1       i386         NVENC Video Encoding  runtime library
ii  libnvidia-fbc1-396:amd64                    396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA OpenGL-based  Framebuffer Capture runtime library
ii   libnvidia-fbc1-396:i386                     396.24.10-0ubuntu0~gpu18.04.1       i386         NVIDIA OpenGL-based  Framebuffer Capture runtime library
ii   libnvidia-gl-396:amd64                      396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA  OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii   libnvidia-gl-396:i386                       396.24.10-0ubuntu0~gpu18.04.1       i386         NVIDIA  OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii   libnvidia-ifr1-396:amd64                    396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA OpenGL-based  Inband Frame Readback runtime library
ii   libnvidia-ifr1-396:i386                     396.24.10-0ubuntu0~gpu18.04.1       i386         NVIDIA OpenGL-based  Inband Frame Readback runtime library
rc  nvidia-compute-utils-390                   390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-396                   396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA compute utilities
rc  nvidia-dkms-390                            390.77-0ubuntu0~gpu18.04.1          amd64        NVIDIA DKMS package
ii  nvidia-dkms-396                            396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA DKMS package
ii  nvidia-driver-396                          396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA driver metapackage
rc   nvidia-kernel-common-390                    390.77-0ubuntu0~gpu18.04.1          amd64        Shared files used with  the kernel module
ii  nvidia-kernel-common-396                    396.24.10-0ubuntu0~gpu18.04.1       amd64        Shared files used with  the kernel module
ii  nvidia-kernel-source-396                   396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.8                               all          Tools to enable NVIDIA's Prime
ii   nvidia-settings                             396.24-0ubuntu0~gpu18.04.1          amd64        Tool for configuring  the NVIDIA graphics driver
ii  nvidia-utils-396                           396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396              396.24.10-0ubuntu0~gpu18.04.1       amd64        NVIDIA binary Xorg driver

```

```

stepan@stepan-NTB:~$ lsmod | grep nouveau
nouveau              1716224  0
mxm_wmi                16384  1 nouveau
ttm                   106496  1 nouveau
wmi                    24576  5 wmi_bmof,intel_wmi_thunderbolt,acer_wmi,mxm_wmi,nouveau
i2c_algo_bit           16384  2 nouveau,i915
drm_kms_helper        172032  2 nouveau,i915
drm                   401408  4 nouveau,i915,ttm,drm_kms_helper
video                  45056  3 acer_wmi,nouveau,i915

```

All commands have been executed properly.
Thanks for help

---

### Post by Bashing-om on 2018-07-22
xman176; Hummm ..

Well, nouveau is also active as well as the nvidia drivet. As to why - I am having to do homework as in 18.04+ blacklisting is not as was formerly done.
for your reference: my system:
{
> 
sysop@x1810:/$ sudo lshw -C display
[sudo] password for sysop: 
  *-display                 
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:c0000-dffff
sysop@x1810:/$

sysop@x1810:/$ ps -efly | grep Xorg
S root       726   713  3  80   0 79160 87033 -      14:22 tty7     00:11:26 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
S sysop     4312  1402  0  80   0  1088  5500 pipe_w 20:03 pts/1    00:00:00 grep --color=auto Xorg
sysop@x1810:/$ 

sysop@x1810:/$ lsmod | grep nouveau
sysop@x1810:/$

}

Now formerly we could expect that the nouveau driver to be "blacklisted" in the /etc/modprobe.d/ directory.
Proof that it is no longer the case: my result:
> 
sysop@x1810:/$ ls -al /etc/modprobe.d/
total 60
drwxr-xr-x   2 root root  4096 Jul 21 01:42 .
drwxr-xr-x 131 root root 12288 Jul 22 14:23 ..
-rw-r--r--   1 root root  2507 Jul 30  2015 alsa-base.conf
-rw-r--r--   1 root root   154 May 25 13:38 amd64-microcode-blacklist.conf
-rw-r--r--   1 root root   325 Jan 28 09:34 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Jan 28 09:34 blacklist.conf
-rw-r--r--   1 root root   210 Jan 28 09:34 blacklist-firewire.conf
-rw-r--r--   1 root root   697 Jan 28 09:34 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Jul 30  2015 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 May 20 12:47 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Jan 28 09:34 blacklist-rare-network.conf
-rw-r--r--   1 root root   127 Feb  7  2017 dkms.conf
-rw-r--r--   1 root root   154 May  3 14:45 intel-microcode-blacklist.conf
-rw-r--r--   1 root root   347 Jan 28 09:34 iwlwifi.conf
sysop@x1810:/$ 


And nope, not blacklisted in the blacklist.conf file either:
> 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


I no longer know how nvidia takes care of nouveau.

While I learn
How about in this case we purge the nvidia driver and return to nouveau?
Once stable on nouveau then see what results in a controlled install of the nvidia driver ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2018-07-24
xman176; Update .

Blacklisting is now done (18.10) in the /lib/modprobe.d directory:
> 
sysop@x1810:~$ ls -al /lib/modprobe.d
total 32
drwxr-xr-x  2 root root 4096 Jul  7 12:25 .
drwxr-xr-x 21 root root 4096 Jun 16 22:27 ..
-rw-r--r--  1 root root  655 May 28 08:12 aliases.conf
-rw-r--r--  1 root root 1461 May 15 00:41 blacklist_linux_4.15.0-22-generic.conf
-rw-r--r--  1 root root 1461 May 23 11:54 blacklist_linux_4.15.0-23-generic.conf
-rw-r--r--  1 root root  390 Apr 20 11:55 fbdev-blacklist.conf
-rw-r--r--  1 root root   81 Jun  6 08:43 nvidia-graphics-drivers.conf
-rw-r--r--  1 root root  765 Jan 28 09:58 systemd.conf
sysop@x1810:~$


when  you are ready to continue ...

[INDENT][INDENT]see now what we can learn
[/INDENT][/INDENT]

---

