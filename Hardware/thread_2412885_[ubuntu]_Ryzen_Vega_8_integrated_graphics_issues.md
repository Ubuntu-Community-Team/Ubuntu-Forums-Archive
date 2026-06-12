---
title: "[ubuntu] Ryzen Vega 8 integrated graphics issues"
date: 2019-02-18
forum: Hardware
---

### Post by gipsyshadow on 2019-02-18
I've just built a PC with this cgf:
- amd ryzen 2200g with Vega 8 integrated graphics;
- msi b450-a pro and upgraded bios to its last release;
- 2x4gb hyperx predator @3200 cl16 (I let them work @2400 by default)
- hdd @7200rpm
- no dedicated graph card

I've just installed ubuntu 18.04.1LTS with these extra parameters to carry the installation on:
vga=791 nomodeset
because a lot of time ago I used them to manage Lubuntu installation on a very old laptop. In both cases I got black screen putting no parameter.

I updated ubuntu to 18.04.2lts but there were something wrong with graphics; some examples:
- FF is very slow to render its pages' contents and freezes continuosly if I use the scroll bar, idem if I try to move its windows around the desktop;
- if I select a tool on the left bar of the monitor it's all very slow and contents shown are messed/mixed up when I try to switch between one tab and the other ones and moving windows is a problem too
- some windows "go out" of the vertical desktop borders (upper and lower ones) so I tried to high monitor resolution to get everything smaller but the only available resolution is 1024x768 (4:3) while my monitor max res is 1440x900 (4:2.5);
- when I try to move file manager window around the desktop it leaves gray colour "traces"!

I've already tried to upgrade the kernel by ukuu starting from 4.15.0-45-generic. I first tried with the latest stable listed which is 4.20.8 but I got black screen then I tried with the previous others and got black screen too until 4.19.0-041900 which I left for now but there're no graph differences with 4.15.0-45. When the system starts up I can read an error displayed, kind of "error vgacon" something, if it could be important.
This is my cat /var/log/gpu-manager.log output if it could be useful

```

$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.19.0-041900-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.19.0-041900-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 1002:15dd
BusID "PCI:56@0:0:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:38:00.0/driver
The device is not bound to any driver.
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 1
Has amd? yes
Has intel? no
Has nvidia? no
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

I'm very newbie so I ask you to please tell me what to do step-by-step :D

---

### Post by Bashing-om on 2019-02-18
gipsyshadow; Hello

Looks like the system sees no driver available. Humm ....

Let's see what the system is aware of. Post back - Between code tags - the out puts of terminal commands:
```

sudo lshw -C display
lspci -k|grep -iEA5 'vga|3d'
lsmod | grep radeon
lsmod | grep amdgpu

```

Mind you, I am not the hippest on AMD graphics - but this will give us a starting place.to find out why the driver fails.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by gipsyshadow on 2019-02-18
Hi Bashing-om,
Nevermind, it's not the time to be hippy for something... if I've understood the meaning/mood :)

I've got outputs for the first 2 inputs but not for the last 2 ones, anyway here we start:
```

$ sudo lshw -C display
[sudo] password ....: 
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:38:00.0
       version: c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fe600000-fe67ffff
$ lspci -k|grep -iEA5 'vga|3d'
15:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43d5 (rev 01)
    Subsystem: ASMedia Technology Inc. Device 1142
    Kernel driver in use: xhci_hcd
15:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43c8 (rev 01)
    Subsystem: ASMedia Technology Inc. Device 1062
    Kernel driver in use: ahci
--
38:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Vega [Radeon Vega 8 Mobile] (rev c8)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Vega [Radeon Vega 8 Mobile]
    Kernel modules: amdgpu
38:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
    Kernel driver in use: snd_hda_intel
$ lsmod | grep radeon
$ lsmod | grep amdgpu

```

By the way I've found that erroe message at start and end of the session and it is: "error vgacon disables amdgpu kernel modesetting", hope this help.

Maybe I'll be awful wrong but I'd like to ask if something could be better with the graphic if I install another DE, such as Kubuntu.

Thanks for help :)

---

### Post by Bashing-om on 2019-02-18
gipsyshadow; Well - well --- Not

OK, we know that a driver is not loaded.
checking verifies that Vega support was added in the 4.12 kernel series, so now in 4.15 drivers should be available. This is AMD and generally drivers are included in the kernel.

So now I am looking to see how we can install from our repo the required driver. Mind ya, I am real rusty with AMD drivers and a lot has changed since last I had AMD experience. Will take me a bit to make sure of what we are going to do. In the meantime. others here may jump in that do have the knowledge/experience. I do not want to keep you with out an update on what our status is.

[INDENT]inquiring minds want to know
[/INDENT]

---

### Post by mc4man on 2019-02-18
I know nothing concerning AMD but 2 questions about things that struck me,

"I've just installed ubuntu 18.04.1LTS with these extra parameters to carry the installation on:
vga=791 nomodeset"
Are you still using those parameters, if so did you try without? This will show
cat /proc/cmdline


"I've just installed ubuntu 18.04.1LTS ....  I updated ubuntu to 18.04.2lts  but there were something wrong with graphics"
Was there any  graphic issues before 'updating' and what do you mean by updating?, i.e just normal updates or did you upgrade to the HWE stack. (xserver, kernel

---

### Post by Bashing-om on 2019-02-18
gipsyshadow; Hey -

Your attention is directed to the esteemed mc4man's last.
In addition we want to know if the drivers are available on your system now.
what shows:
```

dpkg -l xserver-xorg-video-amdgpu
dpkg -l xserver-xorg-video-ati

```

where I do anticipate that we use the amdgpu driver.

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by gipsyshadow on 2019-02-18
My always-answer every time I did something wrong about ubuntu is I'm a newbie :)

That was my cat /proc/cmdline
```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.19.0-041900-generic root=UUID=c9355173-be6d-4e48-a6f6-a2798e225cbf ro nomodeset quiet splash vt.handoff=1

```
so there was no more the vga parameter though the nomodeset one remained. I searched a bit and understood how to modify it permanently:
```

sudo gedit /etc/default/grub

```
and saw the line
```

GRUB_CMDLINE_LINUX="nomodeset"

```
was present so I just turned it into
```

GRUB_CMDLINE_LINUX=""
```
closed the editor and then
```

sudo update-grub

```
and now the graphics seem good though I've no previous expericences with ubuntu, at least all those issues described above disappeared.
I've tried to update the kernel to 4.20.10 by ukuu and everything seems alright for now about graphics.
In other words I myself created my graph issues adding those parameters during the installation. So thank you mc4man for your help.

@Bashing-om
Are dpkg outputs still necessary to know?

Do you think it's better to try something else to test my graphics or I can put [solved]? In case what else?

---

### Post by Bashing-om on 2019-02-18
gipsyshadow; Outstanding :)

You do good work.

For peace-of-mind:
```

sudo lshw -C display

```
Now shows a driver loaded ? ( the parameter 'nomodeset' defeats the Kernel Mode Setting that allows driver discovery) 

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by mc4man on 2019-02-19
```
sudo gedit /etc/default/grub
```
In the future don't run gedit as root like like. Either as below or learn to use nano (pretty easy to pick up.
sudo -H gedit /path/to/file

You may have a root owned file or two now in home folder, no real big deal but not a good idea. In a freshly opened terminal this could show any, if any..
```
ls -lA -R  |grep "root root"
```

---

### Post by gipsyshadow on 2019-02-19
```

$ sudo lshw -C display
[sudo] 
  *-display                 
       description: VGA compatible controller
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:38:00.0
       version: c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: driver=amdgpu latency=0
       resources: irq:53 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fe600000-fe67ffff

```
amdgpu driver's born :)

```

$ sudo ls -lA -R  |grep "root root"
[sudo] 
drwx------ 2 root root 4096 feb 19 01:07 session-bus
-rw-r--r-- 1 root root 466 feb 19 01:13 ba3a4da63c504fb388617e3b349da08c-0

```

@mc4man
sorry but I don't understand. I see I made a mistake with command "sudo gedit /etc/default/grub" because nano'd be better than gedit for that so I guess it'll be better "sudo nano /etc/default/grub" for next times, won't it be?
what about "sudo -H gedit /path/to/file"? I tried it but a blank text file was opened (created?).
What about the 2 files found in home?

---

### Post by mc4man on 2019-02-19
sudo -H gedit /path/to/file is a generic example, /path/to/file means the path to the target file.
Ex.
```
sudo -H gedit /etc/default/grub
```

> sudo ls -lA -R  |grep "root root"
While not an issue sudo wasn't 'advised'   here nor needed.
Probably you have a folder in your home named .dbus owned by root, you can remove the folder & it's content s ( contents are a folder named session-bus, file in that named ba3a4da63c504fb388617e3b349da08c-0

---

### Post by gipsyshadow on 2019-02-27
Bad news for me. Due to many reasons I had to reinstall both win and ubuntu and now I'm in a new (strange) situation. I've got 3 kernels:
```

$ dpkg --list | grep linux-image
ii  linux-image-4.15.0-29-generic                 4.15.0-29.31                                 amd64        Signed kernel image generic
ii  linux-image-4.15.0-45-generic                 4.15.0-45.48                                 amd64        Signed kernel image generic
ii  linux-image-generic                           4.15.0.45.47                                 amd64        Generic Linux kernel image
ii  linux-image-unsigned-4.20.11-042011-generic   4.20.11-042011.201902200535                  amd64        Linux kernel image for version 4.20.11 on 64 bit x86 SMP

```
and I know I've made a mistake getting the 4.20.11 via ukuu because it's not for ubuntu anyway I did and ubuntu can run it but with some freezes. I installed it suddenly at the first session after the installation so I didn't try the native 4.15.0-29 without "nomodeset" parameter because I already knew it could work. Now I've just tried to start ubuntu with both 4.15.0-29 and 4.15.0-45 to uninstall 4.20.11 but I've got black screen in both cases. I opened boot option and saw there was no nomodeset parameter in the proper line then I added it and session could start but with the already said graphic issues. Therefore now my situation is opposite of the beginning: I can start these 2 kernels only with nomodeset and of course this causes graphic issues; consider "driver=amdgpu" has disappeared from "$ sudo lshw -C display".
What did it happen this time and how to solve?

---

### Post by gipsyshadow on 2019-03-01
Sorry to reply to myself but I can't still use ubuntu and that's a mess for me.
I tried to reinstall ubuntu 18.04.1lts root (home is separated and I didn't touch it) but this graphical issue goes on and sessions are almost graphically frozen. Now I'm back to the beginnings because I can't use ubuntu moreover I can't understand why this issue was solved before but is now present again under (apparently) the same conditions.
Could you please help me?

---

