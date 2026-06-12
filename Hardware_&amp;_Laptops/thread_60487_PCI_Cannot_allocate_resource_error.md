---
title: "PCI: Cannot allocate resource error?"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by ry_ry on 2005-08-28
I'm running Ubuntu 5.04, and after "Ok, booting the kernel...."
I get this message:
PCI: Cannot allocate resource region 3 of device 0000:00:00.0

But it boots up fine and seems to run ok except for not having DMA but I'm going to compile a kernel to try to solve that problem. The above device is relating to my Host Bridge: ATI Technologies Inc.

Should I be worried about this? And is there anyway to fix this? Is this an IRQ issue?
My motherboard is a MSI 7145 ATI RS480M SB400. And has a AMD64 3200 with ATI Xpress 200 onboard graphics with an open PCI Express slot.

Any help would be great. Thanks.

---

### Post by pmjdebruijn on 2005-08-28
Well, try pasting a 'lspci' in here, so see which device it applies to...

Regards,
Pascal de Bruijn

---

### Post by tseliot on 2005-08-28
[QUOTE=ry_ry]I'm running Ubuntu 5.04, and after "Ok, booting the kernel...."
I get this message:
PCI: Cannot allocate resource region 3 of device 0000:00:00.0

But it boots up fine and seems to run ok except for not having DMA but I'm going to compile a kernel to try to solve that problem. The above device is relating to my Host Bridge: ATI Technologies Inc.

Should I be worried about this? And is there anyway to fix this? Is this an IRQ issue?
My motherboard is a MSI 7145 ATI RS480M SB400. And has a AMD64 3200 with ATI Xpress 200 onboard graphics with an open PCI Express slot.

Any help would be great. Thanks.[/QUOTE]
I think I have the same motherboard as yours  (MSI ATI RS480)

1) I also have this error but it doesn't affect the functioning of my computer (so dont'you worry)
PCI: Cannot allocate resource region 3 of device 0000:00:00.0

2) Open "System Monitor" and go to Resources. Look at  "CPU1" you should be able to see the percentage of use of your CPU.

DO THIS WHEN NO other program is  running 

and tell me what your percentage is. If it is of about 50%, then you might be affected by the Double clock speed bug (I also have it)

Here's the solution (it works only in Ubuntu 64bit)

[http://ubuntuforums.org/showthread.php?t=53094](http://ubuntuforums.org/showthread.php?t=53094) 


And if you need a guide to compile a new kernel you can try mine. It's aimed at newbies, and it explains (among other things) also how to enable DMA in the kernel.

[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

---

### Post by ry_ry on 2005-08-28
Hi tseliot,

Yes, I had that Double Clock Speed problem, but I solved it using 32bit Ubuntu. I put "noapic" into my grub file and set my UTC=yes to UTC=no and the clock worked just fine after that. I just tried that Saturday and will check it again to make sure it's still functioning correctly.

I've already printed out your "Kernel How To" and plan to use it to try and turn on DMA for my drives. Did this work good for your RS480 system too?

---

### Post by tseliot on 2005-08-29
[QUOTE=ry_ry]Hi tseliot,

Yes, I had that Double Clock Speed problem, but I solved it using 32bit Ubuntu. I put "noapic" into my grub file and set my UTC=yes to UTC=no and the clock worked just fine after that. I just tried that Saturday and will check it again to make sure it's still functioning correctly.

I've already printed out your "Kernel How To" and plan to use it to try and turn on DMA for my drives. Did this work good for your RS480 system too?[/QUOTE]
It worked like a charm. For this reason I decided to write the guide. I knew how much pain it was before I found a way to make my system work properly and I wanted to share my knowledge.

---

### Post by ry_ry on 2005-08-29
tseliot, Thank you for the Kernel Guide, me and alot of others greatly appreciate it.

---

### Post by sfabel on 2005-12-17
Hello,

I am affected by the double speed bug, and haven't been able to solve it using your guide. Unfortunately, I am also a bit confused as to how to proceed.

I don't know what kind of motherboard I have; I know I have a HP Pavillon with X2 AMD64 Dual Processors on it.

This is the output of lspci:

```

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 10)
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:12.0 IDE interface: ATI Technologies Inc: Unknown device 4379
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0141 (rev a2)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

So it seems that my motherboard is also from ATI, but I don't know which type. I am using the newest kubuntu (breezy).

I get lots of these messages in my system log:
```

17.12.2005 11:08:40	localhost	kernel	[4295585.434000] APIC error on CPU1: 40(40)
17.12.2005 11:08:40	localhost	kernel	[4295585.434000] APIC error on CPU0: 40(40)

```

I used to have 64bit Ubuntu installed, but dropped it because of some applications that I neded and refused to run on the 64bit system. I was able to fix it there by using the "notsc" option at boot time. Now this doesn't work also:

```

17.12.2005 12:22:34	localhost	kernel	[4294667.296000] notsc: Kernel compiled with CONFIG_X86_TSC, cannot disable TSC.

```

Maybe with a recompile of the kernel. How can I recompile the exact kernel that I am now running, basically building an "official" kernel but without that option? Or is it dangerous to disable it?

Also, what does this mean:
```

17.12.2005 13:48:37	localhost	kernel	[4305183.936000] apm: disabled on user request.

```

The symptoms of my system are the usual ones, like MP3's playing fast, time going fast, keyboard entering letters multiple times, ...

Thanks for any help!

Stephan

Edit:
ok, sorry, I found the thread using the search options, and didn't realize I posted in the hoary section. I have breezy installed.

---

