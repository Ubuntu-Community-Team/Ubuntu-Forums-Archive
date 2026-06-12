---
title: "Install NVIDIA gtx 1060"
date: 2017-11-03
forum: Hardware
---

### Post by xavier12358 on 2017-11-03
Hello,

I  am desesperated this is the reason why I repost a messages of my problem. I have a Lenovo Y720 and I Can t properly install my NVIDIA gtx 1060.

The NVIDIA setting dont show me the property of my card.
Here is some informations. 

```
sudo nvidia-settings 

** (nvidia-settings:9274): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-hssM08DFHh: Connexion refusée

ERROR: An internal driver error occurred


ERROR: Error querying enabled displays on GPU 0 (Missing Extension).


ERROR: Error querying connected displays on GPU 0 (Missing Extension).

** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this driver at /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application profiles will continue to work, but values cannot be prepopulated
       or validated, and will not be listed in the help text. Please see the README for possible values and descriptions.
```


```
In lspci I have that:

Code:
01:00.0 VGA compatible controller: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Lenovo GP106M [GeForce GTX 1060]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 95000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 50000000 (64-bit, prefetchable) [size=256M]
    Memory at 60000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 5000 [size=128]
    [virtual] Expansion ROM at 96000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [420] Advanced Error Reporting
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_378_drm, nvidia_378

```

Can someone help me?

---

### Post by Autodave on 2017-11-03
Where did you get the driver for your card?

---

### Post by xavier12358 on 2017-11-03
I get it on Ubuntu. I use Additionnel driver to dowload it.

---

### Post by xavier12358 on 2017-11-04
Please I am stuck...

---

### Post by efflandt on 2017-11-05
You don't say which Ubuntu version you are running. Not sure when the GTX 1060 Mobile came on the market, but it is possible that you need a newer nvidia driver from graphics-drivers ppa:```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```For Ubuntu 16.04 or newer you can use "apt" instead of "apt-get". Then try nvidia-384 or nvidia-387.

I am running a desktop GTX 1060 fine with nvidia-381, but Ubuntu 16.10 which I need to change because it has reached end of support (16.04 is long term support version or 17.04 & 17.10 are shorter term versions).

---

