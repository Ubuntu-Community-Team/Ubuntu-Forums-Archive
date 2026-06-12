---
title: "Ubuntu Software Center not detecting second GPU"
date: 2024-01-21
forum: Hardware
---

### Post by kmagnum357 on 2024-01-21
[FONT=Liberation Mono][SIZE=2]Hi Everyone![/SIZE][/FONT]
 
 
 [FONT=Liberation Mono][SIZE=2]I’m Trying to follow these instructions to enable GPU passthru:[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2][https://askubuntu.com/questions/1406888/ubuntu-22-04-gpu-passthrough-qemu](https://askubuntu.com/questions/1406888/ubuntu-22-04-gpu-passthrough-qemu)[/SIZE][/FONT]
 
 
 [FONT=Liberation Mono][SIZE=2]But I’m having an issue on step 8: one of my two graphics cards doesn’t get recognized by software center.[/SIZE][/FONT]
 
 
 
 
 
 
 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=293319&stc=1[/IMG]  

 
 
 [FONT=Liberation Mono][SIZE=2]Unfortunately using the bash commands listed in step 8 to manually set my nouveau drivers seem to affect both graphics cards at once. This is a problem as it seems to make my 2060 no longer able to detect my monitor, as if I’m running both GPUs without drivers.[/SIZE][/FONT]

 
 
 ```
[FONT=Liberation Mono][SIZE=2]Lspci -nnk[/SIZE][/FONT]
```[FONT=Liberation Mono][SIZE=2] shows the following, so I know they’re both somewhat detected.[/SIZE][/FONT]

 
 
 ```
[FONT=Liberation Mono][SIZE=2]05:00.0 VGA compatible controller [0300]: NVIDIA Corporation GA104 [GeForce RTX 3060 Ti Lite Hash Rate] [10de:2489] (rev a1)[/SIZE][/FONT]

 [FONT=Liberation Mono][SIZE=2]    Subsystem: eVga.com. Corp. GA104 [GeForce RTX 3060 Ti Lite Hash Rate] [3842:4663][/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Kernel driver in use: nvidia[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]05:00.1 Audio device [0403]: NVIDIA Corporation GA104 High Definition Audio Controller [10de:228b] (rev a1)[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Subsystem: eVga.com. Corp. GA104 High Definition Audio Controller [3842:4663][/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Kernel modules: snd_hda_intel[/SIZE][/FONT]
 …
 
 
 [FONT=Liberation Mono][SIZE=2]0b:00.0 VGA compatible controller [0300]: NVIDIA Corporation TU106 [GeForce RTX 2060 Rev. A] [10de:1f08] (rev a1)[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Subsystem: Micro-Star International Co., Ltd. [MSI] TU106 [GeForce RTX 2060 Rev. A] [1462:3755][/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Kernel driver in use: nvidia[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]0b:00.1 Audio device [0403]: NVIDIA Corporation TU106 High Definition Audio Controller [10de:10f9] (rev a1)[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Subsystem: Micro-Star International Co., Ltd. [MSI] TU106 High Definition Audio Controller [1462:3755][/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Kernel modules: snd_hda_intel[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]0b:00.2 USB controller [0c03]: NVIDIA Corporation TU106 USB 3.1 Host Controller [10de:1ada] (rev a1)[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Subsystem: Micro-Star International Co., Ltd. [MSI] TU106 USB 3.1 Host Controller [1462:3755][/SIZE][/FONT]

 [FONT=Liberation Mono][SIZE=2]    Kernel driver in use: xhci_hcd[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Kernel modules: xhci_pci[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]0b:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C UCSI Controller [10de:1adb] (rev a1)[/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Subsystem: Micro-Star International Co., Ltd. [MSI] TU106 USB Type-C UCSI Controller [1462:3755][/SIZE][/FONT]
 [FONT=Liberation Mono][SIZE=2]    Kernel driver in use: nvidia-gpu[/SIZE][/FONT]

 [FONT=Liberation Mono][SIZE=2]    Kernel modules: i2c_nvidia_gpu[/SIZE][/FONT]


``` 
 
 
 
 [FONT=Liberation Mono][SIZE=2]Is this a common issue? I did attempt to google this before coming here, to no avail. Am I missing some command here? How can I make sure 1 GPU keeps its driver while I disable the driver of the other one?[/SIZE][/FONT]

 
 
 [FONT=Liberation Mono][SIZE=2]Thank you for your time! Cheers from Detroit![/SIZE][/FONT]

---

### Post by #&amp;thj^% on 2024-01-21
Will you also show us your grub file
```
tac /etc/default/grub
```

And you did see this right? 
> Attention! This guide is only relevant for Nouveau driver. Please read the text carefully before you start system changes.

---

### Post by kmagnum357 on 2024-01-23
```
#GRUB_INIT_TUNE="480 440 1"
# Uncomment to get a beep at grub start

#GRUB_DISABLE_RECOVERY="true"
# Uncomment to disable generation of recovery mode menu entries

#GRUB_DISABLE_LINUX_UUID=true
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux

#GRUB_GFXMODE=640x480
# you can see them in real GRUB with the command `vbeinfo'
# note that you can use only modes which your graphic card supports via VBE
# The resolution used on graphical terminal

#GRUB_TERMINAL=console
# Uncomment to disable graphical terminal

#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
# This works with Linux (no patch required) and with any kernel that obtains
# Uncomment to enable BadRAM filtering, modify to suit your needs

#GRUB_DISABLE_OS_PROBER=false
# filesystems to look for things.
# os-prober can cause damage to those guest OSes as it mounts
# for guest OSes installed via LVM or raw disk devices, running
# probably want to run os-prober. However, if your computer is a host
# If your computer has multiple operating systems installed, then you

GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on kvm.ignore_msrs=1"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_TIMEOUT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_DEFAULT=0

#   info -f grub -n 'Simple configuration'
# For full documentation of the options in this file, see:
# /boot/grub/grub.cfg.
# If you change this file, run 'update-grub' afterwards to update

```

as to the relevance of the guide, I am attempting to follow it to install the nouveau driver, that is where the problem is, I cant seem to install it on one of my GPUs, as it doesnt show up in software center. For some reason the Nvidia driver installs for both GPUs and works for them fine, but, as you say, it doesn't help me complete this process. Again, thank you for your time, and I hope the output above helps!

---

### Post by MAFoElffen on 2024-01-24
You are missing some steps there...

In your /etc/default/grub file, the GRUB_CMDLINE_DEFAULT_LINUX line, you are missing the vfio-pci.ids=<VendorID>:<ProductID>" parameter, where you exclude the GPU from the host... Then if you are missing that, then you probably do not have a vfio.conf file with something like this: 
```

# File /etc/modprobe.d/vfio.conf
# Pass Through the iGPU
# driver used
#
blacklist i915
# where it is located
#vfio-pci.ids=8086:a780
options vfio-pci ids=8086:a780

```
That example is for Intel GPU, but you can see it tell that the GPU stays unclaimed by the host, and blacklists the driver that would load as a default for it, to prevent it from loading...

Then you do this on the Host
```

sudo lspci -nnnk | grep -A3 -E 'Display|VGA|3D'

```
Ensure that the driver for the GPU is showing being used for that is the 'vfio' driver.

 Then you install your VM... And after the install, in the define, give the VM the passthrough XML to tell it to use that IOMMU device as a resource... This device at this bus:slot, etc, as a passthrough PCI device...

If you look in the Virtualization Section, search on my username and "vfio passthrough"... The details are there.

---

### Post by kmagnum357 on 2024-01-30
I followed your advice, adding the vfio-pci.ids to the GRUB_CMDLINE_DEFAULT_LINUX line, and updated my vfio.conf with the following:

```
blacklist nvidia
#blacklist nvidiafb
#blacklist nouveau
blacklist snd_hda_intel
options vfio-pci ids=10de:2489,10de:228b
```

the nvidiafb and nouveau lines remained commented out. I then rebuilt my initram to incorporate the vfio.conf changes, ran the grub update command, and rebooted.

After this, my computer was rendered unbootable, I couldn't even get to grub. I used a boot stick and ran boot-repair, then used the recovery menu to reinstall nvidia drivers, comment out the vfio.conf lines, and rebuild my initram. 

Your suggestion, while the correct advice for the standard gpu passthrough question, seems to have not had the intended effect here. My 2nd graphics card, the 2060, seems to have been affected by these changes, or cannot accept the Nouveau driver for some reason. i feel like I'm going crazy or something.

Any other suggestions? what is going on with this graphics card? why does it work just fine (im using it now) when I install the nvidia drivers to a DIFFERENT GPU, then fail catastrophically when I force a DIFFERENT GPU to use nouveau? quite frustrating. considering buying another GPU to see if that fixes things.

---

### Post by MAFoElffen on 2024-01-30
Unfortunately, most of the time you do pass-through have 2 GPU's "of different types" (using different drivers)... Yours are both NVidia, so when you blacklisted it for one, it blacklisted for both, so didn't load for the other GPU.

You need to use a different strategy. try using this guide:
[https://forum.level1techs.com/t/vfio-in-2019-pop-os-how-to-general-guide-though-draft/142287](https://forum.level1techs.com/t/vfio-in-2019-pop-os-how-to-general-guide-though-draft/142287)

---

### Post by kmagnum357 on 2024-02-02
This worked! I'm still working out kinks and trying to get looking glass and scream working properly but lspci showed the vfio driver provisioned, my windows VM sees the GPU when open up display manager. Thank you!!!

---

