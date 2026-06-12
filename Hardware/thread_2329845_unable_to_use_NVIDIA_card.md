---
title: "unable to use NVIDIA card"
date: 2016-07-05
forum: Hardware
---

### Post by coffee.guy on 2016-07-05
I have a acer laptop with a NVIDIA GT 55M, which is not used by Ubuntu. Indeed in system setting it tells "Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits)" which I assume is the integrated graphic card.
While it's ok for a low usage, it's really bad playing videos, even with a poor 720p .

I'm not sure if the problem is about drivers, settings, or whatever. Trying to have it working I played with drivers, grub configuration, optimum and prime, but it still doesn't work.
According to system setting I'm currently using NVIDIA binary driver - version 352.63 from nvidia-352-updates.

Any help would be really appreciated.

I can post output of a few commands, but I'm sure that there are many that I don't even know. Just ask and I'll try them and add their outputs.

$ lspci | grep 'VGA' ```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106M [GeForce GT 555M] (rev ff)

```

$ optirun glxgears ```
 
[ 3289.867707] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 3289.867864] [ERROR]Aborting because fallback start is disabled.


```

$ nvidia-settings```

** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no  

/**Other stuff not relevant**/

```

---

### Post by Bashing-om on 2016-07-05
coffee.guy; Hello: Welcome to the forum .

Nvidia recommends the 367 version driver for this card and As this is a hybrid graphic's set, we also want nvidia-prime as the controller.
[http://www.nvidia.com/download/driverResults.aspx/104284/en-us](http://www.nvidia.com/download/driverResults.aspx/104284/en-us)
Now, IF and I do say IF the 367 version driver is what is required, it is only available in the 16.04 release.
What release do you have installed ?
In addition, if we go with the 367 version driver, it is available from our trusted PPA  for release 16.04 .... will have to install the PPA source .

The good thing here is that the card is supported !

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-06
Thank you for the answer. I'm going to upgrade to 16.04 in a few days.

Regarding the installation of the driver, I have two question. Are you talking about this PPA[ ]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa")[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)? And do you suggest to purge every NVIDIA stuff, and install only nvidia-graphics-drivers-367, or the purge is not necessary?

---

### Post by Bashing-om on 2016-07-06
coffee.guy; Yeah ,

You have the right of it . That is the PPA I had in mind;
And yes.. will want to purge all the old nvidia stuff, If you installed from Nvidia site, gets a bit more complicated to purge.
You can try the driver ( 364 ) that is available in our software repository in 16.04, wont hurt a thing to see what results before going to the PPA for the 367 version.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-08
Ok, I finally did the upgrade, and the first thing i had to do was purge nvidia* , as I had a familiar login loop (the one in which you insert the right password, the screen goes black and bring you back to the login).

After the purge I tried installing nvidia-364, but the latest available was 361, so I gave it a try. 
The outcome was the usual login loop. I tried running 
 ```
$ sudo update-alternatives --config  x86_64-linux-gnu_gl_conf 
```
and tried all the possibilities. All of them led to the login loop.
The only "fix" is purge nvidia.

So I added the PPA and tried installing nvidia-364. 
As with 361 I had the login loop with every possibility I could set.

Purged again and installed 367. Same outcome of 361 or 364.

Am I missing something?

---

### Post by Bashing-om on 2016-07-08
coffee.guy; Humm ...

Authority to access your GUI ?
What returns:
```

ls -al /home/<user_name>

```

As just
[INDENT][INDENT]one other thought
[/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-10
$ ls -al /home/<user_name>
```
drwxr-xr-x 52 filippo filippo   4096 lug 10 10:05 .
drwxr-xr-x  4 root    root      4096 ott 26  2014 ..
drwx------  3 filippo filippo   4096 ott 26  2014 .adobe
drwxrwxr-x  5 filippo filippo   4096 giu 24 11:52 .android
drwxrwxr-x  3 filippo filippo   4096 giu 23 17:44 Android
drwxrwxr-x  7 filippo filippo   4096 giu 23 17:38 android-studio
drwxrwxr-x  4 filippo filippo   4096 giu 23 17:39 .AndroidStudio2.1
drwxrwxr-x  5 filippo filippo   4096 giu 27 10:45 AndroidStudioProjects
-rw-rw-r--  1 filippo filippo 384939 mar  9  2015 astrazione.mp3
drwxrwxr-x  3 filippo filippo   4096 feb 23 11:15 .audacity-data
-rw-------  1 filippo filippo  59155 lug 10 10:08 .bash_history
-rw-r--r--  1 filippo filippo    220 ott 26  2014 .bash_logout
-rw-r--r--  1 filippo filippo   3760 ott 26  2014 .bashrc
drwx------ 37 filippo filippo   4096 lug  7 21:21 .cache
drwxr-xr-x  3 filippo filippo   4096 dic 19  2015 .codeblocks
drwx------ 38 filippo filippo   4096 giu 26 15:41 .config
drwx------  3 root    root      4096 ott 26  2014 .dbus
-rw-r--r--  1 filippo filippo     25 ott 26  2014 .dmrc
drwxr-xr-x  4 filippo filippo   4096 mar 16 16:22 Documenti
drwx------  5 filippo filippo   4096 lug 10 10:05 .dropbox
drwx------  7 filippo filippo   4096 lug 10 10:05 Dropbox
drwxr-xr-x  3 filippo filippo   4096 giu 13 22:09 .dropbox-dist
-rwxrwxrwx  1 filippo filippo  10626 feb  6 16:07 ElencoFilm
-rw-rw-r--  1 filippo filippo  10626 feb  6 16:10 elencoOrdinato.txt
-rw-r--r--  1 filippo filippo   8980 ott 26  2014 examples.desktop
drwx------  4 filippo filippo   4096 lug 10 10:06 .gconf
drwxrwxr-x  3 filippo filippo   4096 mar 11 15:55 .gfclient
drwxr-xr-x 24 filippo filippo   4096 apr 23 11:50 .gimp-2.8
drwxrwxr-x  8 filippo filippo   4096 mar 11 17:19 glassfish-4.1.1
drwx------  3 filippo filippo   4096 lug 10 10:05 .gnupg
drwx------  2 filippo filippo   4096 mag  5  2015 .gphoto
drwxrwxr-x  5 filippo filippo   4096 giu 24 11:10 .gradle
drwx------  2 root    root      4096 ott 26  2014 .gvfs
-rw-------  1 filippo filippo 145502 lug 10 10:05 .ICEauthority
drwxr-xr-x  3 filippo filippo   4096 giu 17 15:11 Immagini
drwxrwxr-x  5 filippo filippo   4096 mar  3 16:36 .java
-rw-------  1 filippo filippo     89 mar 16 16:31 .lesshst
-rw-r--r--  1 root    root      1313 nov 11  2015 license.txt
drwx------  3 filippo filippo   4096 ott 26  2014 .local
drwxr-xr-x 13 filippo filippo   4096 gen 18 15:44 .lyx
drwx------  3 filippo filippo   4096 ott 26  2014 .macromedia
drwxr-xr-x  2 root    root      4096 gen 21 17:10 mcode
drwxr-xr-x  2 filippo filippo   4096 ott 26  2014 Modelli
drwx------  4 filippo filippo   4096 ott 26  2014 .mozilla
drwxr-xr-x  3 filippo filippo   4096 feb 21  2015 Musica
-rw-rw-r--  1 filippo filippo  49326 gen 21 17:08 m.zip
drwxr-xr-x  2 root    root      4096 nov  1  2015 .nano
drwxrwxr-x  7 filippo filippo   4096 mar 11 17:20 .nbi
drwxrwxr-x  4 filippo filippo   4096 mar 11 17:20 .netbeans
drwxrwxr-x 23 filippo filippo   4096 giu 13 15:26 netbeans-8.1
drwxrwxr-x  3 filippo filippo   4096 mar 11 15:52 .netbeans-derby
drwxrwxr-x  3 filippo filippo   4096 mar 12 11:47 NetBeansProjects
drwx------  3 filippo filippo   4096 ott 27  2014 .nv
-rw-rw-r--  1 filippo filippo    373 lug  5 17:51 .nvidia-settings-rc
-rw-------  1 filippo filippo   6997 feb 14 19:00 .octave_hist
-rw-rw-r--  1 filippo filippo      0 feb  2 17:07 octave-workspace
drwxrwxr-x  2 filippo filippo   4096 mar 11 17:04 .oracle_jre_usage
drwx------  3 filippo filippo   4096 gen 15  2015 .pki
-rw-r--r--  1 filippo filippo    675 ott 26  2014 .profile
-rw-rw-r--  1 filippo filippo    176 dic 23  2015 prova.aux
-rw-rw-r--  1 filippo filippo   3749 dic 23  2015 prova.log
-rw-rw-r--  1 filippo filippo 105869 dic 23  2015 prova.pdf
drwxr-xr-x  2 filippo filippo   4096 ott 26  2014 Pubblici
drwxr-xr-x  8 filippo filippo   4096 lug  4 11:50 Scaricati
drwxr-xr-x  5 filippo filippo   4096 giu 30 16:31 Scrivania
-rw-r--r--  1 filippo filippo      0 ago  5  2015 .sudo_as_admin_successful
drwxrwxr-x  5 filippo filippo   4096 giu 20 13:43 .TelegramDesktop
drwxr-xr-x  4 filippo filippo   4096 gen 18 15:42 .texmf-var
drwx------  4 filippo filippo   4096 dic 21  2014 .thumbnails
drwx------  4 filippo filippo   4096 ott 29  2014 .thunderbird
drwxrwxr-x  2 filippo filippo   4096 mar  2 16:28 .Trash
drwxr-xr-x  3 filippo filippo   4096 giu 24  2015 Video
-rw-------  1 filippo filippo    195 lug 10 10:05 .Xauthority
-rw-rw-r--  1 filippo filippo    130 ott 27  2014 .xinputrc
-rw-------  1 filippo filippo     87 lug 10 10:05 .xsession-errors
-rw-------  1 filippo filippo   1827 lug  8 17:39 .xsession-errors.old

```

I'm currently using nouveau drivers, I don't know if it's relevant.

---

### Post by Bashing-om on 2016-07-10
coffee.guy; Welp;

You as " filippo " are authorized to access you desktop, we can toss that thought out the window, does not apply.

So, now, do we have a driver conflict .. and what is installed ?
```

dpkg -l | grep -i nvidia
lsmod | grep nvidia
lsmod | grep nouveau

```

As we look for the why.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-11
As a consequence of your question, I guess you would me to try those commands with nvidia driver installed (and login loop). I am I right?

Anyway, I tried in both cases. First without nvidia driver installed.

dpkg -l | grep -i nvidia
```
ii  bbswitch-dkms                                        0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  bumblebee                                            3.2.1-10                                                    amd64        NVIDIA Optimus support for Linux
rc  libcuda1-304                                         304.131-0ubuntu0.15.10.1                                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                         340.76-0ubuntu2                                             amd64        NVIDIA CUDA runtime library
rc  libcuda1-352                                         352.63-0ubuntu0.15.10.1                                     amd64        NVIDIA CUDA runtime library
ii  primus                                               0~20150328-1                                                amd64        client-side GPU offloading for NVIDIA Optimus
```

lsmod | grep nvidia
```
/**Nothing**/
```

lsmod | grep nouveau
```
/**Nothing**/
```


After those, I installed again the nvidia drivers 367, and tried again.

dpkg -l | grep -i nvidia
```
ii  bbswitch-dkms                                        0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  bumblebee                                            3.2.1-10                                                    amd64        NVIDIA Optimus support for Linux
rc  libcuda1-304                                         304.131-0ubuntu0.15.10.1                                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                         340.76-0ubuntu2                                             amd64        NVIDIA CUDA runtime library
rc  libcuda1-352                                         352.63-0ubuntu0.15.10.1                                     amd64        NVIDIA CUDA runtime library
ii  libcuda1-367                                         367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA CUDA runtime library
ii  nvidia-367                                           367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA binary driver - version 367.27
ii  nvidia-opencl-icd-367                                367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                      367.18-0ubuntu0~gpu16.04.1                                  amd64        Tool for configuring the NVIDIA graphics driver
ii  primus                                               0~20150328-1                                                amd64        client-side GPU offloading for NVIDIA Optimus
```

lsmod | grep nvidia
```
nvidia_uvm            630784  0
nvidia_drm             45056  0
nvidia_modeset        765952  1 nvidia_drm
drm_kms_helper        147456  2 i915,nvidia_drm
nvidia              11075584  2 nvidia_modeset,nvidia_uvm
drm                   360448  4 i915,drm_kms_helper,nvidia_drm
```

lsmod | grep nouveau
```
/**Nothing**/
```

P.S. I tried "ls -al /home/<user_name>" with nvidia drivers installed too, and it showed me the usual output.

---

### Post by Bashing-om on 2016-07-11
coffee.guy; OK,

Now I have an inkling of what is going on here !
per:
> 
ii  bumblebee
ii  primus

I suggest we have a conflict in the graphic's controller between BumbleBee and nvidia-prime installation. There can be but one controller.
Bumblebee has been depreciated in favor of nvidia-prime and I have no experience with BumbleBee.

How about we remove BumbleBee and install nvidia-prime .. This change will require a mind set change on your part to learn nvidia-prime to control the graphic's sets .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-11
Ok, I removed BumbleBee, to use nvidia-prime, which is installed automatically with nvidia-367.
Unfortunately still experienced login loop. I took the output of the commands I used before, dunno if they can be useful.


dpkg -l | grep -i nvidia
```
ii  bbswitch-dkms                                        0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
rc  libcuda1-304                                         304.131-0ubuntu0.15.10.1                                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                         340.76-0ubuntu2                                             amd64        NVIDIA CUDA runtime library
rc  libcuda1-352                                         352.63-0ubuntu0.15.10.1                                     amd64        NVIDIA CUDA runtime library
ii  libcuda1-367                                         367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA CUDA runtime library
ii  nvidia-367                                           367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA binary driver - version 367.27
ii  nvidia-opencl-icd-367                                367.27-0ubuntu0~gpu16.04.1                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                         0.8.2                                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                      367.18-0ubuntu0~gpu16.04.1                                  amd64        Tool for configuring the NVIDIA graphics driver
```

lsmod | grep nvidia
```
nvidia_uvm            630784  0
nvidia_drm             45056  0
nvidia_modeset        765952  1 nvidia_drm
drm_kms_helper        147456  2 i915,nvidia_drm
nvidia              11075584  2 nvidia_modeset,nvidia_uvm
drm                   360448  4 i915,drm_kms_helper,nvidia_drm
```

lsmod | grep nouveau
```
/**Nothing**/ 

```

---

### Post by Bashing-om on 2016-07-11
coffee.guy; OK;

Looks good // as it is still not working, let's see what X has to say :
```

cat /var/log/Xorg.0.log
cat /var/log/gpu-manager.log

```
Depending here, we next look at the config file " /etc/X11/Xorg.conf " .


[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-13
cat /var/log/Xorg.0.log
```
[    93.728]
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    93.728] X Protocol Version 11, Revision 0
[    93.728] Build Operating System: Linux 3.13.0-86-generic x86_64 Ubuntu
[    93.728] Current Operating System: Linux filippo-Aspire-8951G 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64
[    93.729] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-28-generic root=UUID=270e4a22-7b15-4247-9c1f-b97aab8d33bb ro quiet splash quiet splash nomodeset acpi_osi= vt.handoff=7
[    93.729] Build Date: 18 May 2016  01:07:07AM
[    93.729] xorg-server 2:1.18.3-1ubuntu2.2 (For technical support please see http://www.ubuntu.com/support)
[    93.729] Current version of pixman: 0.33.6
[    93.729]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    93.729] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    93.729] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 12 16:53:07 2016
[    93.729] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    93.730] (==) No Layout section.  Using the first Screen section.
[    93.730] (==) No screen section available. Using defaults.
[    93.730] (**) |-->Screen "Default Screen Section" (0)
[    93.730] (**) |   |-->Monitor "<default monitor>"
[    93.730] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    93.730] (==) Automatically adding devices
[    93.730] (==) Automatically enabling devices
[    93.730] (==) Automatically adding GPU devices
[    93.730] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    93.731] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    93.731]     Entry deleted from font path.
[    93.731] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    93.731]     Entry deleted from font path.
[    93.731] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    93.731]     Entry deleted from font path.
[    93.731] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    93.731]     Entry deleted from font path.
[    93.731] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    93.731]     Entry deleted from font path.
[    93.731] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    93.731] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    93.731] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    93.731] (II) Loader magic: 0x564af7f57da0
[    93.731] (II) Module ABI versions:
[    93.731]     X.Org ANSI C Emulation: 0.4
[    93.731]     X.Org Video Driver: 20.0
[    93.731]     X.Org XInput driver : 22.1
[    93.731]     X.Org Server Extension : 9.0
[    93.732] (++) using VT number 7

[    93.732] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    93.732] (II) xfree86: Adding drm device (/dev/dri/card0)
[    93.734] (--) PCI:*(0:0:2:0) 8086:0116:1025:0566 rev 9, Mem @ 0xd2400000/4194304, 0xc0000000/268435456, I/O @ 0x00007000/64
[    93.734] (--) PCI: (0:1:0:0) 10de:0dce:1025:0566 rev 161, Mem @ 0xd0000000/33554432, 0xa0000000/268435456, 0xb0000000/67108864, I/O @ 0x00006000/128, BIOS @ 0x????????/524288
[    93.734] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    93.734] (II) "glx" will be loaded by default.
[    93.734] (II) LoadModule: "glx"
[    93.734] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    93.740] (II) Module glx: vendor="NVIDIA Corporation"
[    93.740]     compiled for 4.0.2, module version = 1.0.0
[    93.740]     Module class: X.Org Server Extension
[    93.740] (II) NVIDIA GLX Module  367.27  Thu Jun  9 18:19:55 PDT 2016
[    93.740] (==) Matched nvidia as autoconfigured driver 0
[    93.740] (==) Matched nouveau as autoconfigured driver 1
[    93.740] (==) Matched intel as autoconfigured driver 2
[    93.740] (==) Matched modesetting as autoconfigured driver 3
[    93.740] (==) Matched fbdev as autoconfigured driver 4
[    93.740] (==) Matched vesa as autoconfigured driver 5
[    93.740] (==) Assigned the driver to the xf86ConfigLayout
[    93.740] (II) LoadModule: "nvidia"
[    93.740] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    93.741] (II) Module nvidia: vendor="NVIDIA Corporation"
[    93.741]     compiled for 4.0.2, module version = 1.0.0
[    93.741]     Module class: X.Org Video Driver
[    93.741] (II) LoadModule: "nouveau"
[    93.741] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    93.741] (II) Module nouveau: vendor="X.Org Foundation"
[    93.741]     compiled for 1.18.1, module version = 1.0.12
[    93.741]     Module class: X.Org Video Driver
[    93.741]     ABI class: X.Org Video Driver, version 20.0
[    93.741] (II) LoadModule: "intel"
[    93.741] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    93.742] (II) Module intel: vendor="X.Org Foundation"
[    93.742]     compiled for 1.18.1, module version = 2.99.917
[    93.742]     Module class: X.Org Video Driver
[    93.742]     ABI class: X.Org Video Driver, version 20.0
[    93.742] (II) LoadModule: "modesetting"
[    93.742] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    93.742] (II) Module modesetting: vendor="X.Org Foundation"
[    93.742]     compiled for 1.18.3, module version = 1.18.3
[    93.742]     Module class: X.Org Video Driver
[    93.742]     ABI class: X.Org Video Driver, version 20.0
[    93.742] (II) LoadModule: "fbdev"
[    93.742] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    93.742] (II) Module fbdev: vendor="X.Org Foundation"
[    93.742]     compiled for 1.18.1, module version = 0.4.4
[    93.742]     Module class: X.Org Video Driver
[    93.742]     ABI class: X.Org Video Driver, version 20.0
[    93.742] (II) LoadModule: "vesa"
[    93.742] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    93.743] (II) Module vesa: vendor="X.Org Foundation"
[    93.743]     compiled for 1.18.1, module version = 2.3.4
[    93.743]     Module class: X.Org Video Driver
[    93.743]     ABI class: X.Org Video Driver, version 20.0
[    93.743] (II) NVIDIA dlloader X Driver  367.27  Thu Jun  9 17:57:30 PDT 2016
[    93.743] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    93.743] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    93.743] (II) NOUVEAU driver for NVIDIA chipset families :
[    93.743]     RIVA TNT        (NV04)
[    93.743]     RIVA TNT2       (NV05)
[    93.743]     GeForce 256     (NV10)
[    93.743]     GeForce 2       (NV11, NV15)
[    93.743]     GeForce 4MX     (NV17, NV18)
[    93.743]     GeForce 3       (NV20)
[    93.743]     GeForce 4Ti     (NV25, NV28)
[    93.743]     GeForce FX      (NV3x)
[    93.743]     GeForce 6       (NV4x)
[    93.743]     GeForce 7       (G7x)
[    93.743]     GeForce 8       (G8x)
[    93.743]     GeForce GTX 200 (NVA0)
[    93.743]     GeForce GTX 400 (NVC0)
[    93.743] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    93.743] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    93.743] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    93.743] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    93.743] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    93.743] (II) FBDEV: driver for framebuffer: fbdev
[    93.743] (II) VESA: driver for VESA chipsets: vesa
[    93.744] (EE) [drm] Failed to open DRM device for (null): -22
[    93.750] (WW) Falling back to old probe method for modesetting
[    93.750] (II) Loading sub module "fbdevhw"
[    93.750] (II) LoadModule: "fbdevhw"
[    93.750] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    93.750] (II) Module fbdevhw: vendor="X.Org Foundation"
[    93.750]     compiled for 1.18.3, module version = 0.0.2
[    93.750]     ABI class: X.Org Video Driver, version 20.0
[    93.750] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    93.750] (II) FBDEV(1): using default device
[    93.750] (WW) Falling back to old probe method for vesa
[    93.750] (EE) Screen 0 deleted because of no matching config section.
[    93.750] (II) UnloadModule: "modesetting"
[    93.750] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    93.750] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    93.750] (==) FBDEV(0): RGB weight 888
[    93.750] (==) FBDEV(0): Default visual is TrueColor
[    93.750] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    93.750] (II) FBDEV(0): hardware: VESA VGA (video memory: 8128kB)
[    93.750] (II) FBDEV(0): checking modes against framebuffer device...
[    93.750] (II) FBDEV(0): checking modes against monitor...
[    93.750] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    93.750] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[    93.750] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[    93.750] (==) FBDEV(0): DPI set to (96, 96)
[    93.750] (II) Loading sub module "fb"
[    93.750] (II) LoadModule: "fb"
[    93.751] (II) Loading /usr/lib/xorg/modules/libfb.so
[    93.751] (II) Module fb: vendor="X.Org Foundation"
[    93.751]     compiled for 1.18.3, module version = 1.0.0
[    93.751]     ABI class: X.Org ANSI C Emulation, version 0.4
[    93.751] (**) FBDEV(0): using shadow framebuffer
[    93.751] (II) Loading sub module "shadow"
[    93.751] (II) LoadModule: "shadow"
[    93.751] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    93.751] (II) Module shadow: vendor="X.Org Foundation"
[    93.751]     compiled for 1.18.3, module version = 1.1.0
[    93.751]     ABI class: X.Org ANSI C Emulation, version 0.4
[    93.751] (II) UnloadModule: "vesa"
[    93.751] (II) Unloading vesa
[    93.751] (==) Depth 24 pixmap format is 32 bpp
[    93.751] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    93.751] (==) FBDEV(0): Backing store enabled
[    93.752] (==) FBDEV(0): DPMS enabled
[    93.752] (==) RandR enabled
[    93.757] (II) SELinux: Disabled on system
[    93.758] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    93.802] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    93.802] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    93.802] (II) LoadModule: "evdev"
[    93.802] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    93.802] (II) Module evdev: vendor="X.Org Foundation"
[    93.802]     compiled for 1.18.1, module version = 2.10.1
[    93.802]     Module class: X.Org XInput Driver
[    93.802]     ABI class: X.Org XInput driver, version 22.1
[    93.802] (II) Using input driver 'evdev' for 'Power Button'
[    93.802] (**) Power Button: always reports core events
[    93.802] (**) evdev: Power Button: Device: "/dev/input/event3"
[    93.802] (--) evdev: Power Button: Vendor 0 Product 0x1
[    93.802] (--) evdev: Power Button: Found keys
[    93.802] (II) evdev: Power Button: Configuring as keyboard
[    93.802] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    93.802] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    93.802] (**) Option "xkb_rules" "evdev"
[    93.802] (**) Option "xkb_model" "pc104"
[    93.802] (**) Option "xkb_layout" "it"
[    93.802] (**) Option "xkb_options" "lv3:ralt_switch,terminate:ctrl_alt_bksp"
[    93.822] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    93.822] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    93.822] (II) Using input driver 'evdev' for 'Power Button'
[    93.822] (**) Power Button: always reports core events
[    93.822] (**) evdev: Power Button: Device: "/dev/input/event0"
[    93.822] (--) evdev: Power Button: Vendor 0 Product 0x1
[    93.822] (--) evdev: Power Button: Found keys
[    93.822] (II) evdev: Power Button: Configuring as keyboard
[    93.822] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    93.822] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    93.822] (**) Option "xkb_rules" "evdev"
[    93.822] (**) Option "xkb_model" "pc104"
[    93.822] (**) Option "xkb_layout" "it"
[    93.822] (**) Option "xkb_options" "lv3:ralt_switch,terminate:ctrl_alt_bksp"
[    93.823] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    93.823] (II) No input driver specified, ignoring this device.
[    93.823] (II) This device may have been added with another device file.
[    93.823] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    93.823] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    93.823] (II) Using input driver 'evdev' for 'Sleep Button'
[    93.823] (**) Sleep Button: always reports core events
[    93.823] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    93.823] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    93.823] (--) evdev: Sleep Button: Found keys
[    93.823] (II) evdev: Sleep Button: Configuring as keyboard
[    93.823] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    93.823] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    93.823] (**) Option "xkb_rules" "evdev"
[    93.823] (**) Option "xkb_model" "pc104"
[    93.823] (**) Option "xkb_layout" "it"
[    93.823] (**) Option "xkb_options" "lv3:ralt_switch,terminate:ctrl_alt_bksp"
[    93.824] (II) config/udev: Adding input device 1.3M HD 264 WebCam (/dev/input/event14)
[    93.824] (**) 1.3M HD 264 WebCam: Applying InputClass "evdev keyboard catchall"
[    93.824] (II) Using input driver 'evdev' for '1.3M HD 264 WebCam'
[    93.824] (**) 1.3M HD 264 WebCam: always reports core events
[    93.824] (**) evdev: 1.3M HD 264 WebCam: Device: "/dev/input/event14"
[    93.824] (--) evdev: 1.3M HD 264 WebCam: Vendor 0x408 Product 0x1fb2
[    93.824] (--) evdev: 1.3M HD 264 WebCam: Found keys
[    93.824] (II) evdev: 1.3M HD 264 WebCam: Configuring as keyboard
[    93.824] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input14/event14"
[    93.824] (II) XINPUT: Adding extended input device "1.3M HD 264 WebCam" (type: KEYBOARD, id 9)
[    93.824] (**) Option "xkb_rules" "evdev"
[    93.824] (**) Option "xkb_model" "pc104"
[    93.824] (**) Option "xkb_layout" "it"
[    93.824] (**) Option "xkb_options" "lv3:ralt_switch,terminate:ctrl_alt_bksp"
[    93.825] (II) config/udev: Adding input device Areson USB Device (/dev/input/event5)
[    93.825] (**) Areson USB Device: Applying InputClass "evdev pointer catchall"
[    93.825] (II) Using input driver 'evdev' for 'Areson USB Device'
[    93.825] (**) Areson USB Device: always reports core events
[    93.825] (**) evdev: Areson USB Device: Device: "/dev/input/event5"
[    93.880] (--) evdev: Areson USB Device: Vendor 0x4b4 Product 0x60
[    93.880] (--) evdev: Areson USB Device: Found 12 mouse buttons
[    93.880] (--) evdev: Areson USB Device: Found scroll wheel(s)
[    93.880] (--) evdev: Areson USB Device: Found relative axes
[    93.880] (--) evdev: Areson USB Device: Found x and y relative axes
[    93.880] (II) evdev: Areson USB Device: Configuring as mouse
[    93.880] (II) evdev: Areson USB Device: Adding scrollwheel support
[    93.880] (**) evdev: Areson USB Device: YAxisMapping: buttons 4 and 5
[    93.880] (**) evdev: Areson USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    93.880] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/0003:04B4:0060.0001/input/input5/event5"
[    93.880] (II) XINPUT: Adding extended input device "Areson USB Device" (type: MOUSE, id 10)
[    93.880] (II) evdev: Areson USB Device: initialized for relative axes.
[    93.881] (**) Areson USB Device: (accel) keeping acceleration scheme 1
[    93.881] (**) Areson USB Device: (accel) acceleration profile 0
[    93.881] (**) Areson USB Device: (accel) acceleration factor: 2.000
[    93.881] (**) Areson USB Device: (accel) acceleration threshold: 4
[    93.882] (II) config/udev: Adding input device Areson USB Device (/dev/input/mouse0)
[    93.882] (II) No input driver specified, ignoring this device.
[    93.882] (II) This device may have been added with another device file.
[    93.883] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    93.883] (II) No input driver specified, ignoring this device.
[    93.883] (II) This device may have been added with another device file.
[    93.884] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event11)
[    93.884] (II) No input driver specified, ignoring this device.
[    93.884] (II) This device may have been added with another device file.
[    93.885] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[    93.885] (II) No input driver specified, ignoring this device.
[    93.885] (II) This device may have been added with another device file.
[    93.885] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event13)
[    93.885] (II) No input driver specified, ignoring this device.
[    93.885] (II) This device may have been added with another device file.
[    93.887] (II) config/udev: Adding input device SUYIN USB Device (/dev/input/event6)
[    93.887] (**) SUYIN USB Device: Applying InputClass "evdev keyboard catchall"
[    93.887] (II) Using input driver 'evdev' for 'SUYIN USB Device'
[    93.887] (**) SUYIN USB Device: always reports core events
[    93.887] (**) evdev: SUYIN USB Device: Device: "/dev/input/event6"
[    93.887] (--) evdev: SUYIN USB Device: Vendor 0x64e Product 0x3030
[    93.887] (--) evdev: SUYIN USB Device: Found keys
[    93.887] (II) evdev: SUYIN USB Device: Configuring as keyboard
[    93.887] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/0003:064E:3030.0002/input/input6/event6"
[    93.887] (II) XINPUT: Adding extended input device "SUYIN USB Device" (type: KEYBOARD, id 11)
[    93.887] (**) Option "xkb_rules" "evdev"
[    93.887] (**) Option "xkb_model" "pc104"
[    93.887] (**) Option "xkb_layout" "it"
[    93.887] (**) Option "xkb_options" "lv3:ralt_switch,terminate:ctrl_alt_bksp"
[    93.889] (II) config/udev: Adding input device SUYIN USB Device (/dev/input/event7)
[    93.889] (**) SUYIN USB Device: Applying InputClass "evdev pointer catchall"
[    93.889] (**) SUYIN USB Device: Applying InputClass "evdev keyboard catchall"
[    93.889] (II) Using input driver 'evdev' for 'SUYIN USB Device'
[    93.889] (**) SUYIN USB Device: always reports core events
[    93.890] (**) evdev: SUYIN USB Device: Device: "/dev/input/event7"
[    93.890] (--) evdev: SUYIN USB Device: Vendor 0x64e Product 0x3030
[    93.890] (--) evdev: SUYIN USB Device: Found 9 mouse buttons
[    93.890] (--) evdev: SUYIN USB Device: Found scroll wheel(s)
[    93.890] (--) evdev: SUYIN USB Device: Found relative axes
[    93.890] (--) evdev: SUYIN USB Device: Found x and y relative axes
[    93.890] (--) evdev: SUYIN USB Device: Found absolute axes
[    93.890] (II) evdev: SUYIN USB Device: Forcing absolute x/y axes to exist.
[    93.890] (--) evdev: SUYIN USB Device: Found keys
[    93.890] (II) evdev: SUYIN USB Device: Configuring as mouse
[    93.890] (II) evdev: SUYIN USB Device: Configuring as keyboard
[    93.890] (II) evdev: SUYIN USB Device: Adding scrollwheel support
[    93.890] (**) evdev: SUYIN USB Device: YAxisMapping: buttons 4 and 5
[    93.890] (**) evdev: SUYIN USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    93.890] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/0003:064E:3030.0004/input/input7/event7"
[    93.890] (II) XINPUT: Adding extended input device "SUYIN USB Device" (type: KEYBOARD, id 12)
[    93.890] (**) Option "xkb_rules" "evdev"
[    93.890] (**) Option "xkb_model" "pc104"
[    93.890] (**) Option "xkb_layout" "it"
[    93.890] (**) Option "xkb_options" "lv3:ralt_switch,terminate:ctrl_alt_bksp"
[    93.891] (II) evdev: SUYIN USB Device: initialized for relative axes.
[    93.891] (WW) evdev: SUYIN USB Device: ignoring absolute axes.
[    93.891] (**) SUYIN USB Device: (accel) keeping acceleration scheme 1
[    93.891] (**) SUYIN USB Device: (accel) acceleration profile 0
[    93.891] (**) SUYIN USB Device: (accel) acceleration factor: 2.000
[    93.891] (**) SUYIN USB Device: (accel) acceleration threshold: 4
[    93.892] (II) config/udev: Adding input device SUYIN USB Device (/dev/input/mouse1)
[    93.892] (II) No input driver specified, ignoring this device.
[    93.892] (II) This device may have been added with another device file.
[    93.893] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    93.893] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    93.893] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    93.893] (**) AT Translated Set 2 keyboard: always reports core events
[    93.893] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    93.893] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    93.893] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    93.893] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    93.894] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    93.894] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    93.894] (**) Option "xkb_rules" "evdev"
[    93.894] (**) Option "xkb_model" "pc104"
[    93.894] (**) Option "xkb_layout" "it"
[    93.894] (**) Option "xkb_options" "lv3:ralt_switch,terminate:ctrl_alt_bksp"
[    93.898] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event8)
[    93.898] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    93.898] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    93.898] (**) Acer WMI hotkeys: always reports core events
[    93.898] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event8"
[    93.899] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    93.899] (--) evdev: Acer WMI hotkeys: Found keys
[    93.899] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    93.899] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[    93.899] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 14)
[    93.899] (**) Option "xkb_rules" "evdev"
[    93.899] (**) Option "xkb_model" "pc104"
[    93.899] (**) Option "xkb_layout" "it"
[    93.899] (**) Option "xkb_options" "lv3:ralt_switch,terminate:ctrl_alt_bksp"
[    93.900] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event9)
[    93.900] (II) No input driver specified, ignoring this device.
[    93.900] (II) This device may have been added with another device file.
[    93.900] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    93.900] (II) No input driver specified, ignoring this device.
[    93.900] (II) This device may have been added with another device file.
```

cat /var/log/gpu-manager.log
```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-28-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-28-generic/updates/dkms
Found nvidia module: nvidia_367_uvm.ko
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:116
BusID "PCI:0@0:2:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver. Skipping...
Vendor/Device Id: 10de:dce
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-367/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-367/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Single card detected
No change - nothing to do
```


I tried to look for "/etc/X11/Xorg.conf" but it doesn't exist.
I took the content of the folder "/etc/X11/".

ls -al /etc/X11/
```
totale 71788
drwxr-xr-x  11 root root     4096 lug  7 20:19 .
drwxr-xr-x 150 root root    12288 lug 12 16:49 ..
drwxr-xr-x   2 root root     4096 lug  7 20:27 app-defaults
-rw-------   1 root root 99934208 ott 27  2014 core
drwxr-xr-x   2 root root     4096 ott 22  2014 cursors
-rw-r--r--   1 root root       18 ott 22  2014 default-display-manager
drwxr-xr-x   4 root root     4096 ott 22  2014 fonts
-rw-r--r--   1 root root    17394 dic  3  2009 rgb.txt
lrwxrwxrwx   1 root root       13 ott 26  2014 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root     4096 lug  7 20:27 xinit
drwxr-xr-x   2 root root     4096 giu 23  2014 xkb
-rw-r--r--   1 root root     1325 mag  7 16:12 xorg.conf.07072016
-rw-r--r--   1 root root      593 ago  3  2015 xorg.conf.08032015
-rw-r--r--   1 root root        0 ago  4  2015 xorg.conf.08042015
-rw-r--r--   1 root root      593 ago  4  2015 xorg.conf.08052015
-rw-r--r--   1 root root     1332 nov  1  2015 xorg.conf.backup
-rw-r--r--   1 root root      593 ago  3  2015 xorg.conf-backup-150803180244
-rw-r--r--   1 root root      269 ago 14  2015 xorg.conf.failsafe
-rw-r--r--   1 root root        0 mag  7 16:12 xorg.conf.nvidia-xconfig-original
-rw-r--r--   1 root root     1356 nov  1  2015 xorg.conf_old
-rwxr-xr-x   1 root root      709 apr  1  2010 Xreset
drwxr-xr-x   2 root root     4096 lug  7 20:19 Xreset.d
drwxr-xr-x   2 root root     4096 lug  7 20:19 Xresources
-rwxr-xr-x   1 root root     3730 gen 29  2014 Xsession
drwxr-xr-x   2 root root     4096 lug 12 11:06 Xsession.d
-rw-r--r--   1 root root      265 lug  1  2008 Xsession.options
drwxr-xr-x   2 root root     4096 ott 31  2015 xsm
-rw-r--r--   1 root root      601 ott 22  2014 Xwrapper.config
```

---

### Post by Bashing-om on 2016-07-14
coffee.guy; Hummm ...

should workie .. but, booting with the 'nomoeset' boot parameter defeats Kernel Mode Setting such that a higher level graphic's driver will not be loaded .

What results when removing nomodeset; as 367 and nvidia-prime are installed; boot to a terminal AND generate a new config file :
```

sudo nvidia-xconfig

```

reboot the system,  and we see the effect.

[INDENT][INDENT][INDENT]maybe YES
[/INDENT][/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-14
Ok, the 'nomodeset' boot parameter was really the problem. I removed it, and now I am able to log in.
Then I ran ```
sudo nvidia-xconfig
``` and rebooted. Now I'm stuck with a 640x480 (4:3) screen configuration, and I can't change it.

This was the output on terminal of 'sudo nvidia-xconfig'
```
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as
'/etc/X11/xorg.conf.nvidia-xconfig-original'
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


```

cat /etc/X11/xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 367.27  (buildmeister@swio-display-x64-rhel04-12)  Thu Jun  9 19:24:36 PDT 2016

Section "ServerLayout"
    Identifier     "layout"
    Screen      0  "nvidia" 0 0
    Inactive       "intel"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "intel"
    Driver         "modesetting"
    Option         "AccelMethod" "None"
    BusID          "PCI:0@0:2:0"
EndSection

Section "Device"
    Identifier     "nvidia"
    Driver         "nvidia"
    BusID          "PCI:1@0:0:0"
EndSection

Section "Screen"
    Identifier     "intel"
    Device         "intel"
    Monitor        "Monitor0"
EndSection

Section "Screen"
    Identifier     "nvidia"
    Device         "nvidia"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AllowEmptyInitialConfiguration" "on"
    Option         "IgnoreDisplayDevices" "CRT"
    Option         "ConstrainCursor" "off"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection


```

cat /etc/X11/xorg.conf.backup
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection


```

P.S. I can't change it neither from nvidia-settings. I'm not sure if this problem is worth another thread, as the problem with the use nvidia card is now solved

---

### Post by Bashing-om on 2016-07-14
coffee.guy; Hummm ..

I am not the greatest to advise about resolution issues .. but
try this:
in the file /etc/X11/xorg.conf;
edit the line - Option         "AccelMethod" "None"  - in - Section "Device" - to :
```

Option "AccelMethod" "SNA"

```

reboot to see the effect .

[INDENT][INDENT]maybe, though
[INDENT][INDENT][INDENT]not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-14
Nope, that hasn't any effects. 

I tried replacing 'xorg.conf' with 'xorg.conf.backup' and the resolution is fine.
Is that configuration bad for any reason, or I can keep using it?

---

### Post by Bashing-om on 2016-07-14
coffee.guy; Good deal ...

If it works .. do not fix it .. keep using it ..

Maybe look at the differing files and see what is different .

[INDENT][INDENT]just goes to show
[INDENT][INDENT]never can tell 'til
[INDENT][INDENT][INDENT]ya try
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by coffee.guy on 2016-07-14
I'll look for it, 'cause there is still same minor problem, like artifacts on a diagonal and backlight brightness not changing.
Anyway, thanks a lot for the help with the drivers!

---

### Post by Bashing-om on 2016-07-14
coffee.guy; hey;

Glad to assist.

If you are satisfied at this point with the driver install
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Look forward to our next adventure

---

