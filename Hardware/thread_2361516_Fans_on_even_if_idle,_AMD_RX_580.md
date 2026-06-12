---
title: "Fans on even if idle, AMD RX 580"
date: 2017-05-17
forum: Hardware
---

### Post by nigro.orlando on 2017-05-17
Hi!
I just installed my new amd rx 580 and I noticed that the in Ubuntu (17.04) the fans are always on even if on idle, which doesn't happen on Windows. 
It's a Asus card with three fans. 

Is there something I can do about it?

I just recently installed the latest release of Ubuntu Gnome so everything should be up to date

---

### Post by QIII on 2017-05-17
Every AMD GPU with fans I have ever owned has kept the fans spinning at minimum while idle -- both Windows and Linux.

Have you done any research to find the expected behavior?

Which driver are you using?

---

### Post by nigro.orlando on 2017-05-17
I have had a different experience. I had a MSI R9 390 that didn't keep the fans spinning while idle on Windows. And I think it did so on linux too. 

Anyway, in this particular case I can guarantee that the fans don't spin on Windows. 
 
The RX 580 has a technology that keeps the fans from spin when under 54 degrees Celsius. I haven't found much information about the 580 on linux and how it should behave but I guess it should be similar to the 480

---

### Post by QIII on 2017-05-17
Which driver are you using?

---

### Post by nigro.orlando on 2017-05-17
```
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD POLARIS10 (DRM 3.9.0 / 4.10.0-20-generic, LLVM 4.0.0)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.0.3
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.0.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 17.0.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:


```

---

### Post by nigro.orlando on 2017-05-17
ok I don't know if I actually answered your question :P, sorry about that, but I think is basically AMDGPU, I didn't change anything since the installation of ubuntu

---

### Post by QIII on 2017-05-17
OK.

I don't have a GPU of that series to test, but it could be that if this is fairly new technology then the control may not yet be exposed in AMDGPU.

I'd have to do some research, but I am at my day job right now and won't have the opportunity to do that for about the next 9 hours.

---

### Post by Yellow Pasque on 2017-05-17
The rx500 cards are very recent. Try a 4.11 kernel to see if the issue is fixed.

---

### Post by nigro.orlando on 2017-05-18
@ Qlll, thank you for looking into this, there is of course no rush and I'll try to do some research myself. 
This issue is not a big problem. The fans are not spinning at high speed and they at least keep the card cool. It's just a shame since I did like the silence that card could have given me and I have an otherwise very much silent computer.

@ Temüjin
God point, I'll look into that.

---

### Post by nigro.orlando on 2017-05-18
@Temüjin

will the kernel automatically be implemented in ubuntu soon?

---

### Post by Yellow Pasque on 2017-05-18
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by nigro.orlando on 2017-05-19
I have some interesting news, I checked that the file **power_dpm_state** has the value: **performance**.
and the file **power_dpm_force_performance_level** says **auto**.

Could this be useful information?

by the way, I installed the kernel 4.11 but nothing changed. The fans are still on, all the time. 
It doesn't look good for the card to be on performance level with no reason

---

### Post by nigro.orlando on 2017-05-19
should I maybe try amdgpu-pro?

---

### Post by Yellow Pasque on 2017-05-20
> **nigro.orlando said:**
> should I maybe try amdgpu-pro?

I don't think it supports Ubuntu 17.04.

---

### Post by nigro.orlando on 2017-05-21
Ok, I installed ubuntu 16.04 and the amdgpu-pro driver to see if it changed anything but the card is still going full speed.

---

### Post by Yellow Pasque on 2017-05-21
You may also need to manually download firmware files or install the linux-firmware package from Ubuntu 17.10 if dmesg complains about missing amd firmware:
[https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/amdgpu](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/amdgpu)
[https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.165_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.165_all.deb)

```
dmesg | grep -i firmw
```

---

### Post by nigro.orlando on 2017-05-22
I can't check that right now since I took the card out. I didn't want it to be on performance level all the time with no actual need for it.

I'll maybe try it but I I'mseriously thinking to switch to Nvidia, instead of having my card on full speed for weeks or months till this function will be implemented in the driver, which is not even sure to be going to happen.[****]("https://www.google.se/search?client=firefox-b-ab&q=seriously&spell=1&sa=X&ved=0ahUKEwiH7Ompp4PUAhWIWSwKHYaACh8QBQgjKAA")

---

### Post by nigro.orlando on 2017-05-24
I gave up on the 580. I bought a 1070 and I don't have problems there with this issue. The fans don't move as long as the card is below a certain temperature and is therefore completely silent on idle.

Too bad about the 580. I really liked that card and  it has in my opinion the best value for money right now. Unfortunately I couldn't wait for the driversupport to update and fix this issue. And I'm also not enough linux-competent to fix it myself.

---

