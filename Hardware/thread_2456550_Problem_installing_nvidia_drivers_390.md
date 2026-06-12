---
title: "Problem installing nvidia drivers 390"
date: 2021-01-13
forum: Hardware
---

### Post by Manucho on 2021-01-13
Hello dear ubuntu users

I dont recall the exact model of the GPU, i think its a nvidia 510ti

Ive tested removing the drivers and then installing them again by the command line, no luck.
Ive tried the automatic installer in additional drivers, no luck either.


Ive tried what several sites in internet say, with no results

I managed to get the drivers working in a previous install of ubuntu 20.04, but i had to reinstall and now i dont seem to get it working.

Using nvidia-settings gives a blank config interface, and this output in the console

[HTML]ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system


(nvidia-settings:10827): GLib-GObject-CRITICAL **: 21:21:16.667: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 21:21:16.672: PRIME: No offloading required. Abort
** Message: 21:21:16.672: PRIME: is it supported? no
[/HTML]

Would appreciate the help, thanks!

---

### Post by Bashing-om on 2021-01-13
Manucho; Hello -

Show us what there is to work with.
Post back the outputs of terminal commands:
```

lspci -k | grep -iEA5 'vga|3d'
dpkg -l | grep -i nvidia
lsmod | grep -i nvidia

```

See where we go from here.

[INDENT]all in the process[/INDENT]

---

### Post by grahammechanical on 2021-01-13
What Linux kernel do you have?

```
uname -a
```

I think there have been problems with the 5.8 kernels and I also think Nvidia drivers have also been connected to some of the problems.

Can you use Advanced Options for Ubuntu to load into a 5.4 kernel? Would the open source Nouveau video driver be satisfactory for you?

Regards

P.S. An earlier thread illustrating my point about problems with the 5.8 kernel and Nvidia drivers

[https://ubuntuforums.org/showthread.php?t=2456371](https://ubuntuforums.org/showthread.php?t=2456371)

---

### Post by Manucho on 2021-01-14
[HTML]manuel@hypericum:~$ lspci -k | grep -iEA5 'vga|3d'
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
    Subsystem: Point of View BV GF116 [GeForce GTX 550 Ti]
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
    Subsystem: Point of View BV GF116 High Definition Audio Controller
    Kernel driver in use: snd_hda_intel[/HTML]

By the way, it seems sound is not working ok, mp3 songs jump from time to time and have strange glitches.

[HTML]manuel@hypericum:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-390:amd64                   390.141-0ubuntu0.20.04.1              amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                       390.141-0ubuntu0.20.04.1              all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                390.141-0ubuntu0.20.04.1              amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                 390.141-0ubuntu0.20.04.1              i386         NVIDIA libcompute package
rc  libnvidia-compute-460:amd64                460.32.03-0ubuntu0.20.04.1            amd64        NVIDIA libcompute package
ii  libnvidia-decode-390:amd64                 390.141-0ubuntu0.20.04.1              amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386                  390.141-0ubuntu0.20.04.1              i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64                 390.141-0ubuntu0.20.04.1              amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386                  390.141-0ubuntu0.20.04.1              i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64                   390.141-0ubuntu0.20.04.1              amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386                    390.141-0ubuntu0.20.04.1              i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                     390.141-0ubuntu0.20.04.1              amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                      390.141-0ubuntu0.20.04.1              i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64                   390.141-0ubuntu0.20.04.1              amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386                    390.141-0ubuntu0.20.04.1              i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  linux-modules-nvidia-460-5.8.0-36-generic  5.8.0-36.40~20.04.1                   amd64        Linux kernel nvidia modules for version 5.8.0-36
ii  nvidia-compute-utils-390                   390.141-0ubuntu0.20.04.1              amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                            390.141-0ubuntu0.20.04.1              amd64        NVIDIA DKMS package
ii  nvidia-driver-390                          390.141-0ubuntu0.20.04.1              amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390                   390.141-0ubuntu0.20.04.1              amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390                   390.141-0ubuntu0.20.04.1              amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.14                                all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            440.82-0ubuntu0.20.04.1               amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                           390.141-0ubuntu0.20.04.1              amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18build1                            all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-390              390.141-0ubuntu0.20.04.1              amd64        NVIDIA binary Xorg driver[/HTML]

[HTML]manuel@hypericum:~$ lsmod | grep -i nvidia
manuel@hypericum:~$ [/HTML]

Mi linux is 20.04 just updated, i did a fresh installation yesterday, and updated to latest updates.

[HTML]manuel@hypericum:~$ uname -a
Linux hypericum 5.8.0-36-generic #40~20.04.1-Ubuntu SMP Wed Jan 6 10:15:55 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux[/HTML]

Thanks.


"Can you use Advanced Options for Ubuntu to load into a 5.4 kernel? Would  the open source Nouveau video driver be satisfactory for you?"
I dont know how to use those advanced options. I would like to model in blender, my attempts to do so with noveau resulted in crashes in blender. I managed to install nvidia drivers previously and blender worked good, so i think its the only way i can use blender.

---

### Post by Yellow Pasque on 2021-01-14
[https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time)

---

### Post by Manucho on 2021-01-14
I got the command line of grub before boot, by holding esc.
Once I am there i dont have idea what command i must issue to load older kernel :)

---

### Post by Bashing-om on 2021-01-14
Manucho; Ho Kay - working on it :)

We do have some clean up to do -
> 
ii  libnvidia-compute-390:amd64
ii  linux-modules-nvidia-460-5.8.0-36-generic

where there is a conflict in drivers.

So we boot to that latest 5.4 kernel ( a new one out this day[5.4.0-62-generic]) update/upgrade/cleanup/install .

To that end:
boot to grub's boot menu and here choose "advanced options" >> latest 5.4 kernel.
Execute terminal commands:
```

sudo apt update
sudo apt upgrade

```
reboot then into the -62 version kernel.

Cleanup:
```

sudo apt purge nvidia-*

```
to remove the drivers.

Install:
*IMPORTANT* if equiped disable secure boot as the nvidia driver is 3rd party, and to install the 390 vesion driver easily run:
```

sudo ubuntu-drivers autoinstall

```
where I expect the system indeed to choose the 390 version. per
[https://www.nvidia.com/Download/driverResults.aspx/168290/en-us](https://www.nvidia.com/Download/driverResults.aspx/168290/en-us)

now reboot to see the effect.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Manucho on 2021-01-15
"So we boot to that latest 5.4 kernel ( a new one out this day[5.4.0-62-generic]) update/upgrade/cleanup/install .

To that end:
boot to grub's boot menu and here choose "advanced options" >> latest 5.4 kernel.
Execute terminal commands:
 	Code:
 	[HTML]sudo apt update
sudo apt upgrade [/HTML]reboot then into the -62 version kernel."

when i press esc at boot, to log into grub's menu, i dont get a list or menu to choose from, i only get a command line, and i dont have idea which commands to issue in order to get ubuntu to boot from a different kernel.

Maybe there is a command i can issue at that grub's prompt that brings up the menu to choose from?

If that is not the case, which are the commands to load a specific kernel?

thanks

---

### Post by Bashing-om on 2021-01-15
Manucho; Ouch!

> 
i dont get a list or menu to choose from, i only get a command line, 



What has happened from your first post where you were booting ?

Now we are in for a learning curve - up for it ? - that my take a lot of time and effort on your part.
If so advise us on exactly what the prompt is at this command line. as what the prompt is will determine what the kernel is aware of.

Here too tell us what results from grub's command:
```

ls -al

```

From here we can know what to direct grub's attention to in order to affect a boot.

As you know it takes but a few minutes to do a new install - from a new .ISO - ; this might be the avenue to choose. There have been some fixes to the 5.8 kernel and all may well be good now.

[INDENT][INDENT]but, no pain == little gain
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2021-01-16
> **Manucho said:**
> I got the command line of grub before boot, by holding esc.

No, you're supposed to hold right shift to get a menu, not a prompt. 

Try this instead:
For permanent change you'll need to edit your /etc/default/grub file -- place a "#" symbol at the start of line GRUB_HIDDEN_TIMEOUT=0.

Save changes and run sudo update-grub to apply changes.

---

### Post by Manucho on 2021-01-16
bad bashing bashing-om, yellow pasque got it right.

testing his post now.

---

### Post by Manucho on 2021-01-16
i dont have that line to comment, this is the content of my grub file


[HTML]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"[/HTML]

---

### Post by deadflowr on 2021-01-16
Try changing
```
GRUB_TIMEOUT_STYLE=hidden

```to
```
GRUB_TIMEOUT_STYLE=menu

```and increase the timeout length to something like 5 or 10
```
GRUB_TIMEOUT=0

```to 
```
GRUB_TIMEOUT=10
```
Run the update-grub command after you saved your changes.

Make it as long or short as you please. Even as short as just 1 second if you want.
Note that the timeout lasts until you either hit enter or use the up/down arrows.
Hitting enter starts the boot process instantly.
Hitting the arrow keys will keep you on the grub page indefinitely.

---

### Post by Manucho on 2021-01-16
I got the menu, i booted in 5.4 kernel

did the update and upgrade, rebooted, but in the menu there isnt the .62 version, only the 42 version.

I did the purge and autoinstall command anyway.

  	 	 	 	  [HTML] manuel@hypericum:~$ sudo apt purge nvidia-*

 [sudo] contraseña para manuel:  
 Leyendo lista de paquetes... Hecho
 Creando árbol de dependencias        
 Leyendo la información de estado... Hecho
 E: No se ha podido localizar el paquete nvidia-*
 
 
 
 
 
 
 manuel@hypericum:~$ sudo ubuntu-drivers autoinstall
 Leyendo lista de paquetes... Hecho
 Creando árbol de dependencias        
 Leyendo la información de estado... Hecho
 No se pudieron instalar algunos paquetes. Esto puede significar que
 usted pidió una situación imposible o, si está usando la distribución
 inestable, que algunos paquetes necesarios aún no se han creado o se
 han sacado de «Incoming».
 La siguiente información puede ayudar a resolver la situación:
 
 
 Los siguientes paquetes tienen dependencias incumplidas:
  nvidia-driver-460 : Depende: nvidia-kernel-source-460 (= 460.32.03-0ubuntu0.20.04.1) pero no va a instalarse
 E: No se pudieron corregir los problemas, usted ha retenido paquetes rotos.
  p { margin-bottom: 0.25cm; line-height: 115%; background: transparent }[/HTML]

nothing to purge, and the autoinstall will fail.

however, the correct driver version for my graphics card is nvidia 390, will attempt a manual install now.

---

### Post by Manucho on 2021-01-16
The manual install says 390 version is already installed.

running nvidia-settings gives the same error i reported in the first post.

---

### Post by Bashing-om on 2021-01-16
Manucho; Hey - 

True:
> 
E: The nvidia- * package could not be located

as you have a typo in the command - there should be no space after nvidia- .

Try again:
```

sudo apt update
sudo apt upgrade
sudo apt purge nvidia-*

```
Where we want to remove that driver conflict.

As needed - reboot and insure that secure boot is disabled in bios.
Now install the nvidia driver:
```

sudo ubuntu-drivers autoinstall

```
Reboot to see the effect.

[INDENT][INDENT]all good now ?
[/INDENT][/INDENT]

---

### Post by Manucho on 2021-01-18
Strange, i did boot into ubuntu, latest kernel today and nvidia drivers are working, nvidia-settings too, and its set in the correct resolution.

I did nothing since last report....

magic.

will keep posted if any news, thanks all

[https://youtu.be/0p_1QSUsbsM](https://youtu.be/0p_1QSUsbsM)

---

