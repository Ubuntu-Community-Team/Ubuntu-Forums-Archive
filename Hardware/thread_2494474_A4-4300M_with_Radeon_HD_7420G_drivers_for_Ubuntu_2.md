---
title: "A4-4300M with Radeon HD 7420G drivers for Ubuntu 22.04 LTS OS"
date: 2024-01-17
forum: Hardware
---

### Post by vushido on 2024-01-17
I am using Ubuntu 22.04 LTS, AMD® A4-4300m apu with radeon(tm) hd graphics × 2 and AMD® Aruba.
A black screen during every boot includes a message "_common_interrupt: 1.55 No irq handler for vector". I can use operating system normally.
Is it true that the only solution to remove/solve this error from the boot screen is to downgrade Ubuntu to 15.04 as this is the latest one which officially supports the A4-4300M with Radeon HD 7420G according to [https://www.amd.com/en/support/kb/release-notes/rn-rad-lin-15-9](https://www.amd.com/en/support/kb/release-notes/rn-rad-lin-15-9) ? 

How to check which driver version is used at the moment? Isn't downloading and installing [https://www.amd.com/en/support/apu/amd-series-processors/amd-a4-series-apu-for-laptops/a4-4300m-radeon-hd-7420g](https://www.amd.com/en/support/apu/amd-series-processors/amd-a4-series-apu-for-laptops/a4-4300m-radeon-hd-7420g) under Ubuntu x86 64-Bit a choice to try or perhaps it would even solve the aforementioned?

---

### Post by Yellow Pasque on 2024-01-18
> _common_interrupt: 1.55 No irq handler for vector
If you google, you will find a lot of people get similar error messages, but they are harmless. It has nothing to do with the graphics. Maybe an updated BIOS would stop the error message.

Do not download and install any proprietary ATI/AMD graphics drivers ("fglrx" or "Catalyst"). They are obsolete and will not work with any modern/supported version of Ubuntu. Nowadays, the main part of the graphics driver is built into the kernel (and its version number is the same as the kernel). You can verify correct 3D functionality/version with:
```
glxinfo -B
```

I have a laptop with an A4-3300. It works just fine with Ubuntu 22.04

---

### Post by vushido on 2024-01-23
> **Yellow Pasque said:**
> ```
glxinfo -B
```

I got the following:

```
name of display: :0display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Mesa (0x1002)
    Device: AMD ARUBA (DRM 2.50.0 / 6.5.0-14-generic, LLVM 15.0.7) (0x9992)
    Version: 23.0.4
    Accelerated: yes
    Video memory: 512MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 4.5
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 511 MB, largest block: 511 MB
    VBO free aux. memory - total: 1021 MB, largest block: 1021 MB
    Texture free memory - total: 511 MB, largest block: 511 MB
    Texture free aux. memory - total: 1021 MB, largest block: 1021 MB
    Renderbuffer free memory - total: 511 MB, largest block: 511 MB
    Renderbuffer free aux. memory - total: 1021 MB, largest block: 1021 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 512 MB
    Total available memory: 1533 MB
    Currently available dedicated video memory: 511 MB
OpenGL vendor string: Mesa
OpenGL renderer string: AMD ARUBA (DRM 2.50.0 / 6.5.0-14-generic, LLVM 15.0.7)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 23.0.4-0ubuntu1~22.04.1
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 4.5 (Compatibility Profile) Mesa 23.0.4-0ubuntu1~22.04.1
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile


OpenGL ES profile version string: OpenGL ES 3.1 Mesa 23.0.4-0ubuntu1~22.04.1
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10

```

Is it ok?

---

### Post by Yellow Pasque on 2024-01-23
Yes. That is what you want to see.

---

### Post by vushido on 2024-01-24
Why I must uninstall Mesa before updating Ubuntu to 23 in April? What happens if I do not uninstall?

---

### Post by Yellow Pasque on 2024-01-24
> **vushido said:**
> Why I must uninstall Mesa before updating Ubuntu to 23 in April? What happens if I do not uninstall?

I don't know where you got that idea. You are using the standard mesa package. It will be upgraded just like the other packages when you upgrade. You do not need to uninstall it.

---

### Post by vushido on 2024-01-24
> **Yellow Pasque said:**
> I don't know where you got that idea. You are using the standard mesa package. It will be upgraded just like the other packages when you upgrade. You do not need to uninstall it.

This suggestion was in the Terminal after I installed the standard mesa package.

---

### Post by Yellow Pasque on 2024-01-25
> **vushido said:**
> This suggestion was in the Terminal after I installed the standard mesa package.

Sorry, but I'm not sure what you are talking about (copy/paste would be helpful). Mesa is installed as part of the OS install. You should not have needed to manually install anything related to Mesa.

---

### Post by vushido on 2024-01-26
> **Yellow Pasque said:**
> Sorry, but I'm not sure what you are talking about (copy/paste would be helpful). Mesa is installed as part of the OS install. You should not have needed to manually install anything related to Mesa.

When I ran [COLOR=#000000]glxinfo -B[/COLOR] for the first time after your suggestion, the command [COLOR=#000000][FONT=&amp]glxinfo -B[/FONT][/COLOR] gave me an error that the information usually appearing after running the command [COLOR=#000000][FONT=&amp]glxinfo -B[/FONT][/COLOR] cannot be shown due to the missing Mesa package. I then Googled and discovered some needed commands to fix the error. One of the commands was about installing or updating the Mesa package. I then ran the suggested commands and after that I got the needed information with [COLOR=#000000][FONT=&amp]glxinfo -B without any error.

Furthermore, the developer(s) of Mesa had inserted a general post-install text shown to the user in the Terminal after the installation of Mesa. This text included a suggestion to uninstall some Mesa package before upgrading the operating system i.e. from which I wondered that in April before the next Ubuntu LTS release I need to uninstall the Mesa package which the error of [/FONT][/COLOR][COLOR=#000000][FONT=&amp]glxinfo -B suggested to install and re-install it after the upgrade.[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2024-01-26
All you needed to do to get glxinfo was install mesa-utils:
```
sudo apt-get install mesa-utils
```
And I don't remember ever seeing a message that you need to remove that before you upgrade (and I've upgraded various Linux installs with that installed plenty of times). I don't know what else to tell you unless you can be more specific about what other commands you may have run.

---

### Post by vushido on 2024-01-26
I guess that I need to uninstall and install [COLOR=#000000][FONT=&quot]mesa-utils[/FONT][/COLOR] again in order to copy/paste that message.
[COLOR=#000000][FONT=&quot][/FONT][/COLOR]How can I do it safely?

---

### Post by MAFoElffen on 2024-01-27
Did you install mesa-utils from the Ubuntu Repo's? Or from some external source?

If from the Ubuntu Repo's, then you just install initially, and it continues to update in the normal channels. Nothing else needed.

---

### Post by vushido on 2024-01-27
I installed [COLOR=#000000]mesa-utils from the Terminal. It was sudo something that I found via Google in order to fix the aforementioned error that did not let me to see the relevant information at the beginning.
How to check from where I installed mesa-utils?[/COLOR]

---

### Post by MAFoElffen on 2024-01-27
```

apt list mesa* --installed

```
For example
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ apt list mesa* --installed
Listing... Done
mesa-utils-bin/jammy,now 8.4.0-1ubuntu1 amd64 [installed,automatic]
mesa-utils/jammy,now 8.4.0-1ubuntu1 amd64 [installed,automatic]
mesa-va-drivers/jammy-updates,now 23.0.4-0ubuntu1~22.04.1 amd64 [installed,automatic]
mesa-vdpau-drivers/jammy-updates,now 23.0.4-0ubuntu1~22.04.1 amd64 [installed,automatic]
mesa-vulkan-drivers/jammy-updates,now 23.0.4-0ubuntu1~22.04.1 amd64 [installed,automatic]

```
Tells me which packages, where they came from, and their package versions.

Then, if you look in the /var/log/apt/ folder at files term.log and history.log, you can see when it was installed and/or updated, from what source, and when that happened.

---

### Post by vushido on 2024-01-28
```
apt list mesa* --installed
```

tells me

```
mesa-utils-bin/jammy,now 8.4.0-1ubuntu1 amd64 [installed,automatic]mesa-utils/jammy,now 8.4.0-1ubuntu1 amd64 [installed]
mesa-va-drivers/jammy,now 23.3.4~kisak1~j amd64 [installed,automatic]
mesa-vdpau-drivers/jammy,now 23.3.4~kisak1~j amd64 [installed,automatic]
mesa-vulkan-drivers/jammy,now 23.3.4~kisak1~j amd64 [installed,automatic]
mesa-vulkan-drivers/jammy,now 23.3.4~kisak1~j i386 [installed,automatic]
```

The file "term.log" tells me

```
Log started: 2024-01-23  15:59:30Selecting previously unselected package mesa-utils-bin:amd64.
(Andmebaasi lugemine ... 
(Andmebaasi lugemine ... 5%
(Andmebaasi lugemine ... 10%
(Andmebaasi lugemine ... 15%
(Andmebaasi lugemine ... 20%
(Andmebaasi lugemine ... 25%
(Andmebaasi lugemine ... 30%
(Andmebaasi lugemine ... 35%
(Andmebaasi lugemine ... 40%
(Andmebaasi lugemine ... 45%
(Andmebaasi lugemine ... 50%
(Andmebaasi lugemine ... 55%
(Andmebaasi lugemine ... 60%
(Andmebaasi lugemine ... 65%
(Andmebaasi lugemine ... 70%
(Andmebaasi lugemine ... 75%
(Andmebaasi lugemine ... 80%
(Andmebaasi lugemine ... 85%
(Andmebaasi lugemine ... 90%
(Andmebaasi lugemine ... 95%
(Andmebaasi lugemine ... 100%
(Andmebaasi lugemine ... 327189 files and directories currently installed.)
Preparing to unpack .../mesa-utils-bin_8.4.0-1ubuntu1_amd64.deb ...
Unpacking mesa-utils-bin:amd64 (8.4.0-1ubuntu1) ...
Selecting previously unselected package mesa-utils.
Preparing to unpack .../mesa-utils_8.4.0-1ubuntu1_amd64.deb ...
Unpacking mesa-utils (8.4.0-1ubuntu1) ...
Paki mesa-utils-bin:amd64 (8.4.0-1ubuntu1) paikasättimine ...
Paki mesa-utils (8.4.0-1ubuntu1) paikasättimine ...
Processing triggers for man-db (2.10.2-1) ...

Log ended: 2024-01-23  15:59:36

Log started: 2024-01-23  16:08:51
(Andmebaasi lugemine ... 
(Andmebaasi lugemine ... 5%
(Andmebaasi lugemine ... 10%
(Andmebaasi lugemine ... 15%
(Andmebaasi lugemine ... 20%
(Andmebaasi lugemine ... 25%
(Andmebaasi lugemine ... 30%
(Andmebaasi lugemine ... 35%
(Andmebaasi lugemine ... 40%
(Andmebaasi lugemine ... 45%
(Andmebaasi lugemine ... 50%
(Andmebaasi lugemine ... 55%
(Andmebaasi lugemine ... 60%
(Andmebaasi lugemine ... 65%
(Andmebaasi lugemine ... 70%
(Andmebaasi lugemine ... 75%
(Andmebaasi lugemine ... 80%
(Andmebaasi lugemine ... 85%
(Andmebaasi lugemine ... 90%
(Andmebaasi lugemine ... 95%
(Andmebaasi lugemine ... 100%
(Andmebaasi lugemine ... 327234 files and directories currently installed.)
Preparing to unpack .../00-libegl-mesa0_23.3.3~kisak1~j_amd64.deb ...
Unpacking libegl-mesa0:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../01-libgbm1_23.3.3~kisak1~j_amd64.deb ...
De-configuring libgbm1:i386 (23.0.4-0ubuntu1~22.04.1), to allow configuration of libgbm1:amd64 (23.0.4-0ubuntu1~22.04.1) ...
Unpacking libgbm1:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../02-libgbm1_23.3.3~kisak1~j_i386.deb ...
Unpacking libgbm1:i386 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../03-libllvm15_1%3a15.0.7-1~kisak~j_amd64.deb ...
De-configuring libllvm15:i386 (1:15.0.7-0ubuntu0.22.04.3), to allow configuration of libllvm15:amd64 (1:15.0.7-0ubuntu0.22.04.3) ...
Unpacking libllvm15:amd64 (1:15.0.7-1~kisak~j) over (1:15.0.7-0ubuntu0.22.04.3) ...
Preparing to unpack .../04-libllvm15_1%3a15.0.7-1~kisak~j_i386.deb ...
Unpacking libllvm15:i386 (1:15.0.7-1~kisak~j) over (1:15.0.7-0ubuntu0.22.04.3) ...
Preparing to unpack .../05-libosmesa6_23.3.3~kisak1~j_i386.deb ...
De-configuring libosmesa6:amd64 (23.0.4-0ubuntu1~22.04.1), to allow configuration of libosmesa6:i386 (23.0.4-0ubuntu1~22.04.1) ...
Unpacking libosmesa6:i386 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../06-libosmesa6_23.3.3~kisak1~j_amd64.deb ...
Unpacking libosmesa6:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../07-libgl1-mesa-dri_23.3.3~kisak1~j_amd64.deb ...
De-configuring libgl1-mesa-dri:i386 (23.0.4-0ubuntu1~22.04.1), to allow configuration of libgl1-mesa-dri:amd64 (23.0.4-0ubuntu1~22.04.1) ...
Unpacking libgl1-mesa-dri:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../08-libgl1-mesa-dri_23.3.3~kisak1~j_i386.deb ...
Unpacking libgl1-mesa-dri:i386 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../09-libglx-mesa0_23.3.3~kisak1~j_i386.deb ...
De-configuring libglx-mesa0:amd64 (23.0.4-0ubuntu1~22.04.1), to allow configuration of libglx-mesa0:i386 (23.0.4-0ubuntu1~22.04.1) ...
Unpacking libglx-mesa0:i386 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../10-libglx-mesa0_23.3.3~kisak1~j_amd64.deb ...
Unpacking libglx-mesa0:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../11-libglapi-mesa_23.3.3~kisak1~j_amd64.deb ...
De-configuring libglapi-mesa:i386 (23.0.4-0ubuntu1~22.04.1), to allow configuration of libglapi-mesa:amd64 (23.0.4-0ubuntu1~22.04.1) ...
Unpacking libglapi-mesa:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../12-libglapi-mesa_23.3.3~kisak1~j_i386.deb ...
Unpacking libglapi-mesa:i386 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../13-libxatracker2_23.3.3~kisak1~j_amd64.deb ...
Unpacking libxatracker2:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../14-mesa-va-drivers_23.3.3~kisak1~j_amd64.deb ...
Unpacking mesa-va-drivers:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../15-mesa-vdpau-drivers_23.3.3~kisak1~j_amd64.deb ...
Unpacking mesa-vdpau-drivers:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../16-mesa-vulkan-drivers_23.3.3~kisak1~j_i386.deb ...
De-configuring mesa-vulkan-drivers:amd64 (23.0.4-0ubuntu1~22.04.1), to allow configuration of mesa-vulkan-drivers:i386 (23.0.4-0ubuntu1~22.04.1) ...
Unpacking mesa-vulkan-drivers:i386 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Preparing to unpack .../17-mesa-vulkan-drivers_23.3.3~kisak1~j_amd64.deb ...
Unpacking mesa-vulkan-drivers:amd64 (23.3.3~kisak1~j) over (23.0.4-0ubuntu1~22.04.1) ...
Paki libgbm1:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libgbm1:i386 (23.3.3~kisak1~j) paikasättimine ...
Paki libglapi-mesa:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libglapi-mesa:i386 (23.3.3~kisak1~j) paikasättimine ...
Paki libllvm15:amd64 (1:15.0.7-1~kisak~j) paikasättimine ...
Paki libllvm15:i386 (1:15.0.7-1~kisak~j) paikasättimine ...
Paki mesa-va-drivers:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libosmesa6:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libosmesa6:i386 (23.3.3~kisak1~j) paikasättimine ...
Paki mesa-vulkan-drivers:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki mesa-vulkan-drivers:i386 (23.3.3~kisak1~j) paikasättimine ...
Paki mesa-vdpau-drivers:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libgl1-mesa-dri:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libgl1-mesa-dri:i386 (23.3.3~kisak1~j) paikasättimine ...
Paki libxatracker2:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libegl-mesa0:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libglx-mesa0:amd64 (23.3.3~kisak1~j) paikasättimine ...
Paki libglx-mesa0:i386 (23.3.3~kisak1~j) paikasättimine ...
Processing triggers for libc-bin (2.35-0ubuntu3.6) ...
Log ended: 2024-01-23  16:09:21

Log started: 2024-01-25  21:09:25
(Andmebaasi lugemine ... 
(Andmebaasi lugemine ... 5%
(Andmebaasi lugemine ... 10%
(Andmebaasi lugemine ... 15%
(Andmebaasi lugemine ... 20%
(Andmebaasi lugemine ... 25%
(Andmebaasi lugemine ... 30%
(Andmebaasi lugemine ... 35%
(Andmebaasi lugemine ... 40%
(Andmebaasi lugemine ... 45%
(Andmebaasi lugemine ... 50%
(Andmebaasi lugemine ... 55%
(Andmebaasi lugemine ... 60%
(Andmebaasi lugemine ... 65%
(Andmebaasi lugemine ... 70%
(Andmebaasi lugemine ... 75%
(Andmebaasi lugemine ... 80%
(Andmebaasi lugemine ... 85%
(Andmebaasi lugemine ... 90%
(Andmebaasi lugemine ... 95%
(Andmebaasi lugemine ... 100%
(Andmebaasi lugemine ... 364610 files and directories currently installed.)
Preparing to unpack .../systemd-timesyncd_249.11-0ubuntu3.12_amd64.deb ...
Unpacking systemd-timesyncd (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../libudev1_249.11-0ubuntu3.12_i386.deb ...
De-configuring libudev1:amd64 (249.11-0ubuntu3.11), to allow configuration of libudev1:i386 (249.11-0ubuntu3.11) ...
Unpacking libudev1:i386 (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../libudev1_249.11-0ubuntu3.12_amd64.deb ...
Unpacking libudev1:amd64 (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Paki libudev1:amd64 (249.11-0ubuntu3.12) paikasättimine ...
(Andmebaasi lugemine ... 
(Andmebaasi lugemine ... 5%
(Andmebaasi lugemine ... 10%
(Andmebaasi lugemine ... 15%
(Andmebaasi lugemine ... 20%
(Andmebaasi lugemine ... 25%
(Andmebaasi lugemine ... 30%
(Andmebaasi lugemine ... 35%
(Andmebaasi lugemine ... 40%
(Andmebaasi lugemine ... 45%
(Andmebaasi lugemine ... 50%
(Andmebaasi lugemine ... 55%
(Andmebaasi lugemine ... 60%
(Andmebaasi lugemine ... 65%
(Andmebaasi lugemine ... 70%
(Andmebaasi lugemine ... 75%
(Andmebaasi lugemine ... 80%
(Andmebaasi lugemine ... 85%
(Andmebaasi lugemine ... 90%
(Andmebaasi lugemine ... 95%
(Andmebaasi lugemine ... 100%
(Andmebaasi lugemine ... 364610 files and directories currently installed.)
Preparing to unpack .../0-libudev-dev_249.11-0ubuntu3.12_amd64.deb ...
Unpacking libudev-dev:amd64 (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../1-systemd_249.11-0ubuntu3.12_amd64.deb ...
Unpacking systemd (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../2-udev_249.11-0ubuntu3.12_amd64.deb ...
Unpacking udev (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../3-libnss-systemd_249.11-0ubuntu3.12_amd64.deb ...
Unpacking libnss-systemd:amd64 (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../4-libsystemd0_249.11-0ubuntu3.12_i386.deb ...
De-configuring libsystemd0:amd64 (249.11-0ubuntu3.11), to allow configuration of libsystemd0:i386 (249.11-0ubuntu3.11) ...
Unpacking libsystemd0:i386 (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../5-libsystemd0_249.11-0ubuntu3.12_amd64.deb ...
Unpacking libsystemd0:amd64 (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Paki libsystemd0:amd64 (249.11-0ubuntu3.12) paikasättimine ...
Paki systemd (249.11-0ubuntu3.12) paikasättimine ...
(Andmebaasi lugemine ... 
(Andmebaasi lugemine ... 5%
(Andmebaasi lugemine ... 10%
(Andmebaasi lugemine ... 15%
(Andmebaasi lugemine ... 20%
(Andmebaasi lugemine ... 25%
(Andmebaasi lugemine ... 30%
(Andmebaasi lugemine ... 35%
(Andmebaasi lugemine ... 40%
(Andmebaasi lugemine ... 45%
(Andmebaasi lugemine ... 50%
(Andmebaasi lugemine ... 55%
(Andmebaasi lugemine ... 60%
(Andmebaasi lugemine ... 65%
(Andmebaasi lugemine ... 70%
(Andmebaasi lugemine ... 75%
(Andmebaasi lugemine ... 80%
(Andmebaasi lugemine ... 85%
(Andmebaasi lugemine ... 90%
(Andmebaasi lugemine ... 95%
(Andmebaasi lugemine ... 100%
(Andmebaasi lugemine ... 364610 files and directories currently installed.)
Preparing to unpack .../00-systemd-sysv_249.11-0ubuntu3.12_amd64.deb ...
Unpacking systemd-sysv (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../01-systemd-oomd_249.11-0ubuntu3.12_amd64.deb ...
Unpacking systemd-oomd (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../02-libpam-systemd_249.11-0ubuntu3.12_amd64.deb ...
Unpacking libpam-systemd:amd64 (249.11-0ubuntu3.12) over (249.11-0ubuntu3.11) ...
Preparing to unpack .../03-libegl-mesa0_23.3.4~kisak1~j_amd64.deb ...
Unpacking libegl-mesa0:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../04-libgbm1_23.3.4~kisak1~j_amd64.deb ...
De-configuring libgbm1:i386 (23.3.3~kisak1~j), to allow configuration of libgbm1:amd64 (23.3.3~kisak1~j) ...
Unpacking libgbm1:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../05-libgbm1_23.3.4~kisak1~j_i386.deb ...
Unpacking libgbm1:i386 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../06-libgl1-mesa-dri_23.3.4~kisak1~j_i386.deb ...
De-configuring libgl1-mesa-dri:amd64 (23.3.3~kisak1~j), to allow configuration of libgl1-mesa-dri:i386 (23.3.3~kisak1~j) ...
Unpacking libgl1-mesa-dri:i386 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../07-libgl1-mesa-dri_23.3.4~kisak1~j_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../08-libosmesa6_23.3.4~kisak1~j_i386.deb ...
De-configuring libosmesa6:amd64 (23.3.3~kisak1~j), to allow configuration of libosmesa6:i386 (23.3.3~kisak1~j) ...
Unpacking libosmesa6:i386 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../09-libosmesa6_23.3.4~kisak1~j_amd64.deb ...
Unpacking libosmesa6:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../10-libglx-mesa0_23.3.4~kisak1~j_i386.deb ...
De-configuring libglx-mesa0:amd64 (23.3.3~kisak1~j), to allow configuration of libglx-mesa0:i386 (23.3.3~kisak1~j) ...
Unpacking libglx-mesa0:i386 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../11-libglx-mesa0_23.3.4~kisak1~j_amd64.deb ...
Unpacking libglx-mesa0:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../12-libglapi-mesa_23.3.4~kisak1~j_amd64.deb ...
De-configuring libglapi-mesa:i386 (23.3.3~kisak1~j), to allow configuration of libglapi-mesa:amd64 (23.3.3~kisak1~j) ...
Unpacking libglapi-mesa:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../13-libglapi-mesa_23.3.4~kisak1~j_i386.deb ...
Unpacking libglapi-mesa:i386 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../14-brave-browser_1.62.153_amd64.deb ...
Unpacking brave-browser (1.62.153) over (1.61.120) ...
Preparing to unpack .../15-libxatracker2_23.3.4~kisak1~j_amd64.deb ...
Unpacking libxatracker2:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../16-mesa-va-drivers_23.3.4~kisak1~j_amd64.deb ...
Unpacking mesa-va-drivers:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../17-mesa-vdpau-drivers_23.3.4~kisak1~j_amd64.deb ...
Unpacking mesa-vdpau-drivers:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../18-mesa-vulkan-drivers_23.3.4~kisak1~j_amd64.deb ...
De-configuring mesa-vulkan-drivers:i386 (23.3.3~kisak1~j), to allow configuration of mesa-vulkan-drivers:amd64 (23.3.3~kisak1~j) ...
Unpacking mesa-vulkan-drivers:amd64 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Preparing to unpack .../19-mesa-vulkan-drivers_23.3.4~kisak1~j_i386.deb ...
Unpacking mesa-vulkan-drivers:i386 (23.3.4~kisak1~j) over (23.3.3~kisak1~j) ...
Paki mesa-vulkan-drivers:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki mesa-vulkan-drivers:i386 (23.3.4~kisak1~j) paikasättimine ...
Paki mesa-vdpau-drivers:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki systemd-sysv (249.11-0ubuntu3.12) paikasättimine ...
Paki libgbm1:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki libgbm1:i386 (23.3.4~kisak1~j) paikasättimine ...
Paki libnss-systemd:amd64 (249.11-0ubuntu3.12) paikasättimine ...
Paki libsystemd0:i386 (249.11-0ubuntu3.12) paikasättimine ...
Paki libxatracker2:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki systemd-timesyncd (249.11-0ubuntu3.12) paikasättimine ...
Paki udev (249.11-0ubuntu3.12) paikasättimine ...
Paki libudev-dev:amd64 (249.11-0ubuntu3.12) paikasättimine ...
Paki libglapi-mesa:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki libglapi-mesa:i386 (23.3.4~kisak1~j) paikasättimine ...
Paki libudev1:i386 (249.11-0ubuntu3.12) paikasättimine ...
Paki brave-browser (1.62.153) paikasättimine ...
Paki libpam-systemd:amd64 (249.11-0ubuntu3.12) paikasättimine ...
Paki systemd-oomd (249.11-0ubuntu3.12) paikasättimine ...
Paki mesa-va-drivers:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki libosmesa6:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki libosmesa6:i386 (23.3.4~kisak1~j) paikasättimine ...
Paki libgl1-mesa-dri:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki libgl1-mesa-dri:i386 (23.3.4~kisak1~j) paikasättimine ...
Paki libegl-mesa0:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki libglx-mesa0:amd64 (23.3.4~kisak1~j) paikasättimine ...
Paki libglx-mesa0:i386 (23.3.4~kisak1~j) paikasättimine ...
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.5.0-15-generic
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.6) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Log ended: 2024-01-25  21:11:49
```

The file "history.log" tells me

```
Start-Date: 2024-01-23  15:59:30Commandline: apt install mesa-utils
Requested-By: user (1000)
Install: mesa-utils-bin:amd64 (8.4.0-1ubuntu1, automatic), mesa-utils:amd64 (8.4.0-1ubuntu1)
End-Date: 2024-01-23  15:59:36


Start-Date: 2024-01-23  16:08:51
Commandline: aptdaemon role='role-commit-packages' sender=':1.172'
Upgrade: libglx-mesa0:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libglx-mesa0:i386 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libgbm1:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libgbm1:i386 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libllvm15:amd64 (1:15.0.7-0ubuntu0.22.04.3, 1:15.0.7-1~kisak~j), libllvm15:i386 (1:15.0.7-0ubuntu0.22.04.3, 1:15.0.7-1~kisak~j), libxatracker2:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), mesa-va-drivers:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libgl1-mesa-dri:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libgl1-mesa-dri:i386 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libosmesa6:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libosmesa6:i386 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), mesa-vulkan-drivers:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), mesa-vulkan-drivers:i386 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libglapi-mesa:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libglapi-mesa:i386 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), libegl-mesa0:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j), mesa-vdpau-drivers:amd64 (23.0.4-0ubuntu1~22.04.1, 23.3.3~kisak1~j)

End-Date: 2024-01-23  16:09:21

Start-Date: 2024-01-25  21:09:25
Commandline: aptdaemon role='role-commit-packages' sender=':1.88'
Upgrade: udev:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), systemd-oomd:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libglx-mesa0:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libglx-mesa0:i386 (23.3.3~kisak1~j, 23.3.4~kisak1~j), systemd-timesyncd:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libpam-systemd:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libgbm1:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libgbm1:i386 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libsystemd0:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libsystemd0:i386 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libnss-systemd:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libudev-dev:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libxatracker2:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), systemd:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libudev1:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libudev1:i386 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), mesa-va-drivers:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libgl1-mesa-dri:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libgl1-mesa-dri:i386 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libosmesa6:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libosmesa6:i386 (23.3.3~kisak1~j, 23.3.4~kisak1~j), mesa-vulkan-drivers:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), mesa-vulkan-drivers:i386 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libglapi-mesa:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), libglapi-mesa:i386 (23.3.3~kisak1~j, 23.3.4~kisak1~j), brave-browser:amd64 (1.61.120, 1.62.153), systemd-sysv:amd64 (249.11-0ubuntu3.11, 249.11-0ubuntu3.12), libegl-mesa0:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j), mesa-vdpau-drivers:amd64 (23.3.3~kisak1~j, 23.3.4~kisak1~j)
End-Date: 2024-01-25  21:11:49
```

I discovered via Google search that I used the tutorial on [https://unixcop.com/how-to-install-mesa-drivers-ubuntu/](https://unixcop.com/how-to-install-mesa-drivers-ubuntu/) in order to install the Mesa.

---

### Post by MAFoElffen on 2024-01-28
So you are using the newer version of mesa-utils STABLE from ppa:kisak/kisak-mesa instead of from the normal Repo's. Common practice and works well.

---

### Post by vushido on 2024-01-28
I.e. it continues/does not continue to update in the unusual channels and something else is needed as I do not use the normal Repo?

---

### Post by Yellow Pasque on 2024-01-28
Oh, so you are referring to this message?:
> It's strongly recommended to remove this PPA before upgrading to a newer Ubuntu release or using another mesa PPA.

```
sudo apt install ppa-purge
sudo ppa-purge ppa:kisak/kisak-mesa
```

Yes, follow those directions before you upgrade to 24.04. In fact, you could even remove the PPA now if you wanted. It was not necessary to add the PPA just to install mesa-utils.

---

### Post by vushido on 2024-01-28
I am [COLOR=#000000]referring to this message.

I could not detect which steps are mandatory in the Unixcop's tutorial, so I followed all of these.

[/COLOR]sudo ppa-purge ppa:kisak/kisak-mesa tells me:[COLOR=#000000]

[/COLOR]```
he following additional packages will be installed:  libdrm-intel1:i386 libgl1-amber-dri libpciaccess0:i386
Suggested packages:
  libgl1-amber-dri:i386
Paigaldatakse järgnevad NEW paketid:
  libdrm-intel1:i386 libgl1-amber-dri libpciaccess0:i386
Järgnevatest pakettidest paigaldatakse OLD VERSIONS:
  libegl-mesa0 libgbm1 libgbm1:i386 libgl1-mesa-dri libgl1-mesa-dri:i386
  libglapi-mesa libglapi-mesa:i386 libglx-mesa0 libglx-mesa0:i386 libllvm15
  libllvm15:i386 libosmesa6 libosmesa6:i386 libxatracker2 mesa-va-drivers
  mesa-vdpau-drivers mesa-vulkan-drivers mesa-vulkan-drivers:i386
```

Shall I choose Yes or No? Why is it installing and uninstalling if you told me that command only removes PPA?

---

### Post by deadflowr on 2024-01-28
Is this what you're following?
[https://unixcop.com/how-to-install-mesa-drivers-ubuntu/]("https://unixcop.com/how-to-install-mesa-drivers-ubuntu/")

---

### Post by MAFoElffen on 2024-01-28
I must be very confused. 

You showed us output that said you already had mesa-utils installed. Then you told me that link was the guide you followed and used when you installed that...

Why are you doing it again?

---

### Post by vushido on 2024-01-29
[FONT=Verdana]> **deadflowr said:**
> Is this what you're following?[/FONT]
[https://unixcop.com/how-to-install-mesa-drivers-ubuntu/](https://unixcop.com/how-to-install-mesa-drivers-ubuntu/)[FONT=Verdana][/FONT]

Yes.

---

### Post by vushido on 2024-01-29
I am not doing it again after Yellow Pasque found [the text]("https://ubuntuforums.org/showthread.php?t=2494474&p=14177420#post14177420") that I was talking about and could not find.

---

### Post by Yellow Pasque on 2024-01-29
> **vushido said:**
> Shall I choose Yes or No? Why is it installing and uninstalling if you told me that command only removes PPA?

When you purge the PPA, you are reverting to the standard version of the packages. So the output you showed was not proposing complete removal of packages, but instead, it was downgrading the packages. There were some packages to install, and I can only guess there are differences in dependencies with how kisak builds its packages. Anyway, it is safe to do the ppa-purge, or if you still don't want to do it, you can leave the PPA in place until you upgrade and keep the newer mesa version (it may help a bit with 3D performance). Either way..

---

