---
title: "Networking issues in Lucid Lynx, Intel 3945ABG"
date: 2010-05-30
forum: Hardware
---

### Post by dumtratt on 2010-05-30
The basic info:

**Computer:**
Acer Aspire 9802WKMi (Acer Aspire 9800)

**Network interface:**
```
hans@hans-laptop:~$ lspci | grep -i 'wireless'
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev ff
```

**My iwconfig shows:**
```
hans@hans-laptop:~$ iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.

bnep0     no wireless extensions
```

**Modules:**
```
hans@hans-laptop:~$ lsmod | grep 'iwl'
iwl3945                70584  0 
iwlcore               111317  1 iwl3945
mac80211              209830  2 iwl3945,iwlcore
cfg80211              130735  3 iwl3945,iwlcore,mac80211
compat_firmware_class     7043  1 iwl3945
```

**Module info:**

```
hans@hans-laptop:~$ modinfo iwl3945
filename:       /lib/modules/2.6.32-22-generic-pae/updates/cw/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        2.6.32-22-generic-pae-ks
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     5AF1778CBF896C4F6C4E149
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlcore,compat_firmware_class,cfg80211,mac80211
vermagic:       2.6.32-22-generic-pae SMP mod_unload modversions 586TSC 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software])
 (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           fw_restart3945:restart firmware in case of error (int
```

**On boot:**

```
hans@hans-laptop:~$ dmesg | grep 'iwl'
[   23.883658] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 2.6.32-22-generic-pae-ks
[   23.883663] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   23.883782] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   23.883798] iwl3945 0000:07:00.0: setting latency timer to 64
[   24.056288] iwl3945 0000:07:00.0: Error: saturation power is -1, less than minimum expected 40
[   24.056293] iwl3945 0000:07:00.0: Invalid power index
[   24.056376] iwl3945 0000:07:00.0: initializing driver failed
[   24.056471] iwl3945 0000:07:00.0: PCI INT A disabled
[   24.056486] iwl3945: probe of 0000:07:00.0 failed with error -5
```

**Network:**

```
hans@hans-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       physical id: 2
       logical name: bnep0
       serial: 00:16:ce:f0:77:a5
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.2.2 multicast=yes
```

**Ubuntu version:**
```

hans@hans-laptop:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS
```

**Kernel version:**

```
hans@hans-laptop:~$ uname -mr
2.6.32-22-generic-pae i686
```

I've been reading threads and posts on everything, tried every fix, every little trick, tried re-installing. I have internet through a bluetooth connection with my macbook pro sharing the internet to the router. 

I have an ethernet cable hooked up to the computer. 

I have backports installed (linux-backports-modules-wireless-2.6.32-22-generic, linux-backports-modules-wireless-2.6.32-22-generic-pae)

I get no connection. Now I can't even see the device in iwconfig or ifconfig -a. Doesn't even show in lshw -C network, as you can see. 

What to do?

---

### Post by dumtratt on 2010-06-01
Bömp

---

### Post by apos on 2010-06-13
Try this:

```
echo 'options iwl3945 disable_hw_scan=1' | sudo tee /etc/modprobe.d/options-iwl3945.conf
```

Then ether reboot the computer or do:

```
sudo rmmod iwl3945 && sudo modprobe iwl3945
```

Greets Axel

---

### Post by Martin Marshalek on 2010-06-13
I had a very similar problem to this a few weeks ago, only it wasn't exactly with bluetooth, just wireless in general. Try what I describe in this thread: [http://ubuntuforums.org/showthread.php?t=1496078]("http://ubuntuforums.org/showthread.php?t=1496078"). If that works for you after a reboot then your good that way. Also, if that works are you running 32 bit or 64 bit? It makes a difference.

---

