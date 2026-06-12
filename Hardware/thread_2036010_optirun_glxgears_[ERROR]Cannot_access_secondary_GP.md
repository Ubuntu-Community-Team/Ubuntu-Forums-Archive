---
title: "optirun glxgears: [ERROR]Cannot access secondary GPU"
date: 2012-07-31
forum: Hardware
---

### Post by Curvature_Tensor on 2012-07-31
_**Solution:**_
1. Uninstall bumblebee, bumble-nvidia, nvidia-current
2. Reinstall clean versions of the above packages
3. Create a skeleton xorg.conf file in /etc/X11/
[https://wiki.ubuntu.com/X/Config/](https://wiki.ubuntu.com/X/Config/)
4. Force ACPI on by editing /etc/default/grub and then running update-grub
```
GRUB_CMDLINE_LINUX="acpi=force"
```[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Hello,
[B]
+Description:[/B]
I have an NVIDIA Optimus setup that I am trying to manage with bumblebee.  The glxgears displays perfectly with the Intel graphics card prior to and after any installation of nvidia/bumblebee packages.  The optirun command does not seem to be able to find the NVIDIA GPU.  I am stumped about what is going wrong causing modprobe nvidia to fail.  I think there is a link that is pointing in the wrong direction somewhere, but I do not know where to look. 

I followed the bumblebee installation instructions given here:
[http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work)

Essentially the instructions were add the bumblebee repository and install bumblebee along with bumblebee-nvidia.

I am very stumped by how to proceed and would appreciate any suggestions.  Thank you.

**_WORKS:_** **$ glxgears**
**_BROKEN:_** **$ optirun glxgears**
```
[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[ERROR]Aborting because fallback start is disabled.
```**+System Info:**
Ubuntu 12.04
optirun (Bumblebee) 3.0.1
Dell 702X GeForce 500M

3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

**+Hardware Info: $ lspci -k**
```
VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Dell Device 0571
    Kernel driver in use: i915
    Kernel modules: i915

VGA compatible controller: NVIDIA Corporation Device 1246 (rev a1)
    Subsystem: Dell Device 0571
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb
```**+Module Info: $ modprobe nvidia**
```
FATAL: Module nvidia not found.
```**+Module Info: $ modprobe nvidia-current**
[B]+Log: /var/log/kern.log relevant output
[/B]```
NVRM: failed to register with the ACPI subsystem!
NVRM: failed to copy vbios to system memory.
NVRM: RmInitAdapter failed! (0x30:0xffffffff:858)
NVRM: rm_init_adapter(0) failed
NVRM: failed to unregister from the ACPI subsystem!
```[B]

+Log: /var/log/Xorg.8.log relevant output
[/B]```
[] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[] (EE) NVIDIA(0):     check your system's kernel log for additional error
[] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[] (EE) NVIDIA(0):     README for additional information.
[] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[] (EE) NVIDIA(0): Failing initialization of X screen 0
```[B]

+Log: /var/log/Xorg.0.log relevant output[/B]
```
[] (II) LoadModule: "nvidia"
[] (WW) Warning, couldn't open module nvidia
[] (II) UnloadModule: "nvidia"
[] (II) Unloading nvidia
[] (EE) Failed to load module "nvidia" (module does not exist, 0)
```**+Driver Info: jockey-text -l**
```
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_current_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
```**+Configuration File: /etc/bumblebee/bumblebee.conf modifications:**
```
Driver=
CHANGED TO
Driver=nvidia
```**+Library Info: ldd $(which optirun) output:**
```
linux-vdso.so.1 =>  (0x00007fff9a5ff000)
    libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f036c255000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f036c04d000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f036bc8f000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f036ba52000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f036b835000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f036c56b000)
```[B]+Library Info: ldd $(which glxgears) output:
[/B]```
linux-vdso.so.1 =>  (0x00007fffcd861000)
    libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007ffed3f2e000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007ffed3c34000)
    libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007ffed38ff000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007ffed3542000)
    libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007ffed331d000)
    libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007ffed310b000)
    libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007ffed2f08000)
    libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007ffed2d02000)
    libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007ffed2aff000)
    libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007ffed28e8000)
    libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007ffed26ca000)
    libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007ffed24c4000)
    libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007ffed22b9000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007ffed209c000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007ffed1e97000)
    /lib64/ld-linux-x86-64.so.2 (0x00007ffed41af000)
    libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007ffed1c94000)
    libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007ffed1a8d000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007ffed1885000)

```**+Attempted Solution:**
1. Added to /etc/modprobe.d/blacklist.conf:
```
blacklist nvidia-current
blacklist nvidia

```based on this suggestion:
[https://lists.launchpad.net/bumblebee/msg00093.html](https://lists.launchpad.net/bumblebee/msg00093.html)

2. Additionally I tried installing the package nvidia-common.

3. Since modprobe finds nvidia-current, tried to change /etc/bumblebee/bumblebee.conf:
```
MODULE=nvidia
CHANGED TO
MODULE=nvidia-current
```however the /var/log/Xorg.8.log still says:
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
(EE) NVIDIA(0):     check your system's kernel log for additional error
(EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) NVIDIA(0):     README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0): Failing initialization of X screen 0
```[B]+Additional Information:
[/B]I do not have a xorg.conf file.   I do not want to generate one with nvidia-xconfig since my experience agrees with this post:
> nvidia-xconfig is going to break your desktop.[http://askubuntu.com/questions/136079/nvidia-graphics-resolution-problem](http://askubuntu.com/questions/136079/nvidia-graphics-resolution-problem)


Thank you once again

---

### Post by typhoon_tip on 2012-08-01
You have to blacklist nouveau, not nvidia-current. Try again without touching anything else, to blacklist nouveau first. This is NOT correct:

VGA compatible controller: NVIDIA Corporation Device 1246 (rev a1)
    Subsystem: Dell Device 0571
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, **[COLOR="Red"]nouveau[/COLOR]**, **[COLOR="red"]nvidiafb[/COLOR]**

The red ones above should not be there, they interfere with nvidia official driver.

---

### Post by Curvature_Tensor on 2012-08-01
Thank you so much for reading through that long post.

1.   I have had nouveau blacklisted for every attempted solution.  I should have mentioned that.
[B]
/etc/modeprobe.d/blacklist.conf[/B]:[B] blacklist nouveau
$ modprobe nouveau [/B]
```
FATAL: Module off not found.
```

2. Perhaps my problem is display related?
If I run with /etc/bumblebee/bumblee.conf given by:
```
KernelDriver=nvidia-current
Module=nvidia-current
```

Yields:
**+/var/log/Xorg.8.log: relevant output**
```
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
 (**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "UseEDID" "true"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Enabling 2D acceleration
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
(EE) NVIDIA(0):     check your system's kernel log for additional error
(EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
 (EE) NVIDIA(0):     README for additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0): Failing initialization of X screen 0
(II) UnloadModule: "nvidia"
(II) Unloading nvidia
(II) UnloadModule: "wfb"
(II) Unloading wfb
(II) UnloadModule: "fb"
 (II) Unloading fb
(EE) Screen(s) found, but none have a usable configuration.
```

---

### Post by Curvature_Tensor on 2012-08-03
bump.

Any ideas?

---

### Post by Curvature_Tensor on 2012-08-04
I solved the problem, but am confused as to why forcing ACPI to be on was necessary.  Does anyone care to educate me?

---

### Post by typhoon_tip on 2012-08-07
> **Curvature_Tensor said:**
> I solved the problem, but am confused as to why forcing ACPI to be on was necessary.  Does anyone care to educate me?

You mean removing the force has solved the problem ?

---

### Post by landersohn on 2012-09-10
Curvature_Tensor,
can you share how you solved the problem? Marking a thread a SOLVED without posting the solution is a bit frustrating for folks who are having the same problem

---

### Post by Curvature_Tensor on 2012-09-27
> **landersohn said:**
> Curvature_Tensor,
can you share how you solved the problem? Marking a thread a SOLVED without posting the solution is a bit frustrating for folks who are having the same problem

It is in the original post.  I updated it after solving the problem.

I had to force ACPI on to solve the problem.

---

### Post by JoeGoalie on 2012-11-27
I have a Toshiba M645-S4080.  If I change the /etc/defaults/grub to include ```
GRUB_CMDLINE_LINUX="acpi=force"
```
It will not boot.  It just goes to a black screen with a blinking cursor that allows me to type but not actually do anything.  Besides creating the xorg.conf, was there something I was supposed to add to it beyond that example skeleton?  Thanks

Edit: Scratch that.  I changed the xorg.conf permissions to 777 and now it boots.  Maybe I just needed to make it executable?  ```
optirun glxgears
```
Still doesn't work though.  It returns: ```
joseph@M645:~$ optirun glxspheres
[   24.780377] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) No devices detected.

[   24.780419] [ERROR]Aborting because fallback start is disabled.
```
Any ideas?

---

### Post by Kamigor on 2012-12-10
[FONT=Courier 10 Pitch][SIZE=2]Hello everyone!
[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Have the same problem and I've done how it is shown in the solution but it has not still work!

Laptop: Lenovo Y570 (CPU [/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=2][FONT=Courier 10 Pitch][SIZE=2]Core i5-2450M [/SIZE][/FONT]with [/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2]Sandybridge Mobile x86/MMX/SSE2[/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT] and NVidia GeForce GT555M).
System: Ubuntu 12.04.1 LTS 32bit.

After installing Ubuntu and exactly after that I ran these commands to install nvidia driver and bumbbelle ([http://help.ubuntu.ru/wiki/bumblebee](http://help.ubuntu.ru/wiki/bumblebee)):[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]sudo add-apt-repository ppa:bumblebee/stable[/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=2]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]
sudo apt-get update[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]udo apt-get install bumblebee bumblebee-nvidia nvidia-current[/SIZE][/FONT] 
[FONT=Courier 10 Pitch][SIZE=2]restart[/SIZE][/FONT]  [FONT=Courier 10 Pitch][SIZE=2]

Then[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]
sudo apt-get install mesa-utils[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]
optirun --status[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]
Bumblebee status:  Ready (3.0.1). X inactive. Discrete video card is likely on.[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]optirun glxgears[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2][ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]

I tried [/SIZE][SIZE=2]_**Solution:**_[/SIZE][SIZE=2]
1. Uninstall bumblebee, bumble-nvidia, nvidia-current
2. Reinstall clean versions of the above packages
3. Create a skeleton xorg.conf file in /etc/X11/
4. Force ACPI on by editing /etc/default/grub and then running update-grub[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]
but it did not help. What did I do wrong? I cannot see Grafics in Details (System settings).[/SIZE][/FONT] [FONT=Courier 10 Pitch][SIZE=2]

Sometimes I cannot see [SIZE=2]the list of [SIZE=2]drivers in System Settings[SIZE=2] > Additional Drivers[SIZE=2] but in [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2]Details [SIZE=2]I can see Intel® Sandybridge Mobile x86/MMX/SSE2[SIZE=2]. And when I cannot see this [/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2]Sandybridge... in details I can see [SIZE=2]the names of the drivers in [/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][FONT=Courier 10 Pitch][SIZE=2][SIZE=2][SIZE=2][SIZE=2]Additional Drivers.[/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]

Thank you in advance for your answers.

---

### Post by landersohn on 2012-12-10
I think when I worked on this, the key things I did where
1)  sudo tee /proc/acpi/bbswitch <<<ON

I think the outo on/off didn't work with my laptop
And I added 
2) acpi=force 
to /etc/default/grub as boot parameter (like several posters commented on also)

Key was also not to install the regular nvidia driver, only bumblebee and bumlebee-nvidia

---

### Post by Kamigor on 2012-12-10
Thank you  **[landersohn]("http://ubuntuforums.org/member.php?u=725498")** but I have found the solution already. 

The problem was that I am the LUCKY owner of Lenovo IdeaPad Y570. So for this model (and for Y470 too!!!) there is the bug but doing code below you can force to work your video card until new core will announce: 

sudo su
sudo apt-get install git
git clone git://github.com/Bumblebee-Project/bbswitch.git -b hack-lenovo
cd bbswitch
mkdir /usr/src/acpi-handle-hack-0.0.1
cp Makefile acpi-handle-hack.c /usr/src/acpi-handle-hack-0.0.1
cp dkms/acpi-handle-hack.conf /usr/src/acpi-handle-hack-0.0.1/dkms.conf
dkms add acpi-handle-hack/0.0.1
dkms build acpi-handle-hack/0.0.1
dkms install acpi-handle-hack/0.0.1
echo acpi-handle-hack | sudo tee -a /etc/modules
sudo update-initramfs -u

Thanks to **Nikki1993** ( [http://forum.ubuntu.ru/index.php?topic=190100.0](http://forum.ubuntu.ru/index.php?topic=190100.0) ) and **FKGreen** ( [https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo](https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo) ) 
In my case this helped. I can not see the name of my video card in Drivers and details but optirun glxgears works.

---

### Post by olof_ on 2012-12-23
solution in first post works just perfect! 
A tiny note is that there is a typo on stage 1: "Uninstall bumblebee, bumble-nvidia, nvidia-current" should be

bumble->bee<--nvidia

thanks alot.
Merry christmas everyone!

---

### Post by Meowcate on 2013-02-14
Hello,

I just bought a new laptop and so discover the Optimus. I just installed a fresh 12.10 next to the Win8.
I don't use much configs, so I'll share informations based on what Curvature_Tensor said.

I don't have additionnals drivers in sources and Details gives me about my graphic card
```
Driver unknown
Experience standard
```(since it's in french, it can be a little different)

About my system :
[B]Ubuntu 12.10 64b
Linux 3.5.0-17-generic
Gnome 3.6.0
Asus R700V Series
Intel Core i7-3630QM
nvidia Geforce GT 635M[/B]

I tried the solution by uninstall, then install, add a skeleton xorg.conf and force APCI, but when I try **optirun glxgears** I still get :
```
[771.030846] [ERROR]Cannot access secondary GPU - error : Could not load GPU driver
[771.031008] [ERROR]Aborting because fallback start is disabled
```[B]
lspci -k[/B]
```
VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
Subsystem:  ASUSTeK Computer Inc. Device 10bc
Kernel driver in use: i915
Kernel modules: i915

VGA compatible controller: NVIDIA  Corporation Device 0de3 (rev a1)
Subsystem: ASUSTeK Computer Inc.  Device 10bc
Kernel modules: nouveau, nvidiafb
```**modprobe** doesn't found nvidia nor nvidia_current

**jockey-text -l**
```
kmod:nvidia_experimental_310 - Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_current - NVIDIA binary Xorg driver, kernel module and VDPAU library (Free, Disabled, Not in use)

kmod:nvidia_current_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
```By the way, I don't have nvidia-xconfig.
As suggested, I blacklisted nouveau and nvidiafb in bumblee.conf but lspci still get it.

**dkms status**
```
bbswitch, 0.4.2, 3.5.0-23-generic, x86_64: installed
nvidia-current, 304.64: added
```

I don't know what I can do. Even after reinstall nvidia_current, it's like it's not in use. Does someone have an idea ?

---

### Post by landersohn on 2013-02-14
I had to blacklist the nvidia and nvidia-current drivers.
I uninstalled everything nvidia related (nvdidia- current amongst others) and installed bumblebee and bumblebee-nvidia clean.
I could not use the standard nvdidia driver!

I also added acpi=force to the boot parameters in grub, although I am not sure that is needed.

To get the around the power savings problem, i ran

sudo tee /proc/acpi/bbswitch <<<ON

This command turns the card on
If you try to load an nvidia driver (either regular nvidia or bumblebee-nvidia) with the card powered down, you'll get your error.


Good luck

---

### Post by diannaochong on 2013-02-15
nevermind, dont know what I did, but it works all of a sudden.

---

### Post by [::AP::] on 2013-03-28
> **Kamigor said:**
> Thank you  **[landersohn]("http://ubuntuforums.org/member.php?u=725498")** but I have found the solution already. 

The problem was that I am the LUCKY owner of Lenovo IdeaPad Y570. So for this model (and for Y470 too!!!) there is the bug but doing code below you can force to work your video card until new core will announce: 

sudo su
sudo apt-get install git
git clone git://github.com/Bumblebee-Project/bbswitch.git -b hack-lenovo
cd bbswitch
mkdir /usr/src/acpi-handle-hack-0.0.1
cp Makefile acpi-handle-hack.c /usr/src/acpi-handle-hack-0.0.1
cp dkms/acpi-handle-hack.conf /usr/src/acpi-handle-hack-0.0.1/dkms.conf
dkms add acpi-handle-hack/0.0.1
dkms build acpi-handle-hack/0.0.1
dkms install acpi-handle-hack/0.0.1
echo acpi-handle-hack | sudo tee -a /etc/modules
sudo update-initramfs -u

Thanks to **Nikki1993** ( [http://forum.ubuntu.ru/index.php?topic=190100.0](http://forum.ubuntu.ru/index.php?topic=190100.0) ) and **FKGreen** ( [https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo](https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo) ) 
In my case this helped. I can not see the name of my video card in Drivers and details but optirun glxgears works.


@Kamigor - 

Glad to hear that this worked out for you. I have a Y470 running a recent install of Xubuntu.
Do I still need to use the "Solution" in the original post before your posted method, or can I just jump to your Lenovo Y470/570 hack?

Thanks.

---

