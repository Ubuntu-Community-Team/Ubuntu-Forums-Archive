---
title: "Graphics Drivers - NVIDIA GTX 780m Alienware 17"
date: 2014-06-26
forum: Hardware
---

### Post by Morfir on 2014-06-26
Hi all,


I just picked up an Alienware 17 with a NVIDIA GTX 780m, and I am trying to get proprietary graphics installed and working on it in 14.04. I believe it is a problem with the proprietary drivers and acpi on my machine. Here is what I have tried so far, and all help is appreciated.


Background info:


The system has two disks, one ssd with a ubuntu installation using LVM for full disk encryption (full partition table available if becomes relevant), and one 1tb drive with a windows partition. Grub recognizes and can boot both os's.


```

# **lspci**
01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 780M] (rev a1)

```


```

# **apt-get install nvidia-current**
The following extra packages will be installed:
  nvidia-304 nvidia-libopencl1-304 nvidia-opencl-icd-304 nvidia-settings
The following NEW packages will be installed:
  nvidia-304 nvidia-current nvidia-libopencl1-304 nvidia-opencl-icd-304
  nvidia-settings

```


I have also tried using the nvidia-current-updates as well. I have also tried using the nvidia proper run script available on the nvidia drivers site.


In my attempts of installing the proprietary drivers from both the repos and from direct download, the installations have either written their own blacklist files in /etc/modprobe.d/ to disable the nouveau kernel module, or I have written a one when one was not present.


```

# **cat /etc/modprobe.d/blacklist-nouveau.conf**
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current_updates
alias nouveau off
alias lbm-nouveau off
```


In terms of kernel parameters, I have tried a number of different combinations, each time editing /etc/default/grub or the grub line manually upon boot. I have tried many combinations of flags such as modeset=0, nomodeset, acpi=off, all with limited success.


Each time I have made changes to the kernel parameters, I have run both of the following:
```

# **update-initfs -u**
# **update-grub**

```


These all have given me different results, but the most common point of failure is upon startup where the x-session hangs while starting the acpi daemon. This is where I believe my problem is. Assuming any way I install the proprietary drivers is equal, the only difference between boots are the kernel parameters I pass by default. Passing modeset=0 yields the following dmesg warnings:


```

# **dmesg**
[   18.529644] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   18.529651] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.529655] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[   18.529658] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[   18.529661] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 3 (20131115/utaddress-251)
[   18.529664] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.529665] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[   18.529668] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[   18.529671] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \IO_D 3 (20131115/utaddress-251)
[   18.529674] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 4 (20131115/utaddress-251)
[   18.529677] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.529678] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   18.530365] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[   18.530423] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input12

```


Messages after it pertaining to the drivers are as follow:


```

# **dmesg | grep -i nvidia**
[   18.580134] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[   18.580491] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 1
[   18.580497] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.79  Sun May 18 03:55:59 PDT 2014
[   39.103964] init: nvidia-prime main process (1386) terminated with status 127

```


At this point, I began to experiment with disabling acpi with the acpi=off kernel param, but this would yield a completely unusable user interface.


By setting nomodeset, I blackscreen myself. Nearly every change in kernel params causes a change in resolution, blackscreen, completely unusable interface, or access to a tty.


I am currently posting this using the nouveau drivers, but I'd really like to not be using them. Any help is appreciated, and thank you for your time.


Morfir

---

### Post by erodrigue82 on 2014-07-23
I'm having the same problem... you managed to resolve it?

---

### Post by Marc_de_Banville on 2014-10-12
I have my 780M up and running with ubuntu 14.04 on my ASUS ROG 750JH. What I do for now is the following :

1. Go to NVIDIA and download the driver for linux 64 to some easy location 
2. Reboot in recovery mode
3. At the recovery screen run as root
4. mount -o remount,rw /
5. navigate to the driver place and run it ./NVIDIAxxx.run. Build everything (yes to all), config Xfiles yes
6. reboot now

Strangely, to get the card working I have to reboot in recovery mode, and just hit resume at the recovery screen. It works so far even tho I agree this is not a satisfactory behaviour.

Hoping it helped.

Marc

---

