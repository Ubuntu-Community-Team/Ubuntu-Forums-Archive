---
title: "New Monitor LG 29wp500 Not recognized - dkms cannot compile new driver"
date: 2022-10-20
forum: Hardware
---

### Post by dgcampos2 on 2022-10-20
Hello everyone, before all, thanks so much for your help.

I am a very happy ubuntu user since many years, but sometimes linux is quite difficult to solve, that is why i present to you my problem :

I just wanted to have a bigger monitor, big mistake by me,  I bought an LG 29wp500 wide screen , without checking it for compatibility, before that i was using a samsung 21", with this graphics card :

[FONT=monospace][COLOR=#000000]01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev c7)[/COLOR]

[/FONT]with an amdgpu driver. Everything worked fine, actually very, even games (Steam works very well).

But then, i installed the new monitor, and I get a black screen, so i have to choose recovery mode to enter my system. So far so good. Now trying to upgrade my graphics card, one of the kernels had problems during installation, so i decided to enter recovery mode with another kernel, specifically the

[FONT=monospace][COLOR=#000000]Linux dgcdesktop0 5.4.0-54-generic #60-Ubuntu SMP Fri Nov 6 10:37:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
[/FONT]
During the installation of the new driver, the DKMS process shows these messages :

[FONT=monospace][COLOR=#000000]Loading new amdgpu-5.9.20.104-1247438 DKMS files...[/COLOR]
Building for 5.4.0-54-generic 5.15.0-50-generic
Building for architecture x86_64
Building initial module for 5.4.0-54-generic
EFI variables are not supported on this system
/sys/firmware/efi/efivars not found, aborting.
Done.

[/FONT]
The building process for kernel 5.4.0.54-generic works fine and the DKMS modules are installed, then for some reason i do not understand, this process also tries to install for kernel 5.15.0.50-generic, which is not on my system anymore, and so installation is aborted, with these messages from log file:

[FONT=monospace][COLOR=#000000]ProblemType: Package[/COLOR]
DKMSBuildLog:
 DKMS make.log for amdgpu-5.9.20.104-1247438 for kernel 5.15.0-50-generic (x86_64)
 jue 20 oct 2022 09:02:39 -03
 make: se entra en el directorio '/usr/src/linux-headers-5.15.0-50-generic'
 **/var/lib/dkms/amdgpu/5.9.20.104-1247438/build/Makefile:26: "Local GCC version 90404 does not match kernel compiler GCC version 90400"**
 /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/Makefile:27: "This may cause unexpected and hard-to-isolate compiler-related issues"
   CC [M]  /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/scheduler/sched_main.o
 gcc: fatal error: cannot specify ‘-o’ with ‘-c’, ‘-S’ or ‘-E’ with multiple files
 compilation terminated.
 make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/scheduler/sched_main.o] Error 1
 make[1]: *** [scripts/Makefile.build:560: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/scheduler] Error 2
 make[1]: *** Se espera a que terminen otras tareas....
   CC [M]  /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/ttm/ttm_memory.o
 gcc: fatal error: cannot specify ‘-o’ with ‘-c’, ‘-S’ or ‘-E’ with multiple files
 compilation terminated.
 make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/ttm/ttm_memory.o] Error 1
 make[2]: *** Se espera a que terminen otras tareas....
   CC [M]  /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/ttm/ttm_tt.o
   CC [M]  /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdkcl/main.o
 gcc: fatal error: cannot specify ‘-o’ with ‘-c’, ‘-S’ or ‘-E’ with multiple files
 compilation terminated.
 make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/ttm/ttm_tt.o] Error 1
 make[1]: *** [scripts/Makefile.build:560: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/ttm] Error 2
   CC [M]  /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdkcl/symbols.o
 gcc: fatal error: cannot specify ‘-o’ with ‘-c’, ‘-S’ or ‘-E’ with multiple files
 compilation terminated.
 gcc: fatal error: cannot specify ‘-o’ with ‘-c’, ‘-S’ or ‘-E’ with multiple files
 compilation terminated.
 make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdkcl/main.o] Error 1
 make[2]: *** Se espera a que terminen otras tareas....
 make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdkcl/symbols.o] Error 1
   CC [M]  /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdkcl/kcl_common.o
 gcc: fatal error: cannot specify ‘-o’ with ‘-c’, ‘-S’ or ‘-E’ with multiple files
 compilation terminated.
 make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdkcl/kcl_common.o] Error 1
 make[1]: *** [scripts/Makefile.build:560: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdkcl] Error 2
   CC [M]  /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdgpu/amdgpu_drv.o
 gcc: fatal error: cannot specify ‘-o’ with ‘-c’, ‘-S’ or ‘-E’ with multiple files
 compilation terminated.
   CC [M]  /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdgpu/amdgpu_device.o
 make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdgpu/amdgpu_drv.o] Error 1
 make[2]: *** Se espera a que terminen otras tareas....
 gcc: fatal error: cannot specify ‘-o’ with ‘-c’, ‘-S’ or ‘-E’ with multiple files
 compilation terminated.
 make[2]: *** [scripts/Makefile.build:297: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdgpu/amdgpu_device.o] Error 1
 make[1]: *** [scripts/Makefile.build:560: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build/amd/amdgpu] Error 2
 make: *** [Makefile:1900: /var/lib/dkms/amdgpu/5.9.20.104-1247438/build] Error 2
 make: se sale del directorio '/usr/src/linux-headers-5.15.0-50-generic'
DKMSKernelVersion: 5.15.0-50-generic
Date: Thu Oct 20 09:02:41 2022
Package: amdgpu-dkms 1:5.9.20.104-1247438
PackageVersion: 1:5.9.20.104-1247438
SourcePackage: amdgpu-dkms
Title: amdgpu-dkms 1:5.9.20.104-1247438: amdgpu kernel module failed to build

[/FONT]


Is there any way i can remove the 5.15.0-50-generic kernel [FONT=monospace]from the list of DKMS to build? kernel 5.4.0-54 works fine and i want to use this kernel.

[/FONT]Any help with this problem is greatly appreciated.

Thanks so much to everyone in the forum.

Best Regards,

Daniel


[FONT=monospace]
[/FONT]

---

