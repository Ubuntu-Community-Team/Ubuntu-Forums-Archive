---
title: "Cannot switch from Intel to nVidia gfx card(nvidia-prime)"
date: 2015-07-20
forum: Hardware
---

### Post by PotatoHead007 on 2015-07-20
Hello.

I want to activate my nVidia gfx card when playing games, but it does not seem to work. Here is what happens when I try:
 [IMG]http://i.imgur.com/zMXXAGc.png[/IMG]
Any idea what the problem might be? Really desperate.

NOTE that as soon as I ckick "OK", it changes back to Intel.

[B]EDIT:

Fixed! Here's what I did:

[/B]```
sudo apt-get remove --purge nvidia*
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install nvidia-346
```

The problem I had with this was that I was greeted by a black screen upon login, but that can be fixed by installing a different driver version. I can switch to nVidia now, and I am happy!

---

### Post by PaulW2U on 2015-07-20
*Thread moved to **Hardware**.*

---

### Post by PotatoHead007 on 2015-07-20
Shameless bump :( This may also be due to software errors like conflicting packages, which is why I did not initially put it under Hardware.

---

### Post by Bashing-om on 2015-07-20
PotatoHead007; Hummm ...

Not much yet to work with .

What is the hardware :
```

lspci -vnn | grep VGA -A 12

```
A driver loaded ?
```

sudo lshw -C display
dpkg -l | grep -i nvidia

```
What does the system report :
```

cat /var/log/Xorg.0.log

```

With this info, we can begin to discuss this situation.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by efflandt on 2015-07-20
My laptop only lists the Intel graphics grep'g "VGA" from lspci. The lspci line for my GTX 765M contains "3D" instead of "VGA", and just shows "!!! unknown header type 7f" under that while using Intel graphics, so additional lines may not reveal any more. See if the following shows which nvidia chip you have:```
lspci | grep 3D
```And I usually use this to show which nvidia packages are installed, assuming that you used Ubuntu packages and not drivers directly from nvidia.com```
dpkg-query -l nvidia* | grep ii
```Are you sure that your laptop has nvidia graphics. I have seen some people trying to install nvidia drivers when they have only Intel graphics (which case nvidia drivers would not do anything for you).

---

### Post by PotatoHead007 on 2015-07-22
lspci -vnn | grep VGA -A 12 returns:
```

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c652]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at db000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c652]
    Flags: bus master, fast devsel, latency 0, IRQ 43
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119M [GeForce 610M] [10de:1058] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c652]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at da000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Memory at d8000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4105]

```


sudo lshw -C display
dpkg -l | grep -i nvidia gives:
```

*-display               
       description: VGA compatible controller
       product: GF119M [GeForce 610M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:da000000-daffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:3000(size=128)
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:db000000-db3fffff memory:c0000000-cfffffff ioport:4000(size=64)


```

Here's what matters in cat /var/log/Xorg.0.log
```

[    31.525] (WW) Falling back to old probe method for vesa
[    31.525] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    31.525] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    31.525] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32

```

---

### Post by PotatoHead007 on 2015-07-22
@[**[COLOR=#000000]efflandt[/COLOR]**]("http://ubuntuforums.org/member.php?u=937632") I am sure I have an nVidia card, as I have used it before.

---

### Post by Bashing-om on 2015-07-22
PotatoHead007; Hey :

I have yet to see a fault, all appears to be in order.
Maybe a driver conflict ?
What does :
```

dpkg -l | grep -i nvidia

```
reveal about the installed drivers ?

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2015-07-22
Can you disable the Intel adapter in the machine's BIOS?  If so, does that help?

---

### Post by PotatoHead007 on 2015-07-23
@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") I cannot disable it.

```

dpkg -l | grep -i nvidia
```
Returns:
```

ii  bbswitch-dkms                                         0.7-2ubuntu1                                             amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-304                                          304.125-0ubuntu0.0.1                                     amd64        NVIDIA CUDA runtime library
rc  libcuda1-331                                          331.113-0ubuntu0.0.4                                     amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                            304.125-0ubuntu0.0.1                                     amd64        NVIDIA legacy binary driver - version 304.125
rc  nvidia-331                                            331.113-0ubuntu0.0.4                                     amd64        NVIDIA binary driver - version 331.113
ii  nvidia-opencl-icd-304                                 304.125-0ubuntu0.0.1                                     amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331                                 331.113-0ubuntu0.0.4                                     amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                    amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                          amd64        Tool for configuring the NVIDIA graphics driver


```

Someone on reddit told me these drivers are ancient and I should update, thoughts?

---

### Post by Bashing-om on 2015-07-23
PotatoHead007; Hey ;

Now we know more. Your Nvidia card is identified as " GF119M [GeForce 610M]  " ; and, Nvidia recommends their latest driver for this card. That might be too cutting edge, I bet the 346 driver will perform better , As you have tried the 331, we may as well install the 346 version and see what results. That 346 driver for ubuntu release 14.04 must be obtained from outside sources.
In that case you may want to try nvidia-346 from xorg-edgers ppa. ( aside, these drivers are available for 15.04 in our software repository)
```

sudo apt-get remove --purge nvidia*
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install nvidia-346

```

Reboot to see the effect.

[INDENT][INDENT][INDENT]could be now
[INDENT][INDENT][INDENT]all is finer than a frog's hair
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by PotatoHead007 on 2015-07-23
```

sudo apt-get dist-upgrade
```
Does that not upgrade my OS? I want to keep 14.04.

---

### Post by SeijiSensei on 2015-07-23
While the phrase "dist-upgrade" might reasonably lead you to believe that it will upgrade you to the next version of Ubuntu, in fact, it only means that the kernel and its associated files will be updated.

---

### Post by PotatoHead007 on 2015-07-23
I see, thanks! I cannot do this now, but I will do it tomorrow and get back to you all :)

---

### Post by PotatoHead007 on 2015-08-03
**UPDATE: **Took longer than I thought, but it worked! All good now, thanks to everyone who helped.

---

### Post by Bashing-om on 2015-08-03
PotatoHead007; Great !

Pleased the situation is under control. What was the means that you employed ?

As this is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]rewards of good effort
[/INDENT][/INDENT]

---

