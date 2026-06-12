---
title: "Ubuntu with Ryzen 5 4500U / Renoir"
date: 2022-07-03
forum: Hardware
---

### Post by dave72 on 2022-07-03
Can anyone help with a graphics issue which is driving me mad, and I've not had the like of in many years?

I got a HP Probook 445 G7 with a Ryzen 5 4500U integrated GPU. This is a really nice laptop and I'm impressed with the graphics output. However it only ever works on the first boot after a change.

Hardware spec:
```

$ lwhw
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 15GiB
     *-cpu
          product: AMD Ryzen 5 4500U with Radeon Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 23.96.1
          size: 1397MHz
          capacity: 2375MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pd
pe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx 
f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx 
cpb cat_l3 cdp_l3 hw_pstate ssbd mba ibrs ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 cqm rdt_a rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves c
qm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local clzero irperf xsaveerptr rdpru wbnoinvd cppc arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassis
ts pausefilter pfthreshold avic v_vmsave_vmload vgif v_spec_ctrl umip rdpid overflow_recov succor smca cpufreq
          configuration: microcode=140509446
...

$ lspci | grep VGA
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Renoir (rev c3)

$ dmesg | head
[    0.000000] Linux version 5.15.0-40-generic (buildd@lcy02-amd64-047) (gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #43-Ubuntu SMP Wed Ju
n 15 12:54:21 UTC 2022 (Ubuntu 5.15.0-40.43-generic 5.15.35)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.15.0-40-generic root=UUID=bd0c6dc3-cdbb-4c64-9644-c91bfac3d1b2 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Hygon HygonGenuine
[    0.000000]   Centaur CentaurHauls


```

On boot it finds the journaled file system and then hangs with a black screen, forcing a 5s power button hold to reboot. If I go into the advanced options, I can start it in graphics safe mode at low resolution and can't use the external monitor. To enable the Ryzen support I did add the hwe drivers:
```

dpkg --list | grep hwe
ii  linux-generic-hwe-22.04-edge          5.15.0.40.42                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-generic-hwe-22.04-edge  5.15.0.40.42                            amd64        Generic Linux kernel headers
ii  linux-image-generic-hwe-22.04-edge    5.15.0.40.42                            amd64        Generic Linux kernel image

```

On doing so, it boots, graphics up, seems to be performing well, high resolution, both monitors, all good, problem solved. Until I reboot and then it fails again. Back into safe mode, remove the hwe packages, reboot back into safe mode, add them again, reboot and I'm back up and running with great graphics support.

The support and compatability is clearly there. Why would I only get one boot out of these packages? Anyone know a way to make the current graphics settings stick through a reboot?

---

### Post by kurt18947 on 2022-07-04
I had an AMD processor with integrated graphics. It was a real problem with Ubuntu 18.04. One thing that helped was to upgrade to the latest BIOS. Ubuntu 20.04 was much friendlier to Ryzen APUs than 18.04 but I'm surprised you're having problems with 22.04. I see you're using the hwe kernel. Was that installed by default or did you add it? I wouldn't think 22.04 would need the hwe kernel to work with Ryzen APUs. I'm running a Ryzen 2600X on this machine with a separate graphics card (AMD HD7450) so I'm not a lot of help there.

---

### Post by dave72 on 2022-07-12
Solved it in the end. I had legacy bios mode set. I had changed to that when I was having problems with USB boot.

Why it worked sometimes and not others, I've no idea. But, it is now booting reliably.

---

