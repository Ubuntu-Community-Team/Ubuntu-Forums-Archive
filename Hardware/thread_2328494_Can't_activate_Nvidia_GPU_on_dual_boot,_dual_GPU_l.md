---
title: "Can't activate Nvidia GPU on dual boot, dual GPU laptop w/16.04 LTS"
date: 2016-06-21
forum: Hardware
---

### Post by Raffles727 on 2016-06-21
Greetings all,
I have an Acer Aspire E15 laptop which came with Windows 10 and includes a GeForce 940M GPU in addition to the Intel card.
The intention is to use it as a portable platform to run X-Plane 10 as I travel a lot.
X-Plane works on Windows and it shows itself using the Nvidia GPU.
I partitioned the hard drive 50/50 and installed Ubuntu (long story) 16.04 on the new partition.
I have eventually gotten everything to work including X-Plane but not the Nvidia GPU.
The Software and Updates Center shows using NVIDIA binary driver version 367.27 which I installed with the Synaptic Package Manager.
There is nothing in the Nvidia Xserver Settings and the Quick Switch Icon next to the Wifi icon is the Nvidia symbol, but shows that the Intel driver is active.
Indeed the "About This Computer" screen shows only the Intel dinosaur.
I have tried all the suggestions I could find, purge, reinstall, etc and the only one thing that did change something once, was to edit "nomodeset" into the Grub.
However, after that , the GPU could not find the second HDMI screen and X-Plane would not run.
This is what lshw -c video shows :

```
*-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:c2000000-c2ffffff memory:d0000000-dfffffff ioport:5000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: GM108M [GeForce 940M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c3000000-c3ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:3000(size=128)

```
I can upload a few more screen shots and hardware dump if necessary
Thanks in advance.
Ralph

---

### Post by Raffles727 on 2016-06-22
I also ran this on advice from another forum but it appeared to amount to nothing.

```
ralph@ralph-Aspire-E5-573G:~$ export LD_LIBRARY_PATH=/usr/lib/nvidia-367
ralph@ralph-Aspire-E5-573G:~$ glxinfo
name of display: :0
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  37
  Current serial number in output stream:  38
ralph@ralph-Aspire-E5-573G:~$ export LD_LIBRARY_PATH=/usr/lib/nvidia-367
ralph@ralph-Aspire-E5-573G:~$ ldd $(which glxinfo)
    linux-vdso.so.1 =>  (0x00007ffd317b6000)
    libGL.so.1 => /usr/lib/nvidia-367/libGL.so.1 (0x00007f3b2ea7d000)
    libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f3b2e725000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f3b2e35b000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f3b2e157000)
    libGLX.so.0 => /usr/lib/nvidia-367/libGLX.so.0 (0x00007f3b2df27000)
    libGLdispatch.so.0 => /usr/lib/nvidia-367/libGLdispatch.so.0 (0x00007f3b2dc3d000)
    libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f3b2da1b000)
    /lib64/ld-linux-x86-64.so.2 (0x00005618af51a000)
    libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f3b2d809000)
    libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f3b2d604000)
    libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f3b2d3fe000)
ralph@ralph-Aspire-E5-573G:~$
```

---

### Post by Raffles727 on 2016-06-23
As it turns out, inserting "nomodeset" into the Grub does activate the Nvidia GPU (if the Gallium driver stack is running the Nvidia card).
[IMG]http://i35.servimg.com/u/f35/17/29/29/41/galliu10.png[/IMG]
However it doesn't recognize the HDMI screen and X-Plane doesn't start and gives me the following message :

> This video card is: DX10 or 11 - With instancing
0:00:00.000 E/SYS: +-------------------------------------------------------------------------------
0:00:00.000 E/SYS: | X-Plane does not support the Gallium driver stack.
0:00:00.000 E/SYS: | First, try updating or re-installing your graphics drivers.
0:00:00.000 E/SYS: | If this does not help, check your graphics card specifications.
0:00:00.000 E/SYS: | For tech support, email [EMAIL="info@x-plane.com"]info@x-plane.com[/EMAIL]
0:00:00.000 E/SYS: | (OGL_extensions.cpp:983)
0:00:00.000 E/SYS: +-------------------------------------------------------------------------------
----- X-Plane has shut down -----

I know that a friend has X-plane up and running on his Ubuntu machine with a proprietary driver, but a different Nvidia GPU, GTX7 something
When I first installed Ubuntu, the proprietary drivers showed up in the "Additional drivers" tab, but at some point I had to purge nvidia as I had a black screen.
Now only open source drivers show up.... see image below
How can I get the proprietary drivers to show up?
[IMG]http://i35.servimg.com/u/f35/17/29/29/41/screen10.png[/IMG]

---

### Post by X-RED_Tech on 2016-06-23
All "NVIDIA" are proprietary, "nouveau" is open source. The reason the proprietary drivers now show as "open source" is because you added a PPA for graphics drivers. It's just a minor annoyance and it doesn't change the status of the proprietary drivers.

---

### Post by Raffles727 on 2016-06-23
> **X-RED_Tech said:**
> All "NVIDIA" are proprietary, "nouveau" is open source. The reason the proprietary drivers now show as "open source" is because you added a PPA for graphics drivers. It's just a minor annoyance and it doesn't change the status of the proprietary drivers.

Thank you - noted. Perhaps there just isn't a Linux driver for this GPU equivalent to the Windows one.. 

Too bad because the GPU works fairly well in the Windows partition.

---

### Post by Mapring on 2016-06-23
Can you try reverting to the Nouveau driver. Then do a sudo apt autoremove to remove any leftover packages. After that remove the Nvidia graphic ppa that you have added by going to the update tab and removing it. Sudo apt update and open the additional driver again and install the Nvidia driver. (There should only be one)

I hope you can solve it.

---

### Post by X-RED_Tech on 2016-06-24
> **Mapring said:**
> (There should only be one)

Wrong. There should be as much as the versions provided by software repositories, official and third party, and "autoremove" has nothing to do with it.
To the OP: Use Nvidia 367 or 361.

---

### Post by Raffles727 on 2016-06-24
Here is the gpu-manager.log

> log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-24-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-24-generic/updates/dkms
Found nvidia module: nvidia_367_modeset.ko
Is nvidia loaded? no
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
Is nouveau loaded? yes
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:1616
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1347
BusID "PCI:4@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:04:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    eDP connector
output 1:
    HDMIA connector
Number of connected outputs for /dev/dri/card0: 2
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? no
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is mesa egl enabled? yes
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
Nothing to do
No change - nothing to do

---

### Post by briandfrank on 2016-09-30
Ralph, did you ever solve this?  I'm running into the exact same problem with the same laptop except with a 940mx.  

Thank you.

---

