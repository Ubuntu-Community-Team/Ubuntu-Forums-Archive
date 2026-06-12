---
title: "Can't load module speedstep-smi ?!"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by eClaW on 2006-07-26
Hi guys,

I'm desperately trying to get **Speedstep** to work but after 2 days of trying and reading I still had no luck (this is my first Linux install so i guess there's more reading and trying ahead ;)).
I have an IBM T22 which DOES support SpeedStep, strangely enough it's freaking hard to convince Linux of it!

After some research I followed the instructions from [this]("http://www.thinkwiki.org/wiki/How_to_get_SpeedStep_working_on_Coppermine-piix4-smi_based_ThinkPads") Link but no luck:

```
CONFIG_X86_SPEEDSTEP_RELAXED_CHECK = y
sudo modprobe speedstep-lib relaxed_check=1
sudo modprobe speedstep-smi
FATAL: Error inserting speedstep_smi (/lib/modules/2.6.15-23-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-smi.ko): No such device
```

[Here]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35044") are even more ideas on this topic but nothing that worked for my T22.
I guess the main idea is the option "**CONFIG_X86_SPEEDSTEP_RELAXED_CHECK=y**". But *where* do you enter it? In the console or in some config file? Someone pointed out it has to be entered in the kernel config file. If so, where do I find it?

I'm running *APM*, not *ACPI* don't know if that's an issue. Oh, and what's the deal with *powernowd* and *cpufreqd*? Which one should be used?

Thanks in advance for any ideas!

---

### Post by janga on 2006-08-05
I had the same problem with my Toshiba SP4600. But i solved it.

1.
```
sudo gedit /etc/modules
```
add this line:
> speedstep-lib

2.
```
sudo gedit /etc/modprobe.d/speedstep-lib.modprobe
```
insert this line:
> options speedstep-lib relaxed_check=1

3. restart.

By the way, i did this with powersaved NOT with powernowd.

---

### Post by isharra on 2006-08-05
> **eClaW said:**
> "**CONFIG_X86_SPEEDSTEP_RELAXED_CHECK=y**". But *where* do you enter it?
It's a kernel configuration option which is already enabled in the dapper kernels. So you don't have to change anything.

I suspect your real problem is that you have been trying these suggestions when speedstep-lib is already loaded into memory (it loads by default) so the option given in the modprobe line never takes effect. 'lsmod | grep speedstep' to verify if it's loaded. If it is then 'sudo rmmod speedstep-lib' first to remove it.

rofl, janga answered while I was typing this reply.  Those steps match what I did to have it work on every boot.

Note: it did affect my suspend capability.

---

