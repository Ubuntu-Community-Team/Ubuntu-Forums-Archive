---
title: "Install Nvidia GTX 1050"
date: 2017-11-14
forum: Hardware
---

### Post by xavier12358 on 2017-11-14
Hello,

I just buy a HP:
[https://www.amazon.fr/dp/B0743B9YWJ/ref=pe_3044141_189395771_TE_dp_1](https://www.amazon.fr/dp/B0743B9YWJ/ref=pe_3044141_189395771_TE_dp_1)

So I have a NVIDIA GTX 1050, and I try to install the driver.

I go to the sofware_property and I try the 4 drivers allow but they don't work. The disponibled drivers are 378/381/384 and 387.

How can I make the driver work properly?

---

### Post by Bashing-om on 2017-11-14
xavier12358; Hello;

Can not tell from the info provided what the problem may be.
What have we to work with ?
post back - between code tags - the outputs of terminal commands:
```

dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

see then
[INDENT][INDENT][INDENT]what there is to do
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2017-11-14
You may need newest, but if you attempted to install more than one, without purging older one first, you will have issues.
New install of driver, does not uninstall/purge older driver and you get conflicts.

       If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 

      
  you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by xavier12358 on 2017-11-14
@Bashing-om
Here is the result in my terminal;

```

dpkg -l | grep -i nvidia
ii  bbswitch-dkms                              0.8-3ubuntu1                                 amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-387                               387.12-0ubuntu0~gpu16.04.1                   amd64        NVIDIA CUDA runtime library
ii  nvidia-387                                 387.12-0ubuntu0~gpu16.04.1                   amd64        NVIDIA binary driver - version 387.12
ii  nvidia-opencl-icd-387                      387.12-0ubuntu0~gpu16.04.1                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                               0.8.2                                        amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                            387.22-0ubuntu0~gpu16.04.1                   amd64        Tool for configuring the NVIDIA graphics driver

cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.10.0-28-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.10.0-28-generic/updates/dkms
Found nvidia module: nvidia_378_modeset.ko
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
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:591b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c8d
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
The number of cards has changed!
Has the system changed? Yes
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-378/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? no
Is fglrx enabled? no
Is mesa enabled? no
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
System configuration has changed
Single card detected
Selecting mesa
/usr/bin/update-alternatives --set x86_64-linux-gnu_gl_conf /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
update-alternatives status 0
Calling ldconfig
ldconfig status 0
/usr/bin/update-alternatives --set x86_64-linux-gnu_egl_conf /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf
update-alternatives status 0
Calling ldconfig
ldconfig status 0
Error: no alternative found for unblacklist
Removing xorg.conf. Path: /etc/X11/xorg.conf
Moved /etc/X11/xorg.conf to /etc/X11/xorg.conf.11142017
System configuration has changed


```


@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711") I have already install the package to get more drivers, this is the reason why I have 4 drivers disponibles. But the 4 don't work.
     

And when I start nvidia-settings:
```

nvidia-settings 

ERROR: Error querying enabled displays on GPU 0 (Missing Extension).


ERROR: Error querying connected displays on GPU 0 (Missing Extension).

** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.


```

---

### Post by Bashing-om on 2017-11-14
xavier12358; Yuk.

The output of the log file raises more questions than it answers.

post back:
```

lspci -k|grep -iEA5 'vga|3d'
cat /etc/X11/xorg.conf

```
I will not be surprised if the xorg.conf file does not exist .

But. let us know what the hardware is and what the system expects.

[INDENT][INDENT]we can do that[/INDENT][/INDENT]

---

### Post by xavier12358 on 2017-11-14
Here is the other result in terminal:
```

lspci -k|grep -iEA5 'vga|3d'
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
    DeviceName: Intel Kabylake HD Graphics GT2
    Subsystem: Hewlett-Packard Company Device 8259
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 05)
--
01:00.0 3D controller: NVIDIA Corporation Device 1c8d (rev a1)
    Subsystem: Hewlett-Packard Company Device 8259
    Kernel modules: nvidiafb, nouveau, nvidia_387_drm, nvidia_387
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company RTS522A PCI Express Card Reader
    Kernel driver in use: rtsx_pci


cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory



```

---

### Post by Bashing-om on 2017-11-14
xavier12358; confirmed;

 we do have hybrid graphics - nvidia/Intel .

Got to be a reason that the driver fails to install. How about that this is a EFI system, and in that case one must disable secure boot in bios ?

Try again as
disable secure boot in the firmware settings;
boot into the ubuntu install and now run:
```

sudo apt purge nvidia*
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade

```

where we have the system choose the driver .
reboot for the new driver to take effect

all better now ?

---

### Post by xavier12358 on 2017-11-14
YESSSSS!!! You made it.

The card is properly recongnized with driver 387. Thanks a lot.

---

### Post by Bashing-om on 2017-11-14
xavier12358; Outstanding !

Was the issue secure boot related ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by xavier12358 on 2017-11-14
I think it comes from the way I purge and reinstall the driver . 
The secure boot was already disable

---

### Post by Bashing-om on 2017-11-14
xavier12358; Well -

in any event -- all's well that ends well :)

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by croraf on 2018-10-06
> **Bashing-om said:**
> xavier12358; confirmed;

 we do have hybrid graphics - nvidia/Intel .

Got to be a reason that the driver fails to install. How about that this is a EFI system, and in that case one must disable secure boot in bios ?

Try again as
disable secure boot in the firmware settings;
boot into the ubuntu install and now run:
```

sudo apt purge nvidia*
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade

```

where we have the system choose the driver .
reboot for the new driver to take effect

all better now ?

This fixed my issue too. I played game on lowest settings with lag for 1 year :(. (I also disabled secure intell in boot - Lenovo, but I'll reenable it as I dont think it contributed)

---

### Post by oldos2er on 2018-10-06
Old thread closed.

---

