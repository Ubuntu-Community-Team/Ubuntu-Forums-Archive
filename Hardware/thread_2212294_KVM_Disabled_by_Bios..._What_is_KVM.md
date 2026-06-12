---
title: "KVM: Disabled by Bios... What is KVM?"
date: 2014-03-20
forum: Hardware
---

### Post by Nick_Germaine on 2014-03-20
I've googled it and I can't find out.  I used to use Ubuntu on my old laptop, and then when I got this newer one, I always get this message twice upon booting into ubuntu.  I can't really find out what KVM does, so I'm wondering is there a way to enable it in my bios?  Maybe someone else has a similar machine as I do:

AMD A10-5750M APU with Radeon(tm) HD Graphics × 4 
It's an HP, but I can't remember what model or anything.

I'd mostly like to know if my experience is being impacted by not having KVM enabled.  And if so, how can I get KVM enabled.  And if not, how can I suppress that message on boot?

Thanks in advance for any help.

---

### Post by TheFu on 2014-03-20
I'm only aware of 2 kinds of KVM
* Keyboard Video Mouse - a way to connect many different computers to 1 monitor, keyboard and mouse. I have a Belkin KVM switch -  4 port.
* Kernel Virtual Machine - a way to have virtual machines "inside" another machine.  There are BIOS settings for this - usually called VT-x and VT-d in every BIOS I've seen.  AMD calls it something else - VMX?  Never seen it called "KVM."

Did you install qemu, kvm, virt-manager, or virtualbox packages into your ubuntu system?

---

### Post by Nick_Germaine on 2014-03-23
No.  And even on my Windows partition (8.1) when I go into the task manager, it says virtualization is disabled.  I haven't installed any virtual machine related things in this installation of Ubuntu.

---

### Post by TheFu on 2014-03-23
If this is inside the dmesg output, ignore it.  I would guess that you HAVE installed KVM-something, perhaps though a dependency. It won't work until the bios settings are modified, but you don't care, so ignore it and be happy.

If you listed the exact BIOS vendor and version, someone else may be able to help.

---

### Post by lorcastrand on 2014-03-23
Yes! This explains why, whenever I attempt to open VirtualBox, my laptop freezes! I get this exact KVM warning everytime I start Ubuntu.

---

### Post by slooksterpsv on 2014-03-23
KVM will freeze your system if another Virtualization software (like VirtualBox) is on your system at the same time.

VirtualBox should work for your computer without AMD-V (AMD Virtualization); it should, instead of Virtualize your hardware, emulate it. If it's freezing then you have both VirtualBox and KVM installed which can cause issues.

If you want to enable AMD-V, you have to go into BIOS and look for something like:
AMD Virtualization
AMD-V
Virtualization

Something along those lines. Once it's enabled, VirtualBox should work faster.

---

### Post by TheFu on 2014-03-23
In the old days, before many CPUs/MBs supported VT-x/AMD-v, the virtualbox software virtualization support was actually faster than enabling the hardware support. But it only worked for Virtualbox - other virtual/hypervisor solutions needed that hardware support to work at all.

Oh - and having 2 competing hypervisor-like things installed on a single system is asking for trouble if they aren't known to work together.

---

### Post by monkeybrain20122 on 2014-03-23
Well I don't think OP is really interested in the intricacies of KVM  vs Virtualbox. As far as I can tell he is not even running any VM or pondering the options. He is just bothered by the message. So this pros and cons of Vbox vs KVM is largely off topic.

@OP
To get rid of the message just go to bios and enable the options (something to do with virtualization, not sure what it is called) , as you are not really running KVM that shouldn't matter, just that the OPTION is enabled.

---

### Post by TheFu on 2014-03-23
I don't see any KVM messages here on systems not installed with kvm packages.
**dmesg |grep -i KVM**

Which OS is installed?  **more /etc/lsb-release** and **uname -a** output would help.
For example:
```
$ uname  -a
Linux istar 3.11.0-17-generic #31~precise1-Ubuntu SMP Tue Feb 4 21:25:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
```

---

### Post by monkeybrain20122 on 2014-03-23
> **TheFu said:**
> I don't see any KVM messages here on systems not installed with kvm packages.
**dmesg |grep -i KVM**

Which OS is installed?  **more /etc/lsb-release** and **uname -a** output would help.
For example:
```
$ uname  -a
Linux istar 3.11.0-17-generic #31~precise1-Ubuntu SMP Tue Feb 4 21:25:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
```

I did on one machine. It was a new vanilla install and there was the message. Enabled the bios option and the message went away.

---

### Post by Nick_Germaine on 2014-04-03
Yeah, I went into the bios and flicked the switch for virtualization.  I no longer get the error messages (warnings more like) on start up.  My performances isn't affected either.

I've used Virtualbox extensively in the past, but it has never been installed on this new computer.  My Ubuntu version is 14.04 (updated every day... upgraded...  You know the thing you have to do when running alpha or beta.  That's what I do).

Thanks guys.

---

