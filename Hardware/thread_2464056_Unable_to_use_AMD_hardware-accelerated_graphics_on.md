---
title: "Unable to use AMD hardware-accelerated graphics on Kubuntu 20.04.2"
date: 2021-06-23
forum: Hardware
---

### Post by Tamara_Macadam on 2021-06-23
**Didn't realise there was a dedicated hardware subforum, thread is now there: [https://ubuntuforums.org/showthread.php?t=2464237&p=14045827](https://ubuntuforums.org/showthread.php?t=2464237&p=14045827) Can't figure out how to delete this thread though, sorry everyone.**

Hi,

This has actually been a problem that has been following me for a while and made me switch away from Arch Linux, so that's always fun. I want to be able to use the hardware-accelerated graphics drivers for my AMD Radeon RX 570, but have been unable to do so. When I install them, I get the warning ```
WARNING: nomodeset detected in kernel parameters, amdgpu requires KMS
```

The problem is that when I remove nomodeset and update GRUB and all that good stuff, upon next boot I just receive a black screen. The monitor shuts off because it's not receiving a signal, and I am thus forced to add nomodeset back into the kernel parameters. But then ```
lshw -c video
``` doesn't show amdgpu as the graphics driver, nothing of the sort.

Honestly, my real problem is that I have to use nomodeset to boot successfully but when I do I can't use the drivers properly. It is... deeply irritating, and any help would be greatly appreciated. Honestly starting to think this might be a kernel bug but I don't want to be too hasty.

Thanks!

---

### Post by Tamara_Macadam on 2021-06-27
Update: I tried adding amdgpu.dpm=0 to the kernel parameters, but that didn't change anything.

Here's the results for when I do sudo dmesg | grep amdgpu, when nomodeset is *not* enabled:

```
[FONT=monospace][COLOR=#000000][    0.808430] [drm] amdgpu kernel modesetting enabled. [/COLOR]
[    0.808504] amdgpu: Ignoring ACPI CRAT on non-APU system 
[    0.808515] amdgpu: Topology: Add CPU node 
[    0.808577] fb0: switching to amdgpudrmfb from EFI VGA 
[    0.808622] amdgpu 0000:08:00.0: vgaarb: deactivate vga console 
[    0.808720] amdgpu 0000:08:00.0: amdgpu: Trusted Memory Zone (TMZ) feature not supported 
[    0.808910] amdgpu 0000:08:00.0: No more image in the PCI ROM 
[    0.808930] amdgpu: ATOM BIOS: xxx-xxx-xxx 
[    0.808994] amdgpu 0000:08:00.0: amdgpu: VRAM: 4096M 0x000000F400000000 - 0x000000F4FFFFFFFF (4096M used) 
[    0.808995] amdgpu 0000:08:00.0: amdgpu: GART: 256M 0x000000FF00000000 - 0x000000FF0FFFFFFF 
[    0.809147] [drm] amdgpu: 4096M of VRAM memory ready 
[    0.809151] [drm] amdgpu: 4096M of GTT memory ready. 
[    0.812181] amdgpu: hwmgr_sw_init smu backed is polaris10_smu 
[    1.017188] amdgpu: Topology: Add dGPU node [0x67df:0x1002] 
[    1.017192] amdgpu 0000:08:00.0: amdgpu: SE 4, SH per SE 1, CU per SH 9, active_cu_number 32 
[    1.017225] amdgpu 0000:08:00.0: [drm] Cannot find any crtc or sizes 
[    1.021196] [drm] Initialized amdgpu 3.38.0 20150101 for 0000:08:00.0 on minor 0 
[    4.901386] snd_hda_intel 0000:08:00.1: bound 0000:08:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu]) 
[   12.584881] amdgpu 0000:08:00.0: [drm] Cannot find any crtc or sizes
[/FONT]
```

And this is lshw -c video:

```
[FONT=monospace][COLOR=#000000]  *-display                  [/COLOR]
       description: VGA compatible controller 
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       version: ef 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom 
       configuration: driver=amdgpu latency=0 
       resources: irq:63 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:f000(size=256) memory:fcf00000-fcf3ffff memory:c0000-dffff
[/FONT]
```

Here's what happens with dmesg when nomodeset *is* enabled:

```
[FONT=monospace][COLOR=#000000][    0.811873] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting. [/COLOR]
[    4.739501] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
[/FONT]
```

Aaaand lshw -c video:

```
[FONT=monospace][COLOR=#000000]  *-display UNCLAIMED        [/COLOR]
       description: VGA compatible controller 
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       version: ef 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi vga_controller bus_master cap_list 
       configuration: latency=0 
       resources: memory:e0000000-efffffff memory:f0000000-f01fffff ioport:f000(size=256) memory:fcf00000-fcf3ffff memory:c0000-dffff
[/FONT]
```

Incidentally, when amdgpu.dpm=0 was in the kernel parameters, the display was getting a signal, but it was still completely black. When that wasn't there, the display wasn't receiving any signal at all.

Once again, any help would be greatly appreciated. Thanks!

---

### Post by Tamara_Macadam on 2021-06-27
Didn't realise there was a hardware subforum, oops.

This has actually been a problem that has been following me for a while  and made me switch away from Arch Linux, so that's always fun. I want to  be able to use the hardware-accelerated graphics drivers for my AMD  Radeon RX 570, but have been unable to do so. When I install them, I get  the warning ```
WARNING: nomodeset detected in kernel parameters,  amdgpu requires KMS
```

The problem is that when I remove nomodeset and update GRUB and all that  good stuff, upon next boot I just receive a black screen. The monitor  shuts off because it's not receiving a signal, and I am thus forced to  add nomodeset back into the kernel parameters. I tried adding amdgpu.dpm=0 to the kernel parameters, but that didn't change anything.

Here's the results for when I do sudo dmesg | grep amdgpu, when nomodeset is *not* enabled:

```
[FONT=monospace][COLOR=#000000][    0.808430] [drm] amdgpu kernel modesetting enabled. [/COLOR]
[    0.808504] amdgpu: Ignoring ACPI CRAT on non-APU system 
[    0.808515] amdgpu: Topology: Add CPU node 
[    0.808577] fb0: switching to amdgpudrmfb from EFI VGA 
[    0.808622] amdgpu 0000:08:00.0: vgaarb: deactivate vga console 
[    0.808720] amdgpu 0000:08:00.0: amdgpu: Trusted Memory Zone (TMZ) feature not supported 
[    0.808910] amdgpu 0000:08:00.0: No more image in the PCI ROM 
[    0.808930] amdgpu: ATOM BIOS: xxx-xxx-xxx 
[    0.808994] amdgpu 0000:08:00.0: amdgpu: VRAM: 4096M 0x000000F400000000 - 0x000000F4FFFFFFFF (4096M used) 
[    0.808995] amdgpu 0000:08:00.0: amdgpu: GART: 256M 0x000000FF00000000 - 0x000000FF0FFFFFFF 
[    0.809147] [drm] amdgpu: 4096M of VRAM memory ready 
[    0.809151] [drm] amdgpu: 4096M of GTT memory ready. 
[    0.812181] amdgpu: hwmgr_sw_init smu backed is polaris10_smu 
[    1.017188] amdgpu: Topology: Add dGPU node [0x67df:0x1002] 
[    1.017192] amdgpu 0000:08:00.0: amdgpu: SE 4, SH per SE 1, CU per SH 9, active_cu_number 32 
[    1.017225] amdgpu 0000:08:00.0: [drm] Cannot find any crtc or sizes 
[    1.021196] [drm] Initialized amdgpu 3.38.0 20150101 for 0000:08:00.0 on minor 0 
[    4.901386] snd_hda_intel 0000:08:00.1: bound 0000:08:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu]) 
[   12.584881] amdgpu 0000:08:00.0: [drm] Cannot find any crtc or sizes
[/FONT]
```

And this is lshw -c video:

```
[FONT=monospace][COLOR=#000000]  *-display                  [/COLOR]
       description: VGA compatible controller 
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       version: ef 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom 
       configuration: driver=amdgpu latency=0 
       resources: irq:63 memory:e0000000-efffffff  memory:f0000000-f01fffff ioport:f000(size=256) memory:fcf00000-fcf3ffff  memory:c0000-dffff
[/FONT]
```

Here's what happens with dmesg when nomodeset *is* enabled:

```
[FONT=monospace][COLOR=#000000][    0.811873] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting. [/COLOR]
[    4.739501] [drm:amdgpu_init [amdgpu]] *ERROR* VGACON disables amdgpu kernel modesetting.
[/FONT]
```

Aaaand lshw -c video:

```
[FONT=monospace][COLOR=#000000]  *-display UNCLAIMED        [/COLOR]
       description: VGA compatible controller 
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       version: ef 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi vga_controller bus_master cap_list 
       configuration: latency=0 
       resources: memory:e0000000-efffffff memory:f0000000-f01fffff  ioport:f000(size=256) memory:fcf00000-fcf3ffff memory:c0000-dffff
[/FONT]
```

Incidentally, when amdgpu.dpm=0 was in the kernel parameters, the  display was getting a signal, but it was still completely black. When  that wasn't there, the display wasn't receiving any signal at all.

Any help would be greatly appreciated. Thanks!

---

### Post by QIII on 2021-06-27
Threads merged.  

Please do not start duplicate threads.  If you would like to have a thread moved, please use the "report post" button and leave a message for the Staff indicating that you would like the thread moved.  We will decide if that is appropriate.

---

### Post by Yellow Pasque on 2021-06-27
Possibly related: [https://gitlab.freedesktop.org/drm/amd/-/issues/490](https://gitlab.freedesktop.org/drm/amd/-/issues/490)

---

### Post by linuux on 2021-06-27
I want to upgrade my Dell Optiplex to a discrete graphics card and one card I am considering is an RX 550, 4gb.  

I would like to help you but obviously, I don't have similar hardware yet.  I do believe that this is an isolated case because lots of people have RX 550, 560, 570, 580 cards and use Linux, including Ubuntu.   Why you are having that problem, I have no clue.  However, my suggestion is to add more info in case someone here reads your post and notices something that offers a clue.

You might offer details on your hardware - cpu, memory, cable connection - is this using hdmi to hdmi or what?  The problem of the black screen happens.  I tested my Ubuntu iso on my usb flash drive at a friend's - who has an nvidia card.  I did get it to work but I used safe graphics mode.  

AMD uses open source drivers - 'amdgpu' and you shouldn't need nomodeset.  I would try other things and take that out of the kernel parameters.   Can you use an hdmi to hdmi cable connection?   Is it hdmi 2.0?  Amdgpu uses/requires kms and it's disabled if you use nomodeset, hence the message.

P.S.  do you get the same result if you try an Ubuntu 20.04 iso (run it at defaults and if it goes to black screen, choose safe graphics mode)?   Try that and see what happens.  You shouldn't have to 'install' anything - if you use open source amdgpu drivers, it should just boot up and run.

---

### Post by Tamara_Macadam on 2021-06-27
> **linuux said:**
> I want to upgrade my Dell Optiplex to a discrete graphics card and one card I am considering is an RX 550, 4gb.  

I would like to help you but obviously, I don't have similar hardware yet.  I do believe that this is an isolated case because lots of people have RX 550, 560, 570, 580 cards and use Linux, including Ubuntu.   Why you are having that problem, I have no clue.  However, my suggestion is to add more info in case someone here reads your post and notices something that offers a clue.

You might offer details on your hardware - cpu, memory, cable connection - is this using hdmi to hdmi or what?  The problem of the black screen happens.  I tested my Ubuntu iso on my usb flash drive at a friend's - who has an nvidia card.  I did get it to work but I used safe graphics mode.  

AMD uses open source drivers - 'amdgpu' and you shouldn't need nomodeset.  I would try other things and take that out of the kernel parameters.   Can you use an hdmi to hdmi cable connection?   Is it hdmi 2.0?  Amdgpu uses/requires kms and it's disabled if you use nomodeset, hence the message.

P.S.  do you get the same result if you try an Ubuntu 20.04 iso (run it at defaults and if it goes to black screen, choose safe graphics mode)?   Try that and see what happens.  You shouldn't have to 'install' anything - if you use open source amdgpu drivers, it should just boot up and run.

I'm using an HDMI to HDMI connection, my monitor only supports HDMI. The CPU is an AMD Ryzen 5 2600, 16GB of memory, Asus Prime B450-Plus motherboard.

The problem is that I *can't* boot up without nomodeset, so I'm unable to use amdgpu. The only way for me to boot is without graphics drivers. I'm not sure if it's HDMI 2.0 or not, but it seems likely.

If I boot from an ISO, I get the black screen unless I use safe graphics... which enables nomodeset, thus disabling amdgpu.

EDIT: A thought occurs. On Arch Linux, the problem didn't occur until I upgraded to the 5.12 kernel. Kubuntu 20.04.2 is using 5.8, and yet I'm having the same problem despite it working fine on 5.8 under Arch.

Could this be a hardware fault? I'm not sure how I'd check, is the thing, since I don't really have a spare Radeon RX 570 or a spare PC just lying about.

---

### Post by linuux on 2021-06-28
> **Tamara_Macadam said:**
> I'm using an HDMI to HDMI connection, my monitor only supports HDMI. The CPU is an AMD Ryzen 5 2600, 16GB of memory, Asus Prime B450-Plus motherboard.

The problem is that I *can't* boot up without nomodeset, so I'm unable to use amdgpu. The only way for me to boot is without graphics drivers. I'm not sure if it's HDMI 2.0 or not, but it seems likely.

If I boot from an ISO, I get the black screen unless I use safe graphics... which enables nomodeset, thus disabling amdgpu.

EDIT: A thought occurs. On Arch Linux, the problem didn't occur until I upgraded to the 5.12 kernel. Kubuntu 20.04.2 is using 5.8, and yet I'm having the same problem despite it working fine on 5.8 under Arch.

Could this be a hardware fault? I'm not sure how I'd check, is the thing, since I don't really have a spare Radeon RX 570 or a spare PC just lying about.If you use nomodeset, then your computer will boot with a working screen?   If so, then it's probably not hardware?  Do you use Windows?  Does this same computer work fine in Windows?

I would try a 20.10 iso and 21.04 iso to see if the same result happens.  

As I said, I tested on a 21.04 iso and the hardware was similar to yours - Ryzen 2600x, 32gb RAM, Rx 570 (not sure which brand, or how many gb - I can find out, but I don't think it's a factor).   It booted up fine and I don't recall nomodeset being enabled.  I'm pretty sure, I selected the default setting at the grub screen.  

If hardware was the culprit, the screen would go out randomly or when stressing hardware (gaming, accessing some software program).  That doesn't seem to be happening here.  

I suggest trying the other live versions - on a usb flash drive, and report what happens, whether it's the same experience or something different.

Edit:  the reason I am suggesting to try the other versions is that, AFAIK, amdgpu version should be newer and the kernel is newer.  Just wondering if either is a factor or changes your experience at all.  That's what I am assuming, I'm testing.

---

### Post by Tamara_Macadam on 2021-06-28
> **linuux said:**
> If you use nomodeset, then your computer will boot with a working screen?   If so, then it's probably not hardware?  Do you use Windows?  Does this same computer work fine in Windows?

I would try a 20.10 iso and 21.04 iso to see if the same result happens.  

As I said, I tested on a 21.04 iso and the hardware was similar to yours - Ryzen 2600x, 32gb RAM, Rx 570 (not sure which brand, or how many gb - I can find out, but I don't think it's a factor).   It booted up fine and I don't recall nomodeset being enabled.  I'm pretty sure, I selected the default setting at the grub screen.  

If hardware was the culprit, the screen would go out randomly or when stressing hardware (gaming, accessing some software program).  That doesn't seem to be happening here.  

I suggest trying the other live versions - on a usb flash drive, and report what happens, whether it's the same experience or something different.

Edit:  the reason I am suggesting to try the other versions is that, AFAIK, amdgpu version should be newer and the kernel is newer.  Just wondering if either is a factor or changes your experience at all.  That's what I am assuming, I'm testing.

I don't have Windows so I'm unable to test that. Using a 20.10 ISO and 21.04 ISO, I had the same problem. Again, I first noticed this issue with Arch under the 5.12 kernel, and yet it has somehow propagated backwards into the 5.8 kernel with Kubuntu 20.04.2. The AMDGPU driver itself hasn't been updated in either the Arch repo or the Ubuntu repos for over a year, because it hasn't been updated upstream in that long. It seems impossible for this to be caused by a driver update as a result, because those *have definitely not changed*. Since the kernel seems to be irrelevant as well, it feels like the issue is independent of the kernel and the driver.

Which has completely broken my brain, honestly...

---

### Post by mastablasta on 2021-06-29
i assume you have amdgpu and that you didn't patch kernel with AMDGPU-pro or anything like that?

you could try kernel parameter: ```
iommu=soft
```

it should affect you as you don't have an APU, but you never know.

here is another solution to a similar problem: [https://askubuntu.com/questions/1135590/amdgpu-driver-refuses-to-load-on-19-04](https://askubuntu.com/questions/1135590/amdgpu-driver-refuses-to-load-on-19-04)

another option is you do actually install the pro drivers: [https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676/page/18](https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676/page/18)

quite possibly some bug in AMD driver: [https://bugzilla.kernel.org/show_bug.cgi?id=200695](https://bugzilla.kernel.org/show_bug.cgi?id=200695)
but you could try the workaround: ```
amdgpu.dc=0
```

here is a patch for ni output: [https://bugzilla.kernel.org/show_bug.cgi?id=209721](https://bugzilla.kernel.org/show_bug.cgi?id=209721)
i came to it from Manjaro (arch based) forum: [https://forum.manjaro.org/t/what-is-kernel-parameter-amdgpu-dc-0-doing-and-why-do-i-suddenly-need-it/32813](https://forum.manjaro.org/t/what-is-kernel-parameter-amdgpu-dc-0-doing-and-why-do-i-suddenly-need-it/32813)

you could also try loading all updates. maybe the patch is in kernel?!

---

### Post by linuux on 2021-06-29
> **Tamara_Macadam said:**
> I don't have Windows so I'm unable to test that. Using a 20.10 ISO and 21.04 ISO, I had the same problem. Again, I first noticed this issue with Arch under the 5.12 kernel, and yet it has somehow propagated backwards into the 5.8 kernel with Kubuntu 20.04.2. The AMDGPU driver itself hasn't been updated in either the Arch repo or the Ubuntu repos for over a year, because it hasn't been updated upstream in that long. It seems impossible for this to be caused by a driver update as a result, because those *have definitely not changed*. Since the kernel seems to be irrelevant as well, it feels like the issue is independent of the kernel and the driver.

Which has completely broken my brain, honestly...
Okay, 'was worth a shot.  I was going to suggest a Fedora 34 iso next but I am starting to think there's something strange going on.  Another poster is suggesting some steps so maybe a new direction is needed.

I was wondering about the drivers and amdgpu & amdgpu-pro.  I wonder if it's possible to have both drivers installed or have a conflict.  Could you check Software Manager and see the section of 'Additional Drivers' and what is clicked there?

There's something peculiar going on, imho.  Like I said earlier, I tried booting 21.04 for an experiment on a system that had similar specs as yours:  2600x, RX 570....the RAM was 32gb, but the main components cpu and gpu was sufficiently similar.  I believe I chose the default Ubuntu in grub and it booted no problem.

We both tried the same iso with different results.  It is interesting, though, that you can't boot normally with an installed Ubuntu OS or any live iso either.   That suggests hardware to me but it's difficult to tell.  I still think installing Windows on another hard drive and seeing what happens would be interesting to try.

If you can't get ANY live OS iso to boot properly at defaults with an RX 570, that's really weird.  By now, the Rx 570 (Polaris 20) cards are supported by AMD open source drivers - amdgpu - and you shouldn't have to mess with kernel parameters or anything else.   The only thing that I remember one might want is upgraded/updated Mesa.

What is your psu?  What is the gpu, exactly?  What is your display hardware - monitor or TV, etc.?   Just curious.

Did this problem just happen recently?  Or the first time you installed Ubuntu with this card?  You said that Arch had the same problem - at the very beginning?  Was there any upgrades or updates done - did it ever boot up properly or from day one trying the OS?

---

### Post by linuux on 2021-06-29
> **mastablasta said:**
> i assume you have amdgpu and that you didn't patch kernel with AMDGPU-pro or anything like that?

you could try kernel parameter: ```
iommu=soft
```

it should affect you as you don't have an APU, but you never know.

here is another solution to a similar problem: [https://askubuntu.com/questions/1135590/amdgpu-driver-refuses-to-load-on-19-04](https://askubuntu.com/questions/1135590/amdgpu-driver-refuses-to-load-on-19-04)

another option is you do actually install the pro drivers: [https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676/page/18](https://community.amd.com/t5/drivers-software/can-t-install-amdgpu-drivers-on-ubuntu-20-04-1-5-4-0-56-generic/td-p/426676/page/18)

quite possibly some bug in AMD driver: [https://bugzilla.kernel.org/show_bug.cgi?id=200695](https://bugzilla.kernel.org/show_bug.cgi?id=200695)
but you could try the workaround: ```
amdgpu.dc=0
```

here is a patch for ni output: [https://bugzilla.kernel.org/show_bug.cgi?id=209721](https://bugzilla.kernel.org/show_bug.cgi?id=209721)
i came to it from Manjaro (arch based) forum: [https://forum.manjaro.org/t/what-is-kernel-parameter-amdgpu-dc-0-doing-and-why-do-i-suddenly-need-it/32813](https://forum.manjaro.org/t/what-is-kernel-parameter-amdgpu-dc-0-doing-and-why-do-i-suddenly-need-it/32813)

you could also try loading all updates. maybe the patch is in kernel?!
Thanks for trying to help.   I didn't think of those angles.

My question regarding the question "maybe it's a bug or relating to a driver problem" is I cannot find similar problems across this forum or any other place.  I checked this forum, Pop OS, Fedora, OpenSUSE forums and other sites - askUbuntu for e.g. - but, I cannot find similar experiences with mentions of 'bug' or anything relating to a bug impacting users of Rx 570, Rx 580 or Rx 590 video cards.

I would expect a bug to at least affect a number of users provoking similar posts.  Wouldn't they?  

Yes, we all have different hardware but the OP's hardware is pretty common - Ryzen 2600x, Rx 570.... for it not to boot even a live iso and output the same problem as the installed system, I thought was strange.  

Then, maybe I don't know what I am talking about.  That's always a possibility but I am trying (to help), anyway. :=)

---

### Post by Tamara_Macadam on 2021-06-29
> **mastablasta said:**
> but you could try the workaround: ```
amdgpu.dc=0
```

**This has done the trick!** I have visual output on the display, and the amdgpu driver is loaded. Also vsynctester.com is displaying at 60 fps, and not around 42 fps like it was without amdgpu.

I'll put some more hardware info here, fortunately I made a list a while ago of every component in the system: ```
Case: Cooler Master K282
CPU: AMD Ryzen 5 2600 with Wraith Stealth cooler
Motherboard: Asus Prime B450 Plus
GPU: Gigabyte Radeon RX 570 Gaming 4GB
Memory: Corsair Vengeance LPX 16 GB (2x8GB) DDR4 2400 MHz Black
PSU: Super Flower Leadex III Gold 650W
Optical Drive: LG Blu-ray Writer 16x
Memory Card Reader: Icy Box 863-A Card Reader
Wi-Fi Card: TP-Link Archer T4E-AC1200
USB Expansion: Orico 5 Port USB3 PCI-E Expansion Card
SSD: Crucial MX500 250GB SSD
HDD: Seagate Barracuda 2TB 7200RPM HDD

```

Also the monitor is a BenQ GW2270H.

Obviously that kernel option isn't exactly ideal - I'm not sure what it does, but it seems like it'd be better to just avoid it. (Maybe it is a kernel bug after all?) However, as my graphics are now working (and I don't know what I would use Display Core for anyway), I'm happy.

Thanks everyone!

---

### Post by linuux on 2021-06-29
> **Tamara_Macadam said:**
> **This has done the trick!** I have visual output on the display, and the amdgpu driver is loaded. Also vsynctester.com is displaying at 60 fps, and not around 42 fps like it was without amdgpu.

I'll put some more hardware info here, fortunately I made a list a while ago of every component in the system: ```
Case: Cooler Master K282
CPU: AMD Ryzen 5 2600 with Wraith Stealth cooler
Motherboard: Asus Prime B450 Plus
GPU: Gigabyte Radeon RX 570 Gaming 4GB
Memory: Corsair Vengeance LPX 16 GB (2x8GB) DDR4 2400 MHz Black
PSU: Super Flower Leadex III Gold 650W
Optical Drive: LG Blu-ray Writer 16x
Memory Card Reader: Icy Box 863-A Card Reader
Wi-Fi Card: TP-Link Archer T4E-AC1200
USB Expansion: Orico 5 Port USB3 PCI-E Expansion Card
SSD: Crucial MX500 250GB SSD
HDD: Seagate Barracuda 2TB 7200RPM HDD

```

Also the monitor is a BenQ GW2270H.

Obviously that kernel option isn't exactly ideal - I'm not sure what it does, but it seems like it'd be better to just avoid it. (Maybe it is a kernel bug after all?) However, as my graphics are now working (and I don't know what I would use Display Core for anyway), I'm happy.

Thanks everyone!
Awesome to hear!  I'm glad you found something that works/helps.  I'm glad mastablasta volunteered his expertise....I wouldn't want you going down a rabbit hole with my crappy advice.....haha....

I am interested in his solution/advice.  I'll have to look into it.  I might have an RX 550 or RX 570 in the future - hopefully.  Keep us updated with any new developments - if anything changes!  Cheers!

---

### Post by mastablasta on 2021-06-30
kernel bug then it seems.
here is what you did:

> **drm/amd/display - Display Core (DC)**

[COLOR=#000000][FONT=serif]Because it is partially shared with other operating systems, the Display Core Driver is divided in two pieces.[/FONT][/COLOR]

[LIST]
[*]Display Core (DC) contains the OS-agnostic components. Things like hardware programming and resource management are handled here.
[*]Display Manager (DM) contains the OS-dependent components. Hooks to the amdgpu base driver and DRM are implemented here.
[/LIST]
[COLOR=#000000][FONT=serif]It doesn&#8217;t help that the entire package is frequently referred to as DC. But with the context in mind, it should be clear.[/FONT][/COLOR]
[COLOR=#000000][FONT=serif]When CONFIG_DRM_AMD_DC is enabled, DC will be initialized by default for supported ASICs. To force disable, set amdgpu.dc=0 on kernel command line. Likewise, to force enable on unsupported ASICs, set amdgpu.dc=1.[/FONT][/COLOR]
[COLOR=#000000][FONT=serif]To determine if DC is loaded, search dmesg for the following entry:[/FONT][/COLOR]
[COLOR=#000000][FONT=serif]Display Core initialized with <version number here>[/FONT][/COLOR]


on the other hand it could be that your system does doe snot have supported ASICs. ASIC: [https://en.wikipedia.org/wiki/Application-specific_integrated_circuit](https://en.wikipedia.org/wiki/Application-specific_integrated_circuit)

anyway must be some switching in kernel not working correctly. i mean there is so many people where card works flawlessly and so many people with issues. i hope they fix it soon.

also as long as things are working ok, you should be fine...

---

