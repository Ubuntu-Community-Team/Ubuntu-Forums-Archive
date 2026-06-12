---
title: "Dell Inspiron 530 hard freeze with 12.04"
date: 2012-07-20
forum: Hardware
---

### Post by richpri on 2012-07-20
This is yet another case of a hard freeze which started happening after upgrading to Ubuntu 12.04. The freeze usually happens when using Firefox to access something like a Youtube video. Though this is not always the case.

The upgrade was done about two weeks ago and when I did a update yesterday the freeze started happening within minutes after the Desktop was powered up. IE: The problem was much worse after the upgrade!  I am attaching the APT log which covers the upgrade. 

The Desktop is a Dell Inspiron 530 and I am attaching an ishw output which gives all of its hardware specifications.

I would appreciate any help or comments received. I am also interested in finding out if any other Dell Inspiron 530 users have had this problem.

---

### Post by richpri on 2012-07-22
Out of desperation I switched to Ubuntu 2d and I did not have any freezes using that version. Thus, I suspect that this issue could be related to the graphics driver.

I am using the default driver:

```
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8300 GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff 
```

Is there an alternate driver or an upgrade to this one?

---

### Post by richpri on 2012-07-22
I spoke too soon!

The Dell is now freezing under Ubuntu 2d whenever we start Firefox!

The freeze is immediate and it has not happened with any other application.

Also, I was looking in dmesg and found this set of messages:

```
[   28.210319] nvidia: module license 'NVIDIA' taints kernel.
[   28.210326] D1sabl1ng lock debugging due to kernel taint
[   28.676843] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.O-3.2)
[   28.733912] nvidia OOOO:01:OO.O:  PCI INT A -> GSI 16 (level,  low) -> IRQ 16
[   28.733925] nvidia OOOO:01:OO.O:  setting latency timer to 64
[   28.733932] vgaarb:  device changed decodes: PCI:OO00:01:OO.O,olddecodes&#8801;io+mem,decodes&#8801;none:owns&#8801;io+mem
[   28.734260] NVRM:  loading NVIDIA UNIX x86 Kernel Module  295.40  Thu Apr  5 21:28:09 PDT 2012
```

Does anyone have any suggestions about this issue??

---

### Post by richpri on 2012-07-24
I opened a bug report for this issue.

See [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1027724](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1027724)

---

