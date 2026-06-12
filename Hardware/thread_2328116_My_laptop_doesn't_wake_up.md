---
title: "My laptop doesn't wake up"
date: 2016-06-17
forum: Hardware
---

### Post by Juan_Fiorenzano on 2016-06-17
Hello community how are you doing? I am having this problem with my laptop Asus x555u and Ubuntu 16.04, when I put the laptop to sleep, Ubuntu doesn't wake up I have to press the shutdown button for start the system again, I have a Nvidia 940m with the property drivers installed, I some post the people advice to update to the 4.4.8 kernel version I did that but I still having the same problem.

```

lspci -v

....

01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940M] (rev a2)
    Subsystem: ASUSTeK Computer Inc. GM108M [GeForce 940M]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at df000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_361
....

```

I have a skylake processor I don't know if this has something to do.

---

### Post by wmoore on 2016-06-19
When you say "Ubuntu doesn't wake up" do you mean that the laptop doesn't power on at all, or just that the screen stays black? I run 16.04 on a MacBook Air and there is a known issue where after suspend, the screen doesn't light up. In my case, you have to increase the brightness to maximum to get it to light up. It's an Intel graphics chip in the Mac so yours may well not be the same I guess.

---

### Post by coldraven on 2016-06-19
This is just to bump you. I have been lucky and since Ubuntu 8.04 all my machines have restored from suspend. I hope that a solution is found.

---

