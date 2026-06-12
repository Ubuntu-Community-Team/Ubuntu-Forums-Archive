---
title: "Black screen nvidia driver 320m"
date: 2016-01-01
forum: Hardware
---

### Post by dellboy56 on 2016-01-01
Hey guys im practically a novice when it comes to ubuntu but just a few miniutes ago when i was clicking on additional drivers tab i clicked on some nvidia drivers inthere i applied changes to install and they prompted the software manager to update which i said yes i then reboot into onenof the drivers and it has a black screen this is very common and has had me bugging me since switching to ubuntu on this mac i need help so if you can please provide me help through here or on the irc but not throguh #ubuntu as i am banned

---

### Post by Bashing-om on 2016-01-02
dellboy56; Well ....

The question is ... what driver(s) are presently installed ( a conflict ?) ?
And what driver is loaded ?
Post back  - Between code tags - the output of terminal commands:
( at the login screen key combo ctl_alt+F1 )
```

lspci -vnn | grep -i VGA
dpkg -l | grep -i nvidia
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

we see where we go
[INDENT][INDENT][INDENT]from here[/INDENT][/INDENT][/INDENT]

---

### Post by dellboy56 on 2016-01-02
i typed these commands in the terminal i couldnt find the code tag that you wanted me to link the stuff into anyways heres the first one that was read out on the vga 
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation MCP89 [GeForce 320M] [10de:08a0] (rev a2) (prog-if 00 [VGA controller])

```
grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                          304.131-0ubuntu0.14.04.1                            amd64        NVIDIA CUDA runtime library
rc  libcuda1-304-updates                                  304.131-0ubuntu0.14.04.1                            amd64        NVIDIA CUDA runtime library
ii  libcuda1-340                                          340.96-0ubuntu0.14.04.1                             amd64        NVIDIA CUDA runtime library
rc  libcuda1-340-updates                                  340.96-0ubuntu0.14.04.1                             amd64        NVIDIA CUDA runtime library
rc  nvidia-340                                            340.96-0ubuntu0.14.04.1                             amd64        NVIDIA binary driver - version 340.96
ii  nvidia-opencl-icd-340                                 340.96-0ubuntu0.14.04.1                             amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
```


```
*-display               
       description: VGA compatible controller
       product: MCP89 [GeForce 320M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:26 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:1000(size=128) memory:d3000000-d301ffff
```

---

### Post by papibe on 2016-01-02
Hi dellboy56.

According to the nvidia-340 package's docs, your card is supported:
```
$ zcat /usr/share/doc/nvidia-340/README.txt.gz | grep -i 08a0
    GeForce 320M                          0x08A0           C
```
It looks like the driver is not installed (status rc). Try to do it manually on the terminal:
```
sudo apt-get update

sudo apt-get install nvidia-340 nvidia-340-uvm

sudo nvidia-xconfig 
```
Then restart your machine.

If you get a black screen, remember that you can get a text login by pressing Ctrl+Alt+F1. To disable the driver:
```
sudo rm /etc/X11/xorg.conf
```
and this to reboot:
```
sudo reboot
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by matt_symes on 2016-01-02
Hi papibe

> **papibe said:**
> ```
$ zcat /usr/share/doc/nvidia-340/README.txt.gz | grep -i 08a0
    GeForce 320M                          0x08A0           C
```


If you have not come across it before, you may find *zgrep* useful in these situations.

I came across it the other day. I hope it helps.

Kind regards

---

### Post by papibe on 2016-01-02
> **matt_symes said:**
> If you have not come across it before, you may find *zgrep* useful in these situations.
groovy! :D

---

### Post by dellboy56 on 2016-01-02
Ok thanks guys will look into it

---

### Post by dellboy56 on 2016-01-02
Doesnt work

---

### Post by Bashing-om on 2016-01-03
dellboy56; Hey ....

Well:
> 
Doesnt work

Does not give us much to work with.

So; what did you do, what did you expect to happen, and what actually did happen ?

A tale is told in the log files.

Might be good to look at the current situation:
post back :
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

