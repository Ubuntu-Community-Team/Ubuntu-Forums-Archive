---
title: "Slow boot"
date: 2014-12-25
forum: Hardware
---

### Post by -Marco on 2014-12-25
Luckily that Ubuntu was faster than Windows 8.1
I do not think it's normal that I load Ubuntu after 2 minutes flat. 2 MINUTES!
The beauty is that I have the world's fastest HDD, a Caviar Black 2 FusionDrive, and an i5.
But my notebook of 2006 with ATA HDD (that is the generation of my grandmother) loads Ubuntu 14.10 in 30 seconds maximum or less ..


I want to explain why? If no return to Windows. There is no advantage at this point to use Ubunutu (in addition to having an open source software) :mad:

---

### Post by Reha_Andrew on 2014-12-26
what exactly are you trying to ask or say?

---

### Post by -Marco on 2014-12-26
> **Reha_Andrew said:**
> what exactly are you trying to ask or say?
How can I solve this problem. Yep, it's a problem at all. It's strange that an user have a faster HDD but Ubuntu boot slow.
Is that a bug? A settings that I didn't configure?

So, please help me :)

---

### Post by mörgæs on 2014-12-26
The command
```
more /var/log/dmesg
```
shows what takes place during boot and what delays the proces. The number in [] is the time stamp.

---

### Post by -Marco on 2014-12-26
> **mörgæs said:**
> The command
```
more /var/log/dmesg
```
shows what takes place during boot and what delays the proces. The number in [] is the time stamp.
It shows me a lot of line. All the time stamp are 0.
Example: ```
[    0.000000] CPU0 microcode updated early to revision 0x1a, date = 2014-05-23[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-43-generic (buildd@tipua) (gcc version 4.8.2
 (Ubuntu 4.8.2-19ubuntu1) ) #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 (Ubuntu 3
.13.0-43.72-generic 3.13.11.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-43-generic root=UUI
D=6daf5f24-bcc0-4f80-9bd7-f9ec6b24e5e9 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b7e8efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b7e8f000-0x00000000b7e95fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b7e96000-0x00000000b8ab0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b8ab1000-0x00000000b8fbffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b8fc0000-0x00000000cbe9cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cbe9d000-0x00000000cc0a2fff] reserved
--Ancora--(2%)
```

---

### Post by mörgæs on 2014-12-26
Pushing space while the command is running gives you additional screens. 

You don't have to post the output. It was meant as a way for you to study how the system works.

---

### Post by -Marco on 2014-12-26
> **mörgæs said:**
> Pushing space while the command is running gives you additional screens. 

You don't have to post the output. It was meant as a way for you to study how the system works.
Yeah, but it's a regula check-up to boot. Nothing to report.. but Ubuntu boot slow ever.
With this command i see that my PC checks every USB port, AHCI controller, ACPI, bus ecc.. but checks slowly.
Again, i don't think it's my CPU (that's an i5-4670K) and my HDD. Other OS boot faster than Ubuntu.

P.S: I've this problem with 13.10, 14.04, Debian, centOS and 14.10! I downloaded all available drivers, microcode ecc. for my Linux machines. :'(

---

### Post by oldfred on 2014-12-26
What motherboard?
Gigabyte need IOMMU setting in UEFI. Not sure about others.

You see all the processes it goes thru, what is important for figuring out the issue, is those with long times between timestamps.

---

### Post by -Marco on 2014-12-26
> **oldfred said:**
> What motherboard?
Gigabyte need IOMMU setting in UEFI. Not sure about others.

You see all the processes it goes thru, what is important for figuring out the issue, is those with long times between timestamps.
I've **AsRock Z87 Extreme 4** (it's a UEFI BIOS, but it's setting by me a lot of time ago [no secure boot, disable some options for windows, try Other OS Settings]). I'm trying to autokill some process during the boot. ;)

I'll re-edit this post tomorrow guys

---

### Post by schragge on 2014-12-26
This will show lines in the kernel log where large delays (more than 0.3 s) occured during boot:
```

 awk -F'[][] *' '$2-ts>0.3{printf "%s\n%s\n---\n",l,$0}{ts=$2;l=$0}' /var/log/dmesg

```

---

### Post by oldfred on 2014-12-26
Asrock's have issues with the ASmedia drives. 

So make sure no drives, even DVD player are connected to the Asmedia ports.

---

### Post by mörgæs on 2014-12-26
> **schragge said:**
> This will show lines in the kernel log where large delays (more than 0.3 s) occured during boot:
```

 awk -F'[][] *' '$2-ts>0.3{printf "%s\n%s\n---\n",l,$0}{ts=$2;l=$0}' /var/log/dmesg

```

Thanks! Now incorporated into the Old Hardware thread with credit to you.

---

### Post by -Marco on 2014-12-27
> **oldfred said:**
> Asrock's have issues with the ASmedia drives. 

So make sure no drives, even DVD player are connected to the Asmedia ports.
I saw the output. So the delay of the boot, according to the kernel, is due to my Wi-Fi card (among other things having all drivers) and RC6 power state of the CPU, which strangely was killed how the process.

I can only say that the kernel does not yet support these phases of power almost new (created from Haswell generation, c. 2013).
Ok, I'm still noob in this field, and then tell me if I'm wrong. :p

Output:```
[    1.898291] usb 4-5: SerialNumber: USB2.0 Hub
[    2.400354] Switched to clocksource tsc
---
[    2.400354] Switched to clocksource tsc
[    2.909856] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
---
[    2.909856] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.893653] usb 4-5: Enable of device-initiated U1 failed.
---
[    6.894463] hub 4-5:1.0: 4 ports detected
[    8.305706] random: nonblocking pool is initialized
---
[    8.305706] random: nonblocking pool is initialized
[   10.090602] Adding 8042492k swap on /dev/sda5.  Priority:-1 extents:1 across:8042492k FS
---
[   10.090602] Adding 8042492k swap on /dev/sda5.  Priority:-1 extents:1 across:8042492k FS
[   12.824704] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
---
[   12.824704] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.451022] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
---
[   13.456088] systemd-udevd[329]: starting version 204
[   14.885812] lp: driver loaded but no devices found
---
[   14.885812] lp: driver loaded but no devices found
[   15.253192] ppdev: user-space parallel port driver
---
[   15.253192] ppdev: user-space parallel port driver
[   17.185986] video: module verification failed: signature and/or  required key missing - tainting kernel
---
[   17.860839] cfg80211: Calling CRDA to update world regulatory domain
[   18.163954] fbcon: inteldrmfb (fb0) is primary device
---
[   18.525628] ieee80211 phy0: Atheros AR5418 MAC/BB Rev:2 AR2133 RF Rev:81 mem=0xffffc90004ea0000, irq=17
[   19.324744] cfg80211: World regulatory domain updated:
---
[   19.326348] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 1800 mBm)
[   19.794132] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
---
[   19.794132] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   20.321449] init: failsafe main process (676) killed by TERM signal
---
[   20.321449] init: failsafe main process (676) killed by TERM signal
[   24.280396] audit_printk_skb: 42 callbacks suppressed
---
[   24.636917] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.347972] type=1400 audit(1419673082.115:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=987 comm="apparmor_parser"

```

---

### Post by mörgæs on 2014-12-27
Where is the problem? A boot time of 25 seconds sounds fine to me.

---

