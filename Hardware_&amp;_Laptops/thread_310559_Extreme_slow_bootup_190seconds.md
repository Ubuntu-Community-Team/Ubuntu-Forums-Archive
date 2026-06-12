---
title: "Extreme slow bootup 190seconds"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by neemz on 2006-12-01
Hi folks I was wondering if somebody could help me.

My laptop boots very slowly indeed. It is a Philips X56 (only sold in UK from PCworld) which is actually a TwinHead H12Y as far as I am aware.

If I pass in acpi=off at bootup then it boots fast yet I then don't have access to any power management.

When it hangs I get these lines

scsi subsystem initialized
acpi: pci interupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 225

Then I have to wait a few minutes and it continues on the boot process at loading USB devices.

Here is the attached image from bootchart

---

### Post by neemz on 2006-12-01
If it helps I could also provide whichever logs are relevant.

I beleive this issue is also causing my vmware server to run erratically (guest is very slow).

Please help me!

---

### Post by Thumper322 on 2006-12-01
> **neemz said:**
> If it helps I could also provide whichever logs are relevant.

I beleive this issue is also causing my vmware server to run erratically (guest is very slow).

Please help me!

Regarding VMWare... Did you install VMWare Extensions (or whatever they call it)?

---

### Post by neemz on 2006-12-02
Yes I installed vmware tools but that isn't the problem.

If I watch the clock in the guest OS it ticks 1 second every 10-30 seconds of real time!

But I just want to put this back on track cos the slow booting with the strange acpi issue is what is really annoying me (seeing as suspend resume sucks so much).

---

### Post by bbbscarter on 2006-12-02
I'm randomly getting exactly the same thing - the boot up pauses for several minutes just after the pci interrupt message. It doesn't always happen, however; often it'll boot without a problem several times in a row.

In my case this isn't running on VMWare, it's a dual-boot install on a Sony Vaio S4XP.

I'm rather new to this Linux thang, so let me know if I need to provide any more info. Any help much appreciated!

Simon.

---

### Post by neemz on 2006-12-04
Issue resolved by rolling my own kernel, 2.6.19 works a treat, bootup according to bootchart now takes 32 seconds.

---

