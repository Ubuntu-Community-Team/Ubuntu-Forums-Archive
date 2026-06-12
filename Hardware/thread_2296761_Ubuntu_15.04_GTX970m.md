---
title: "Ubuntu 15.04 GTX970m"
date: 2015-09-28
forum: Hardware
---

### Post by cranerja on 2015-09-28
I recently purchased a msi GE72 2QF which has a GTX970m card. I installed the drivers properly but I am still facing a few issues:
1. chrome://gpu shows that there is no hardware acceleration, even with the override setting enabled. It shows as well when watching videos.
2. There is a lot of screen tearing during regular desktop use, specifically when moving windows.
3. (not vital) I read that there were ways to control the msi keyboard LEDs in Linux but the instructions do not work for me.
I installed the 352 drivers along with primus it is set to nvidia.
Thanks in advance!

---

### Post by Bashing-om on 2015-09-28
cranerja; Humm ...

What does :
> 
installed the drivers properly

mean ? Like, what method did you employ to install ? - from our software repository ?

And did you remove the old drivers prior to (RE-(installing ?
Do we now have a conflict in drivers ?
Post back the output of terminal command:
```

dpkg -l | grep -i nvidia

```

[INDENT][INDENT]we see where we go from here
[/INDENT][/INDENT]

---

### Post by cranerja on 2015-09-28
> **Bashing-om said:**
> cranerja; Humm ...

What does :

mean ? Like, what method did you employ to install ? - from our software repository ?

And did you remove the old drivers prior to (RE-(installing ?
Do we now have a conflict in drivers ?
Post back the output of terminal command:
```

dpkg -l | grep -i nvidia

```
[INDENT][INDENT]we see where we go from here
[/INDENT]
[/INDENT]

This is how I installed the drivers:
```
sudo add-apt-repository ppa;graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-352 nvidia-prime
```
And your request gave:
```
jacob@Aguila:~$ dpkg -l | grep -i nvidiaii  bbswitch-dkms                                        0.7-2ubuntu1                               amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-352                                         352.41-0ubuntu0~gpu15.04.1                 amd64        NVIDIA CUDA runtime library
ii  nvidia-352                                           352.41-0ubuntu0~gpu15.04.1                 amd64        NVIDIA binary driver - version 352.41
ii  nvidia-opencl-icd-352                                352.41-0ubuntu0~gpu15.04.1                 amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                         0.8.1                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                      355.11-0ubuntu0~gpu15.04.1                 amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by Bashing-om on 2015-09-28
cranerja; Yeah ...

Agreed, the install of the driver is all prim and proper, and there are no conflicts.
But is the 352 version the correct version ?
```

lspci -nnk | grep -iA3 vga

```
to allow me to match up the hardware to the driver.

[INDENT][INDENT]should workie;
[INDENT][INDENT][INDENT]no workie;
[INDENT][INDENT][INDENT][INDENT]how cum
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cranerja on 2015-09-28
> **Bashing-om said:**
> cranerja; Yeah ...

Agreed, the install of the driver is all prim and proper, and there are no conflicts.
But is the 352 version the correct version ?
```

lspci -nnk | grep -iA3 vga

```
to allow me to match up the hardware to the driver.[INDENT][INDENT]should workie;[INDENT][INDENT][INDENT]no workie;[INDENT][INDENT][INDENT][INDENT]how cum
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


The outcome:

```
jacob@Aguila:~$ lspci -nnk | grep -iA3 vga00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1612] (rev 0a)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1134]
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 0a)



```

It doesn't list the nvidia card here, even though it does in system information:
GeForce GTX 970M/PCIe/SSE2

---

### Post by Bashing-om on 2015-09-28
cranerja; Sheeeshhh ....

Looks like I am not asking the system the right question;
How about
```

lspci | grep "VGA\|3D"
sudo ubuntu-drivers devices

```

But " GeForce GTX 970M/PCIe/SSE2 " is the format and syntax I needed .
And I do confirm that for that card the 352 version is as Nvidia recommends.

That proprietary driver is available in our software repository .. Maybe ppa-purge " ppa:graphics-drivers/ppa " to revert the PPA driver to that of the repo ? Maybe ?

[INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cranerja on 2015-09-28
> **Bashing-om said:**
> cranerja; Sheeeshhh ....

Looks like I am not asking the system the right question;
How about
```

lspci | grep "VGA\|3D"
sudo ubuntu-drivers devices

```

But " GeForce GTX 970M/PCIe/SSE2 " is the format and syntax I needed .
And I do confirm that for that card the 352 version is as Nvidia recommends.

That proprietary driver is available in our software repository .. Maybe ppa-purge " ppa:graphics-drivers/ppa " to revert the PPA driver to that of the repo ? Maybe ?[INDENT][INDENT]sometimes[INDENT][INDENT][INDENT]I just do not know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Not bad, it now lists this:
```
jacob@Aguila:~$ lspci | grep "VGA\|3D"00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 0a)
01:00.0 3D controller: NVIDIA Corporation GM204M [GeForce GTX 970M] (rev a1)

```

And for the second line:
```
jacob@Aguila:~$ sudo ubuntu-drivers devices
[sudo] password for jacob: 
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free


== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : GM204M [GeForce GTX 970M]
modalias : pci:v000010DEd000013D8sv00001462sd00001134bc03sc02i00
vendor   : NVIDIA Corporation
driver   : nvidia-352 - third-party free
driver   : nvidia-346 - distro non-free
driver   : nvidia-346-updates - distro non-free
driver   : nvidia-355 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

```
Did the ppa-purge, no change.

---

### Post by Bashing-om on 2015-09-28
cranerja; Well .. Do not know rightly what to advise:
However:
> 
driver   : nvidia-355 - third-party free recommended


Try that 355 version.
Make sure that the PPA fetch in /etc/apt/sources.list.d is disabled;
purge the present driver:
```

sudo apt-get purge nvidia*

```
see if the system installs that system recommended driver:
```

sudo ubuntu-drivers autoinstall

```

Reboot to see the effect.

[INDENT][INDENT][INDENT]maybe yes 
[/INDENT][/INDENT][/INDENT]

---

### Post by cranerja on 2015-09-28
> **Bashing-om said:**
> cranerja; Well .. Do not know rightly what to advise:
However:


Try that 355 version.
Make sure that the PPA fetch in /etc/apt/sources.list.d is disabled;
purge the present driver:
```

sudo apt-get purge nvidia*

```
see if the system installs that system recommended driver:
```

sudo ubuntu-drivers autoinstall

```

Reboot to see the effect.
[INDENT][INDENT][INDENT]maybe yes 
[/INDENT]
[/INDENT]
[/INDENT]


The autoinstall gave me the 346, I will try this out then the 355, then report back.

---

### Post by cranerja on 2015-09-28
> **Bashing-om said:**
> cranerja; Well .. Do not know rightly what to advise:
However:


Try that 355 version.
Make sure that the PPA fetch in /etc/apt/sources.list.d is disabled;
purge the present driver:
```

sudo apt-get purge nvidia*

```
see if the system installs that system recommended driver:
```

sudo ubuntu-drivers autoinstall

```
[INDENT][INDENT][INDENT]Reboot to see the effect.maybe yes 
[/INDENT]
[/INDENT]
[/INDENT]


Still the same problem. I just tried on firefox and webgl would load but did not work well, unlike with chrome. Is there some other configuration that needs to take place?

---

### Post by Bashing-om on 2015-09-28
cranerja; Well ..

I have to wonder how much ram is installed ... greater then 2 Gigs ?  In bios, how much memory is allocated to graphics ?

[INDENT][INDENT]just grasping at straws
[/INDENT][/INDENT]

---

### Post by cranerja on 2015-09-29
> **Bashing-om said:**
> cranerja; Well ..

I have to wonder how much ram is installed ... greater then 2 Gigs ?  In bios, how much memory is allocated to graphics ?
[INDENT][INDENT]just grasping at straws
[/INDENT]
[/INDENT]


The machine has 16 Gigs and the card has 3 Gigs. The system itself is working fine, it is something in the driver. I wish I could just disable the intel GPU somehow.

---

### Post by cranerja on 2015-09-29
> **cranerja said:**
> The machine has 16 Gigs and the card has 3 Gigs. The system itself is working fine, it is something in the driver. I wish I could just disable the intel GPU somehow.

Maybe I need to use bumblebee in combination with primus?

---

### Post by Bashing-om on 2015-09-29
cranerja; Well.

For sure memory and memory management is not the issue.
And yes, some have had better results with BumbleBee. Be aware BumbleBee and Nvidia-prime will not co-exist. If you go with BumbleBee, nvidia-prime will have to be removed.

[INDENT][INDENT][INDENT]will not hurt to try
[INDENT][INDENT]can always be re-done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cranerja on 2015-09-29
> **Bashing-om said:**
> cranerja; Well.

For sure memory and memory management is not the issue.
And yes, some have had better results with BumbleBee. Be aware BumbleBee and Nvidia-prime will not co-exist. If you go with BumbleBee, nvidia-prime will have to be removed.
[INDENT][INDENT][INDENT]will not hurt to try[INDENT][INDENT]can always be re-done
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I have seen instructions that vary quite a bit, is there a guide that you would recommend for this case? I know what packages to install, but I understand that one must modify files as well.

---

### Post by Bashing-om on 2015-09-29
cranerja; Hey ;

I have very limited experience with BumbleBee but I do hold their effort in high regard.
maybe start here:
[https://wiki.debian.org/Bumblebee](https://wiki.debian.org/Bumblebee)
[http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-8-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-8-on.html)

So for BB just install bumblebee, nvidia-bumblebee, then remove nvidia-prime

Read the installation instructions as it may still be required to run:
```

sudo apt-get install --reinstall ubuntu-drivers-common
sudo usermod -a -G bumblebee $USER

```


When all is completed, reboot to see the effect.

[INDENT][INDENT]interesting little project [/INDENT][/INDENT]

---

### Post by cranerja on 2015-09-29
> **Bashing-om said:**
> cranerja; Hey ;

I have very limited experience with BumbleBee but I do hold their effort in high regard.
maybe start here:
[https://wiki.debian.org/Bumblebee](https://wiki.debian.org/Bumblebee)
[http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-8-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-8-on.html)

So for BB just install bumblebee, nvidia-bumblebee, then remove nvidia-prime

Read the installation instructions as it may still be required to run:
```

sudo apt-get install --reinstall ubuntu-drivers-common
sudo usermod -a -G bumblebee $USER

```


When all is completed, reboot to see the effect.
[INDENT][INDENT]interesting little project [/INDENT]
[/INDENT]

IT WORKS!
Thank you so much for all your help!
I had to go through and change many .conf files and reinstall one of the intel drivers but it works! I followed most of the instructions found here: [http://rajat-osgyan.blogspot.com/2015/03/how-to-install-bumblebee-on-ubuntu.html](http://rajat-osgyan.blogspot.com/2015/03/how-to-install-bumblebee-on-ubuntu.html)

---

### Post by Bashing-om on 2015-09-29
cranerja; Outstanding !


Glad ya got it fingered out. Appreciate that you provided the how-to that proved of value.
Note: the referenced link provides for 15.04 !

[INDENT][INDENT]our knowledge base expands
[/INDENT][/INDENT]

---

