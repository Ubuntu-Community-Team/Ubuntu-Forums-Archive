---
title: "Only one CPU core detected of six available"
date: 2022-02-21
forum: Hardware
---

### Post by gnosticchemist on 2022-02-21
I was using my computer on Ubuntu and noticed that it was underperforming while I was doing basic stuff, like watching streams and using Discord
Then I decided to check my Hardware, and noticed that it was using only one CPU core for some reason, even when it reachs 100% usage it doesn't activates other cores.

How do I fix it?

[https://prnt.sc/kdn4ncMehZ12](https://prnt.sc/kdn4ncMehZ12)
[https://media.discordapp.net/attachments/733036243205750806/945338444584984646/unknown.png](https://media.discordapp.net/attachments/733036243205750806/945338444584984646/unknown.png)
[https://media.discordapp.net/attachments/733036243205750806/945338666581118996/unknown.png](https://media.discordapp.net/attachments/733036243205750806/945338666581118996/unknown.png)

---

### Post by Autodave on 2022-02-21
Did you install 32 or 64 bit Linux?

---

### Post by #&amp;thj^% on 2022-02-21
As of 18.04, 32-bit versions of Ubuntu are no longer available for download. However, the default Ubuntu desktop can be installed on any Ubuntu Flavor, most of which still provide 32-bit downloads: Downloads may also be found at the following links: The 32 bit version files end in -i386.iso.
Would need to see more please:
```
inxi -Sf --no-filter

```
Please paste back wrapped in Code tags.

---

### Post by gnosticchemist on 2022-02-22
It gives me an error because of --no-filter
```

Error 22: Unsupported option: --no-filter
Check -h for correct parameters.

```

Running without --no-filter:
```

System:    Host: gnosticChemistPC Kernel: 5.11.0-27-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 
           Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
CPU:       Topology: Single Core model: AMD Ryzen 5 3500X bits: 64 type: UP L2 cache: 512 KiB 
           Speed: 3889 MHz min/max: N/A Core speed (MHz): 1: 3889 
           Flags: 3dnowprefetch abm adx aes aperfmperf apic arat avic avx avx2 bmi1 bmi2 bpext cat_l3 cdp_l3 clflush 
           clflushopt clwb clzero cmov cmp_legacy constant_tsc cpb cpuid cqm cqm_llc cqm_mbm_local cqm_mbm_total cqm_occup_llc 
           cr8_legacy cx16 cx8 de decodeassists extapic extd_apicid f16c flushbyasid fma fpu fsgsbase fxsr fxsr_opt ht 
           hw_pstate ibpb ibs irperf lahf_lm lbrv lm mba mca mce misalignsse mmx mmxext monitor movbe msr mtrr mwaitx 
           nonstop_tsc nopl npt nrip_save nx osvw overflow_recov pae pat pausefilter pclmulqdq pdpe1gb perfctr_core 
           perfctr_llc perfctr_nb pfthreshold pge pni popcnt pse pse36 rdpid rdpru rdrand rdseed rdt_a rdtscp rep_good sep sev 
           sev_es sha_ni skinit smap smca sme smep ssbd sse sse2 sse4_1 sse4_2 sse4a ssse3 stibp succor svm svm_lock syscall 
           tce topoext tsc tsc_scale umip v_vmsave_vmload vgif vmcb_clean vme vmmcall wbnoinvd wdt xgetbv1 xsave xsavec 
           xsaveerptr xsaveopt xsaves 

```

---

### Post by gnosticchemist on 2022-02-22
Installed 64 bits, with dual boot Windows

---

### Post by #&amp;thj^% on 2022-02-22
I must say 1st time for everything, never seen anything like this before, but I love challenges.
Last nite I did come across this:
> Notes
China only retail and OEM.

This processor comes with an unlocked base clock multiplier, allowing users to set the multiplier value higher than shipped value, to facilitate better overclocking.
I will need to see your Grub setup:
```
cat /etc/default/grub
```

---

### Post by gnosticchemist on 2022-02-22
Here it is:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="menu"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER="false"

```

Maybe is relevant mention that I needed to add "acpi=off" to my Ubuntu GRUB entry, because without it freezes on boot, here's the full entry:
```

recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
insmod part_msdos
insmod ext2
set root='hd1,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  532fbfa6-626c-4489-8e57-05b22b0daa92
else
  search --no-floppy --fs-uuid --set=root 532fbfa6-626c-4489-8e57-05b22b0daa92
fi
linux    /vmlinuz-5.11.0-27-generic root=UUID=e88bdfaa-1a03-44aa-95b4-b2fb281101eb ro  quiet splash acpi=off $vt_handoff
initrd    /initrd.img-5.11.0-27-generic

```

---

### Post by #&amp;thj^% on 2022-02-22
Thanks that was quick.
When using "acpi=off", we explicitly told the kernel to disable all power management features. So that effectively disabled multi-core usage because the OS has no way to manage them.
Could you now try and remove  "acpi=off" then add
```
acpi=ht irqpoll
```
Like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=ht irqpoll quiet splash"
```
update grub, and reboot, now any difference?

---

### Post by Doug S on 2022-02-22
Are cores disabled in the BIOS? I can not read the manual for your particular motherboard as it is Brazilian Portuguese, but my ASUS motherboards BIOS's allow setting the number of active cores. There might be some message in the logs about it. see /var/log/kern.log and/or dmesg.

EDIT: I did not see the two posts done while I was typing.

---

### Post by gnosticchemist on 2022-02-22
It loads for a bit, but then freezes like before I added the acpi=off

---

### Post by #&amp;thj^% on 2022-02-22
Well dang, that would have been the easiest to use, but I got one more for you to try;
Add this:
EG:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=assign-busses apicmaintimer idle=poll reboot=cold,hard"
```
And update-grub and reboot fingers crossed.
I have no problems with mine:
```
inxi -C --no-filter
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1461 min/max: 1400/3000 cores: 1: 1873 2: 1478 3: 1397
    4: 1397 5: 1453 6: 1397 7: 1431 8: 1397 9: 1397 10: 1397 11: 1429 12: 1490

```

---

### Post by gnosticchemist on 2022-02-22
>  [COLOR=#000000]Are cores disabled in the BIOS? [/COLOR]
I doubt this is the case, the Windows installation uses the 6 cores normally

---

### Post by #&amp;thj^% on 2022-02-22
> **gnosticchemist said:**
> [/COLOR]
I doubt this is the case, the Windows installation uses the 6 cores normally

Suspense is killing me, have you tried the new kernel parms I just suggested.

---

### Post by gnosticchemist on 2022-02-22
I'm trying it now, It didn't freeze yet but it don't stop loading, its on boot screen with the Ubuntu logo spinning like 5 minutes

I did modify by Grub Customizer, it upgrades the grub when I saves it, rigth?

Edit: I restarted and it just freezes again

---

### Post by #&amp;thj^% on 2022-02-22
> **gnosticchemist said:**
> I'm trying it now, It didn't freeze yet but it don't stop loading, its on boot screen with the Ubuntu logo spinning like 5 minutes

I did modify by Grub Customizer, it upgrades the grub when I saves it, rigth?

IMHO not a fan of Grub Customizer, results like yours may result by application.

---

### Post by #&amp;thj^% on 2022-02-22
Please try with an older kernel when rebooting.

---

### Post by gnosticchemist on 2022-02-22
I manually changed and updated the grub, it just freezes too

USB Live Disks also freeze if I don't use the acpi=off

---

### Post by #&amp;thj^% on 2022-02-22
I'm at a loss here now, be sure to have good back-ups in place.
When you first installed it, were the same problems there?

---

### Post by gnosticchemist on 2022-02-22
The older kernel worked, It booted and it shows the 6 cores working
Currently working on kernel 5.11.0-27-generic with the last params posted

> 
When you first installed it, were the same problems there?

The freezing problem yes, it affects my computer since I used the Live Disk to install ubuntu, I didn't have any trouble using the same Live Disk on my Notebook
The CPU core usage I'm not sure, I suspect it was there since the first use but I didn't used many apps at once to stress the one core, but when I did then I noticed only one core was working.

---

### Post by #&amp;thj^% on 2022-02-22
> **gnosticchemist said:**
> The older kernel worked, It booted and it shows the 6 cores working
Currently working on kernel 5.11.0-27-generic with the last params posted


The freezing problem yes, it affects my computer since I used the Live Disk to install ubuntu, I didn't have any trouble using the same Live Disk on my Notebook
The CPU core usage I'm not sure, I suspect it was there since the first use but I didn't used many apps at once to stress the one core, but when I did then I noticed only one core was working.

You may have to remain on that kernel version for now.
I don't think it would hurt to file a bug against kernel 5.11.0-27-generic AMD
EDIT: that was a little vague sorry Example: ubuntu-bug <package name> and press Enter

---

