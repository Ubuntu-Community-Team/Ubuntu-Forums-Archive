---
title: "How do I install 9.04 Alpha 4 in Virtualbox"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by cchester on 2009-02-06
Hey guys and girls,

I just downloaded and burned Ubuntu 9.04 Jaunty Alpha 4 and burned it to cd.

I then created a Ubuntu 64 virtual machine in virtualbox and tried to install it and it say I can't because I am using a x86 system?

So how do I setup virtualbox the correct way so that I can test the new Aplha 4 because going with what was obvious in virtualbox wasn't the correct way.

Please help.

Thanks.

---

### Post by howefield on 2009-02-06
You need a processor capable of running a 64 bit system, and you need version 2.1 or later of Virtualbox. Do you have these ?

---

### Post by cchester on 2009-02-07
Hello,

I have a 64 bit processor and I have Virtualbox 2.1 installed.

The only thing is my Ubuntu host system is 32 bit 8.10.

Does that make a difference?

Thanks for the reply.

> **howefield said:**
> You need a processor capable of running a 64 bit system, and you need version 2.1 or later of Virtualbox. Do you have these ?

---

### Post by howefield on 2009-02-07
Try the steps here, from the Virtualbox manual.

Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems. Starting with Version 2.1, you can even run 64-bit guests on a 32-bit host operating system, so long as you have sufficient hardware. In detail, 64-bit guests are supported under the following conditions:

1. You need a 64-bit processor with hardware virtualization support (see chapter 1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 10).

2. You must enable hardware virtualization for the particular VM for which you want 64-bit support; software virtualization is not supported for 64-bit VMs.

Note: On most systems, the hardware virtualization features first need to be enabled in the BIOS before VirtualBox can use them.

3. If you want to use 64-bit guest support on a 32-bit host operating system, you must also select a 64-bit operating system for the particular VM. Since supporting 64 bits on 32-bit hosts incurs additional overhead, VirtualBox only enables this support upon explicit request. On 64-bit hosts, 64-bit guest support is always enabled, so you can simply install a 64-bit operating system in the guest.

Warning: On any host, you should enable the I/O APIC for virtual machines that you intend to use in 64-bit mode. This is especially true for 64-bit Windows VMs. See chapter 3.7.1.2, “Advanced” tab, page 46. In addition, for 64-bit Windows guests, you should make sure that the VM uses the Intel networking device, since there is no 64-bit driver support for the AMD PCnet card; see chapter 6.1, Virtual networking hardware, page 77.

Read the manual here: [http://download.virtualbox.org/virtualbox/2.1.2/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.1.2/UserManual.pdf)

---

### Post by cchester on 2009-02-07
Hello,

Thanks for the reply I had all that checked so I guess my processor doesn't support virtualization.

Thanks.

> **howefield said:**
> Try the steps here, from the Virtualbox manual.

Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems. Starting with Version 2.1, you can even run 64-bit guests on a 32-bit host operating system, so long as you have sufficient hardware. In detail, 64-bit guests are supported under the following conditions:

1. You need a 64-bit processor with hardware virtualization support (see chapter 1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 10).

2. You must enable hardware virtualization for the particular VM for which you want 64-bit support; software virtualization is not supported for 64-bit VMs.

Note: On most systems, the hardware virtualization features first need to be enabled in the BIOS before VirtualBox can use them.

3. If you want to use 64-bit guest support on a 32-bit host operating system, you must also select a 64-bit operating system for the particular VM. Since supporting 64 bits on 32-bit hosts incurs additional overhead, VirtualBox only enables this support upon explicit request. On 64-bit hosts, 64-bit guest support is always enabled, so you can simply install a 64-bit operating system in the guest.

Warning: On any host, you should enable the I/O APIC for virtual machines that you intend to use in 64-bit mode. This is especially true for 64-bit Windows VMs. See chapter 3.7.1.2, “Advanced” tab, page 46. In addition, for 64-bit Windows guests, you should make sure that the VM uses the Intel networking device, since there is no 64-bit driver support for the AMD PCnet card; see chapter 6.1, Virtual networking hardware, page 77.

Read the manual here: [http://download.virtualbox.org/virtualbox/2.1.2/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.1.2/UserManual.pdf)

---

