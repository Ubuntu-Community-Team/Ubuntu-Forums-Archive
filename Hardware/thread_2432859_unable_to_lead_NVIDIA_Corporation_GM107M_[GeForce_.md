---
title: "unable to lead NVIDIA Corporation GM107M [GeForce GTX 960M]"
date: 2019-12-10
forum: Hardware
---

### Post by jdosio on 2019-12-10
I have been trying to get this graphics card to work on ubuntu for over a year now with no luck, but i think now i am able.
Not too long ago my nvidia drivers were blacklisted under the following command...

```

jdosio@2io-01:~$ sudo cat /var/log/gpu-manager.log
[sudo] password for jdosio: 
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.0.0-37-generic/updates/dkms
Found nvidia module: nvidia-drm.ko
Looking for amdgpu modules in /lib/modules/5.0.0-37-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:191b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:139b
BusID "PCI:2@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:02:00.0/driver
The device is not bound to any driver.
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-HDMI-A-1
output 1:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 2
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Intel hybrid system
Creating /usr/share/X11/xorg.conf.d/11-nvidia-prime.conf
Setting power control to "on" in /sys/bus/pci/devices/0000:02:00.0/power/control
Loading nvidia with "no" parameters

```

which clearly is no longer blacklisted and is also loaded,
trying

```

jdosio@2io-01:~$ nvidia-detector
none

```

Not sure what that means exactly if it said before it was loaded but to be fair i was not quite sure what loaded ment in that context either to be honest.
Anyway trying to switch to the nvidia driver through the regular nvidia-settings panel has not worked, currently my settings say i am using "Intel® HD Graphics 530 (Skylake GT2)" for "graphics", anyone know what i should do to get the nvidia 430 driver to run ?

---

### Post by slickymaster on 2019-12-10
*Thread moved to **Hardware**.*

---

### Post by jdosio on 2019-12-11
bump

---

### Post by oldfred on 2019-12-11
If you have installed multiple nVidia drivers, you have to purge.
Installing new driver does not remove an old driver and then you get conflicts. 
And do not install the .run file directly from nVidia. If you did that purge that with whatever commands it has.

Check on what is correct driver for your card/chip.
       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
It looks like 440.xx or 430.xx would work.

      
 #What is installed
dkms status
lsmod | grep nvidia
Whats available
dpkg -l | grep -i nvidia 

      
 # make sure system is up to date
sudo apt-get update
sudo apt-get upgrade 
    
       If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
    
Depending on version of Ubuntu you may or may not have correct nVidia driver in standard Ubuntu repository. But can add ppa to have all the drivers that are available.

       sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
    
       # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX  
    
       If you just want default version - recommended one
sudo ubuntu-drivers autoinstall

---

### Post by jdosio on 2019-12-12
so after following the commands you mentioned

```
jdosio@2io-01:~$ dkms status
nvidia, 430.50, 4.15.0-72-generic, x86_64: installed
nvidia, 430.50, 5.0.0-32-generic, x86_64: installed
nvidia, 430.50, 5.0.0-36-generic, x86_64: installed
nvidia, 430.50, 5.0.0-37-generic, x86_64: installed
wireguard, 0.0.20191206, 5.0.0-37-generic, x86_64: installed
jdosio@2io-01:~$ lsmod |grep nvidia
no result
```

does this mean that all the nvidia drivers displayed after "dkms status" are installed?

---

### Post by oldfred on 2019-12-12
I thought dkms showed what you have installed into the kernel.
Each kernel you have installed has a nVidia the driver 430.50 installed.

You show 4 kernels, but system normally only keeps two kernels. And one kernel is older, so is your system an update from older version, not new clean install?

My main working install still has the 4.15 kernel from 18.04 LTS. I use LTS version as main working install. Newer versions are for Ubuntu to test changes & for those who have very new hardware or really want to install the latest software. Next year I will do a new clean install of 20.04LTS to be my main working install.

---

