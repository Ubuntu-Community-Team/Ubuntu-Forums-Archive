---
title: "How to get Optimus working on ASUS U45JC in using Bumblebee in Ubuntu 11.10"
date: 2011-12-19
forum: Hardware
---

### Post by rickrobs on 2011-12-19
It took me FOREVER to get this working properly on this laptop, and I know I'm not the only linux user with this machine, so I will post a solution here. 

Note: This will not work if you have installed NVidia proprietary drivers.  For best results, do this from a clean install, and do not opt to install restricted add-ons, as this will install the proprietary drivers.  

This command will output the drain on your battery.  It should be around 20000

```
watch grep rate /proc/acpi/battery/BAT0/state
```

**Step 1: Install the latest graphics drivers**
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

**Step 2: Enable active state power management**
Open the grub config file 
```
sudo gedit /etc/default/grub
```
Find this line: 
```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash"
```
and insert **pcie_aspm=force** to the string, like so: 
```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash pcie_aspm=force”
```
Update grub to enact the changes 
```
sudo update-grub
```

**Step 3: Install and configure bumblebee**
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee
sudo apt-get install acpi-call-tools
```

Add yourself to the bumblebee user group: 
```
sudo usermod -a -G bumblebee YOURUSERNAME
```
Where USERNAME is your account user name

Open bumblebee.conf
```
sudo gedit /etc/bumblebee/bumblebee.conf[/CODE
Find these two lines and make sure they = Y
[CODE]STOP_SERVICE_ON_EXIT=Y

ENABLE_POWER_MANAGEMENT=Y
```

Open xorg.conf.nvidia 
```
sudo gedit /etc/bumblebee/xorg.conf.nvidia
```
and replace the contents with this 
```

Section "ServerLayout"
    Identifier "Layout0"
    Option "AutoAddDevices" "false"
EndSection

Section "Files"
    ModulePath "/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules"
EndSection

Section "Device"
    Identifier "Device1"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    BusID "01:00:0"
    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "ConnectedMonitor" "CRT"
EndSection

Section "Screen"
    Identifier    "Screen1"
    Device        "Device1"
EndSection
```

Create 'cardoff' file

```
sudo gedit /etc/bumblebee/cardoff
```

and insert this: 
```
\_SB.PCI0.PEG1.GFX0._OFF 
```

Create 'cardon' file 
```
sudo gedit /etc/bumblebee/cardon
```

and insert this: 
\_SB.PCI0.PEG1.GFX0._ON 

Reboot, and test. 

Your battery discharge should be <15, with low brightness, wifi off, and no usb devices, this number could be as low as 7000
```
watch grep rate /proc/acpi/battery/BAT0/state
```

if you need to run a program with the nvidia card, use optirun.  Test it with
```
optirun gedit
```

---

