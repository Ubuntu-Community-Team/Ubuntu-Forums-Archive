---
title: "Hard freezes"
date: 2013-05-20
forum: Hardware
---

### Post by mosteo on 2013-05-20
Hello,

I have a HP computer which used to freeze from time to time with 12.10. Now, it does so almost every night with 13.04. It rarely happens when I'm using it (three times in many months that I can remember) but it happens almost every night (this computer should be always running): when I'm back in the morning, monitor doesn't get input and nothing works: caps lock lights are stuck, SysReq+Alt commands don't work.

I see nothing suspicious in syslog or dmesg. I've tried disabling all powersave functions. When it has happened with me in front of the computer, the mouse kept working for a while, but no kernel panic or anything worth googling happened. I couldn't switch to console with Ctrl+Alt+F1.

I suspect a hardware component is the culprit, or some combination. Sadly, I can't think of anything to do to get some information to pinpoint it, and I have no spare parts to swap in and see if that does any good.

Since opening a bug with this little information seems futile, I wanted to ask you for any pointers that could give any clues. Much appreciated!

---

### Post by TenPlus1 on 2013-05-20
What is the specification of your HP computer and are you running 32 or 64-bit Ubuntu ? also, what other software do you have installed ?

---

### Post by zero2xiii on 2013-05-20
Hay,

See my singnature for a link to a thread I opened to help us gather useful information about your system.

Also on top of that, during grub, select the memtest option and run a memory test on the RAM. Just to scratch that from the list of endless possibilities.

Cheers and good luck

---

### Post by mosteo on 2013-05-20
Hello, thanks for the quick reply!

You're right, I should have added some specs. They're next. I just tested RAM and it checks OK.

```

$ uname -a
Linux miles 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:17:37 UTC 2013 i686 i686 i686 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

```

And attached is the bulk of the report, using the commands given in the suggested thread.

---

### Post by zero2xiii on 2013-05-21
Hay,

Wow thats a lot of output, but the only thing that "jumps at me" if you will is this part:

```
LSHW OUTPUT
miles
    description: Mini Tower Computer
    product: HP Compaq 8200 Elite SFF PC (XY146ET#ABE)
    vendor: Hewlett-Packard
    serial: CZC13832LR[B]
    width: 32 bits[/B]
    capabilities: smbios-2.7 dmi-2.7 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=4 family=103C_53307F G=D sku=XY146ET#ABE uuid=00989FC6-C9DC-E011-0000-3CD92B69165D
  *-core
       description: Motherboard
       product: 1495
       vendor: Hewlett-Packard
       physical id: 0
       serial: CZC13832LR
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: J01 v02.06
          date: 06/09/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot uefi
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          slot: SOCKET 0
          size: 3101MHz
          capacity: 3800MHz
          **width: 64 bits**
          clock: 100MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
```

But it might just be a reporting error from the hardware. Glad the memtest went okay :).

Any chance we can get the dmesg output from as quickly after a freeze as possible (after a freeze I suggest booting to a recovery console, telinit 1 or 2 should give sufficient system level access to get a dmesg log before a whole lot of the other resources are loaded).

Cheers

---

### Post by mörgæs on 2013-05-21
I don't see any errors here, just a 32 bit operative system on hardware capable of 64 bit.

---

### Post by user_of_gnomes on 2013-05-21
Did you diagnose the hard drive?

---

### Post by hansdown on 2013-05-21
Hi 
mosteo.

My intel chipset will not run unity; gpu lockups.

I was testing manjaro linux with xfce last week, and everything was fine, until I installed compiz, which unity runs on top of.

The gpu lockups were back.

My belief is, that compiz is at fault.

---

### Post by mosteo on 2013-05-22
I have run the SMART tests in the past, yes. Time to do so again just to be sure then.

Probably later in the day I'll go to this computer and with any "luck" it will have frozen, so I can get the chance to get a fresh dmesg.

---

### Post by mosteo on 2013-05-24
Today I found the computer frozen. I booted directly to recovery console and to my surprise, the latest dmesg and syslog are from three days ago, not matching the last boot date.

I was in a hurry and I haven't been able to resolve the matter. I'll try to get a clearer idea of what is the last log next time this happens.

---

