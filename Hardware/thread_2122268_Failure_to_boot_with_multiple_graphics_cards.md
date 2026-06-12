---
title: "Failure to boot with multiple graphics cards"
date: 2013-03-04
forum: Hardware
---

### Post by llemes4011 on 2013-03-04
Hi guys,

I'm having a bit of an issue with booting into Ubuntu 12.10 with multiple graphics cards. The two card in question are the AMD Radeon HD 7950 and AMD Radeon HD 5850.

I had the drivers for the 7950 installed, rebooted, inserted the 5850, and when I tried to log in, compiz would crash, and the two cards would become very hot. 

I tried shutting down, removing the 5850, rebooting, uninstalling the 7950 drivers (booting w/o the 5850 worked fine), shutting down, putting in the 5850, rebooting. This time I couldn't even get to the logon screen, and it wouldn't let me access any vterms either (Ctrl+Alt+F{1..6}), and I had to power off manually. 

The reasoning behind this is I want to use the 5850 in linux, and using KVM to pass the 7950 to a Windows VM.

Any thoughts or solutions would be appreciated. I can get logs in a bit, I was pressed for time earlier, and I'm not at that computer now. I looked at the system logs quickly and it just showed that compiz was dying and restarting too quickly (before uninstalling the 7950 drivers)

I'd prefer not to boot up with both cards in until I can figure out why they're heating up so much :/

---

### Post by gordintoronto on 2013-03-04
I have not used KVM, so this might be incorrect or irrelevant: some VMs include a virtual video adapter, which is not related to the actual hardware in the computer.

Both cards can consume a lot of energy, 151 and 200 watts respectively. If your computer case doesn't have excellent airflow, that means they will get quite hot. I use Conky to see the actual temperature of my graphics card, but it's an Nvidia, so I don't know how to use it with AMD cards.

In short, I don't think two graphics cards are useful for what you want to do.

---

### Post by ManamiVixen on 2013-03-04
Linux, specifically X is unable to handle more than one card at a time. You'll have to pull one out. Cause at the moment, technolgy like Crossfire is unavailible. Also X can't switch on the fly like that without a complete logout and relogin.

---

### Post by QIII on 2013-03-04
> **ManamiVixen said:**
> Linux, specifically X is unable to handle more than one card at a time. You'll have to pull one out. Cause at the moment, technolgy like Crossfire is unavailible. Also X can't switch on the fly like that without a complete logout and relogin.

This is incorrect.  I am typing right now from a rig with two ATI cards.  They are, however, identical.

There are a few things that might be problematic:

1.  It could be that the HD 7000 and HD 5000 series cards do not play well together.

2.  When installing the driver, it is necessary to initialize all adapters

```
sudo amdconfig --initial --adapter=all
```

3.  You may have installed the fglrx-updates driver if you installed from the repo.  This is more often prone to failure than success.  I recommend only installing fglrx.

---

### Post by ManamiVixen on 2013-03-04
Huh, I didn't know two cards could work now. As long as they are the same.

---

### Post by llemes4011 on 2013-03-04
You bring up a couple of good points that I guess I didn't hit on in my post. 

> **gordintoronto said:**
> I have not used KVM, so this might be incorrect or irrelevant: some VMs include a virtual video adapter, which is not related to the actual hardware in the computer.

They do, however I'm looking to use PCI passthrough to pass the better of the two to my windows VM so I don't have to reboot to get native performance (for gaming, rendering, etc). The virtual adapter is not good enough.

> **gordintoronto said:**
> Both cards can consume a lot of energy, 151 and 200 watts respectively. If your computer case doesn't have excellent airflow, that means they will get quite hot. I use Conky to see the actual temperature of my graphics card, but it's an Nvidia, so I don't know how to use it with AMD cards.

True, but I have a 750 Watt PSU, so I'm not worried about that. The air flow is decent, and normal temps for both cards (when used individually) are fairly normal (I've never had issues). Additionally, they heat up to extreme temperatures almost instantly upon booting the computer. 

> **gordintoronto said:**
> In short, I don't think two graphics cards are useful for what you want to do.
If I could get away with one, I would. I don't want to deal with dual booting, and there's no video output port of any kind on my mobo, and I can't pass the graphics card off to KVM unless it's not in use. If it's not in use, I can't use it to display things, and I can't use the computer :/

> **QIII said:**
> This is incorrect. I am typing right now from a rig with two ATI cards. They are, however, identical.

There are a few things that might be problematic:

1. It could be that the HD 7000 and HD 5000 series cards do not play well together.
2. When installing the driver, it is necessary to initialize all adapters
```
sudo amdconfig --initial --adapter=all
```
3. You may have installed the fglrx-updates driver if you installed from the repo. This is more often prone to failure than success. I recommend only installing fglrx.

Even without drivers installed the computer refused to complete the boot cycle. It locked up after grub, and before I was able to get to a logon screen (Even by Cntl+Alt+F1, which I use on a daily basis)

---

