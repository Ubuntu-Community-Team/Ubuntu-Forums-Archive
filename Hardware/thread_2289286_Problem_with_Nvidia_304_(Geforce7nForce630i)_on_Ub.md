---
title: "Problem with Nvidia 304 (Geforce7/nForce630i) on Ubuntu 15.04"
date: 2015-08-02
forum: Hardware
---

### Post by oneindelijk on 2015-08-02
Hi, 

I've been trying for two days to get Ubuntu to use my monitor in a higher resolution than 640x480 with no avail.

I've tried many things of which I noticed that
 - blacklisting doesn't seem to be working no matter the version of the kernel (tried 3.19.0.15, 3.19.0.25, 4.0.0, 4.1.3, 4.2.0rc4)
 - DKMS does not work for kernel versions higher than the one in the repositories
 - the nouveau driver tries to load even when it's uninstalled

Now I'm stuck at trying to solve this problem ```
insmod nvidia
insmod: ERROR: could not load module nvidia: No such file or directory
``` 
 This is a snippet of my Xorg.0.log
```
root@Jelle-PC:~# grep -E -C3 'nvid|Nvi|NVD|nouv' /var/log/Xorg.0.log
[    26.232] (WW) "xmir" is not to be loaded by default. Skipping.
[    26.232] (II) LoadModule: "glx"
[    26.232] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    26.247] (II) Module glx: vendor="NVIDIA Corporation"
[    26.247] 	compiled for 4.0.2, module version = 1.0.0
[    26.247] 	Module class: X.Org Server Extension
[    26.247] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    26.247] (==) Matched nvidia as autoconfigured driver 0
[    26.247] (==) Matched nouveau as autoconfigured driver 1
[    26.247] (==) Matched modesetting as autoconfigured driver 2
[    26.247] (==) Matched fbdev as autoconfigured driver 3
[    26.247] (==) Matched vesa as autoconfigured driver 4
[    26.247] (==) Assigned the driver to the xf86ConfigLayout
[    26.247] (II) LoadModule: "nvidia"
[    26.247] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    26.248] (II) Module nvidia: vendor="NVIDIA Corporation"
[    26.248] 	compiled for 4.0.2, module version = 1.0.0
[    26.248] 	Module class: X.Org Video Driver
[    26.251] (II) LoadModule: "nouveau"
[    26.251] (WW) Warning, couldn't open module nouveau
[    26.251] (II) UnloadModule: "nouveau"
[    26.251] (II) Unloading nouveau
[    26.251] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    26.251] (II) LoadModule: "modesetting"
[    26.251] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.251] (II) Module modesetting: vendor="X.Org Foundation"
--
[    26.252] 	compiled for 1.17.1, module version = 2.3.3
[    26.252] 	Module class: X.Org Video Driver
[    26.252] 	ABI class: X.Org Video Driver, version 19.0
[    26.252] (==) Matched nvidia as autoconfigured driver 0
[    26.252] (==) Matched nouveau as autoconfigured driver 1
[    26.252] (==) Matched modesetting as autoconfigured driver 2
[    26.252] (==) Matched fbdev as autoconfigured driver 3
[    26.252] (==) Matched vesa as autoconfigured driver 4
[    26.252] (==) Assigned the driver to the xf86ConfigLayout
[    26.252] (II) LoadModule: "nvidia"
[    26.252] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    26.252] (II) Module nvidia: vendor="NVIDIA Corporation"
[    26.252] 	compiled for 4.0.2, module version = 1.0.0
[    26.252] 	Module class: X.Org Video Driver
[    26.252] (II) UnloadModule: "nvidia"
[    26.252] (II) Unloading nvidia
[    26.252] (II) Failed to load module "nvidia" (already loaded, 32763)
[    26.252] (II) LoadModule: "nouveau"
[    26.253] (WW) Warning, couldn't open module nouveau
[    26.253] (II) UnloadModule: "nouveau"
[    26.253] (II) Unloading nouveau
[    26.253] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    26.253] (II) LoadModule: "modesetting"
[    26.253] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.253] (II) Module modesetting: vendor="X.Org Foundation"
--
[    26.254] (II) UnloadModule: "vesa"
[    26.254] (II) Unloading vesa
[    26.254] (II) Failed to load module "vesa" (already loaded, 0)
[    26.254] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    26.254] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    26.254] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.254] (II) FBDEV: driver for framebuffer: fbdev
[    26.254] (II) VESA: driver for VESA chipsets: vesa
--
[    26.255] 	compiled for 1.17.1, module version = 0.0.2
[    26.255] 	ABI class: X.Org Video Driver, version 19.0
[    26.255] (WW) Falling back to old probe method for vesa
[    26.255] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.255] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    26.255] (==) NVIDIA(0): RGB weight 888
[    26.255] (==) NVIDIA(0): Default visual is TrueColor
[    26.255] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    26.255] (**) NVIDIA(0): Enabling 2D acceleration
[    26.260] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    26.260] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    26.260] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    26.260] (EE) NVIDIA(0):  *** Aborting ***
[    26.260] (EE) NVIDIA(0): Failing initialization of X screen 0
[    26.261] (II) UnloadModule: "nvidia"
[    26.261] (II) UnloadSubModule: "wfb"
[    26.261] (II) UnloadSubModule: "fb"
[    26.261] (EE) Screen(s) found, but none have a usable configuration.



```

After every change I made (installing and uninstalling upstream kernels) I ran:
```
apt-get purge nvidia*
apt-get install nvidia-current

```

What else can I try ?

---

### Post by Yellow Pasque on 2015-08-02
> **oneindelijk said:**
> blacklisting doesn't seem to be working no matter the version of the kernel

You shouldn't have to worry about any blacklisting. If you install with a package, it should automatically create the appropriate /etc/modprobe.d/nvidia-graphics-drivers.conf file.

> DKMS does not work for kernel versions higher than the one in the repositories
If you want to use it with 4.x kernels, you need a patched version, such as the one found in Ubuntu 15.10:
```
nvidia-graphics-drivers-304 (304.125-0ubuntu3) wily; urgency=medium
  *  debian/templates/dkms.conf.in,  debian/dkms/patches/buildfix_kernel_4.0.patch:
     - Add support for Linux 4.0.
```

> the nouveau driver tries to load even when it's uninstalled

If you're referring to the portion in the log you gave where it tries to load nouveau, that is expected since X autodetects you have an nvidia card and matches nouveau as a possible driver. As long as X is not assigning a higher priority (lower numbers are higher priority in the log) to nouveau than it is to "nvidia" driver, do not worry about it.


So, to sum it up, get a patched package (or remove 4.x kernels) and come back with updated Xorg log (and/or a build log if the kernel module fails to build).

---

### Post by oneindelijk on 2015-08-02
> **Temüjin said:**
> You shouldn't have to worry about any blacklisting. If you install with a package, it should automatically create the appropriate /etc/modprobe.d/nvidia-graphics-drivers.conf file.

I didn't create any blacklist myself, I noticed these entries where in there, but I wondered why the kernel smees to try to load them anyway

> ** If you want to use it with 4.x kernels, you need a patched version, such as the one found in Ubuntu 15.10:
```
nvidia-graphics-drivers-304 (304.125-0ubuntu3) wily said:**
> 
 I've already uninstalled all upstream kernels, I'm back on 3.19.0-25-generic

[QUOTE= If you're referring to the portion in the log you gave where it tries to load nouveau, that is expected since X autodetects you have an nvidia card and matches nouveau as a possible driver. As long as X is not assigning a higher priority (lower numbers are higher priority in the log) to nouveau than it is to "nvidia" driver, do not worry about it.


 So, to sum it up, get a patched package (or remove 4.x kernels) and come back with updated Xorg log (and/or a build log if the kernel module fails to build). 
The log is from my last attempt (with the 3.19.0-25-generic kernel)

---

### Post by Yellow Pasque on 2015-08-02
Okay, so the first Xorg log you gave was from when you had a 3.19 kernel booted, correct?
I take it you reinstalled the nvidia-current package after removing the 4.x kernel(s), correct?
Is there anything indicating nvidia kernel module build failure in the dkms build logs? (I think nvidia puts them /var/lib/dkms)
Any useful nvidia info in other logs (dmesg, journalctl)?

```
sudo modinfo nvidia
```

---

### Post by oneindelijk on 2015-08-03
dmesg contains this, which I assume is harmless, bumblebee is not installed (and would fail anyway if nvidia fails ?)
```
[    6.055291] systemd[1]: Cannot add dependency job for unit bumblebeed.service, ignoring: Unit bumblebeed.service is masked.[    6.056917] systemd[1]: Cannot add dependency job for unit sddm.service, ignoring: Unit sddm.service is masked.

```
And then 4 lines, information about vesafb, nothing funny there...
journalctl -xn yields very little information this time, only some stuff about the network
neither /var/log/kern.log or /var/log/syslog contain any information about the Video card

Which other logs should I check ?

---

### Post by oneindelijk on 2015-08-03
find /var -name "dkms*" doesn't find a log...

I didn't see any errors when installing nvidia, using my current kernel (I did when I used newer kernels which was related to the patching (as you stated in your first reply)

---

### Post by Yellow Pasque on 2015-08-03
Well, you don't need bumblebee for your GPU, so I'd purge it if possible. If the kernel module built correctly, can you manually load it?
```
sudo modprobe -v nvidia
```

---

### Post by oneindelijk on 2015-08-03
Modprobe/insmod nvidia says: no such file or directory.
I will try the verbose arg and get back to you

---

### Post by oneindelijk on 2015-08-03
Unexpectedly modprobe -v didn't return any errors, so I ran startx.
Here is the output:
```
Welcome to Ubuntu 15.04 (GNU/Linux 3.19.0-25-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Mon Aug  3 12:56:32 2015 from android-737909df4d781833
remadmin@Jelle-PC:~$ sudo -i
[sudo] password for remadmin:
root@Jelle-PC:~# modprobe -v nvidia
root@Jelle-PC:~# startx


X.Org X Server 1.17.1
Release Date: 2015-02-10
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
Current Operating System: Linux Jelle-PC 3.19.0-25-generic #26-Ubuntu SMP Fri Jul 24 21:17:31 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-25-generic root=UUID=21641a6c-d44d-490b-ac6f-9e6da4343676 ro nomodeset=1 drm.debug=0xe plymouth:debug
Build Date: 19 March 2015  09:26:59AM
xorg-server 2:1.17.1-0ubuntu3 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.32.6
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Aug  3 15:34:00 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
NVIDIA: could not open the device file /dev/nvidiactl (No such device or address).
(EE)
Fatal server error:
(EE) no screens found(EE)
(EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
(EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.
```

---

### Post by oneindelijk on 2015-08-03
And ```
root@Jelle-PC:~# systemctl start lightdm
root@Jelle-PC:~# systemctl status lightdm
&#9679; lightdm.service - Light Display Manager
   Loaded: loaded (/lib/systemd/system/lightdm.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/display-manager.service.d
           &#9492;&#9472;xdiagnose.conf
   Active: failed (Result: start-limit) since ma 2015-08-03 15:38:45 CEST; 8s ago
     Docs: man:lightdm(1)
  Process: 30932 ExecStart=/usr/sbin/lightdm (code=exited, status=1/FAILURE)
  Process: 30927 ExecStartPre=/bin/sh -c [ "$(basename $(cat /etc/X11/default-display-manager 2>/dev/null))" = "lightdm" ] (code=exited, status=0/SUCCESS)
 Main PID: 30932 (code=exited, status=1/FAILURE)

aug 03 15:38:45 Jelle-PC systemd[1]: lightdm.servic...aug 03 15:38:45 Jelle-PC systemd[1]: lightdm.servic...aug 03 15:38:45 Jelle-PC systemd[1]: start request ...aug 03 15:38:45 Jelle-PC systemd[1]: Failed to star...aug 03 15:38:45 Jelle-PC systemd[1]: Unit lightdm.s...aug 03 15:38:45 Jelle-PC systemd[1]: Triggering OnF...aug 03 15:38:45 Jelle-PC systemd[1]: lightdm.servic...Hint: Some lines were ellipsized, use -l to show in full.
root@Jelle-PC:~# 
```

---

### Post by oneindelijk on 2015-08-03
Solved !
I did a reboot after that and it worked.
Unity still doesn't want to load, but I will just use gnome instead.
I'm still getting some visual artifacts using x11vnc, but it might be in vnc only. Checking it after dinner ;)
Thanks for your help !

---

