---
title: "Burnt fingers on my Centrino (Dothan)"
date: 2004-12-12
forum: Hardware &amp; Laptops
---

### Post by markus on 2004-12-12
Hi,
About two weeks ago I installed Ubuntu on my laptop, to make the switch from Windowz. The only problem that stops me from making the jump is the temp of my centrino. I have acpi installed but it seems not to detect centrino (Dothan) very well, speedstep features aren't being used and that is making my laptop really hot.

In win the temp don't raise above 40ºC while on ubuntu it's at 70ºC with fan on (with it's anoying sound...). I've tried to get the speedstep run properly but it seems impossible, all tries get the same from /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.50GHz
stepping        : 6
cpu MHz         : 1496.295
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe tm2 est
bogomips        : 2973.69

The speed at it's maximum. Acpi is running. I also have tried cpudyn and powernow but none make any change...

I've read in laptop-mode man pages that there's a file in /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies, but cpufreq dir doesn't exist, does it mean that scaling is not detected?

I also have seen that there was a problem detecting scaling on Dothan by kernel, may this be the problem?

I'm new at linux, and I'm a little lost, any help would be really apreciated, ask for anything you need.

Thanks!  :-D

---

### Post by dave_euser on 2004-12-28
[QUOTE=markus]Hi,
About two weeks ago I installed Ubuntu on my laptop, to make the switch from Windowz. The only problem that stops me from making the jump is the temp of my centrino. I have acpi installed but it seems not to detect centrino (Dothan) very well, speedstep features aren't being used and that is making my laptop really hot.

In win the temp don't raise above 40ºC while on ubuntu it's at 70ºC with fan on (with it's anoying sound...). I've tried to get the speedstep run properly but it seems impossible, all tries get the same from /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.50GHz
stepping        : 6
cpu MHz         : 1496.295
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe tm2 est
bogomips        : 2973.69

The speed at it's maximum. Acpi is running. I also have tried cpudyn and powernow but none make any change...

I've read in laptop-mode man pages that there's a file in /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies, but cpufreq dir doesn't exist, does it mean that scaling is not detected?

I also have seen that there was a problem detecting scaling on Dothan by kernel, may this be the problem?

I'm new at linux, and I'm a little lost, any help would be really apreciated, ask for anything you need.

Thanks!  :-D[/QUOTE]
 take a look at my post in this thread: [http://www.ubuntuforums.org/showpost.php?p=39711&postcount=5](http://www.ubuntuforums.org/showpost.php?p=39711&postcount=5)

should help you out....you'll probably need the speedstep_centrino module installed....then restart powernowd, should start modulating your clock frequency...

---

### Post by LB06 on 2004-12-28
[QUOTE=dave_euser]take a look at my post in this thread: [http://www.ubuntuforums.org/showpost.php?p=39711&postcount=5](http://www.ubuntuforums.org/showpost.php?p=39711&postcount=5)

should help you out....you'll probably need the speedstep_centrino module installed....then restart powernowd, should start modulating your clock frequency...[/QUOTE]
I can't get this module to load. It says no such device or device busy, depending on whether I try to load it before or after acpi, respectively. I'm sure that I have a Pentium M715 1,5Ghz Dothan though.

---

### Post by LB06 on 2004-12-28
Btw you probably can get it to run @600MHz by loading the modules acpi cpufreq-powersave (and possibly some other cpufreq-* modules).

---

### Post by dave_euser on 2004-12-29
[QUOTE=LB06]I can't get this module to load. It says no such device or device busy, depending on whether I try to load it before or after acpi, respectively. I'm sure that I have a Pentium M715 1,5Ghz Dothan though.[/QUOTE]


Can you post the output of lsmod and then dmesg after you attempt to load the centrino driver?

---

### Post by LB06 on 2004-12-30
```

luk@travelmate:~ $ sudo modprobe speedstep-centrino
Password:
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.8.1-4-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Device or resource busy
luk@travelmate:~ $ lsmod
Module                  Size  Used by
i830                   76004  3
acpi                    5996  0
proc_intf               3776  0
cpufreq_powersave       1728  0
cpufreq_userspace       5240  2
freq_table              4196  1 acpi
ds                     18436  2
button                  6584  0
ac                      4812  0
battery                 9388  0
ipv6                  257028  8
af_packet              22088  2
ohci1394               34884  0
ieee1394              108408  1 ohci1394
yenta_socket           20992  0
pcmcia_core            68404  2 ds,yenta_socket
ipw2200               118252  0
firmware_class         10016  1 ipw2200
ieee80211              23524  1 ipw2200
ieee80211_crypt         5608  1 ieee80211
b44                    21476  0
mii                     5056  1 b44
snd_intel8x0m          19656  3
snd_intel8x0           35468  5
snd_ac97_codec         67844  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            52968  1
snd_mixer_oss          19456  5 snd_pcm_oss
snd_pcm                95140  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              24900  1 snd_pcm
snd_page_alloc         11432  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4608  1 snd_intel8x0
snd_mpu401_uart         7776  1 snd_intel8x0
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8040  1 snd_rawmidi
snd                    55300  16 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10112  6 snd
pciehp                 96108  0
shpchp                 99340  0
pci_hotplug            33680  2 pciehp,shpchp
ehci_hcd               30756  0
usbhid                 31392  0
uhci_hcd               31952  0
usbcore               115684  5 ehci_hcd,usbhid,uhci_hcd
intel_agp              22112  1
agpgart                33640  4 intel_agp
pcspkr                  3592  0
rtc                    12536  0
nls_iso8859_1           4032  1
nls_cp437               5696  1
vfat                   14304  1
fat                    45824  1 vfat
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
parport_pc             34752  0
lp                     10724  0
parport                40712  2 parport_pc,lp
ide_cd                 41572  0
cdrom                  39392  1 ide_cd
joydev                  9728  0
evdev                   9440  1
tsdev                   7232  0
mousedev               10220  1
psmouse                19720  0
reiserfs              240880  1
ext2                   69960  1
ext3                  123880  0
jbd                    60824  1 ext3
mbcache                 9092  2 ext2,ext3
ide_generic             1408  0
ide_disk               18752  5
piix                   13088  1
ide_core              136120  4 ide_cd,ide_generic,ide_disk,piix
unix                   28304  910
fan                     3980  0
thermal                12976  0
processor              17392  2 acpi,thermal
fbcon                  31172  71
font                    8352  1 fbcon
vesafb                  6560  1
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb

luk@travelmate:~ $ dmesg |grep -i cpufreq
cpufreq: CPU0 - ACPI performance management activated.
cpufreq:  P0: 1600 MHz, 24000 mW, 10 uS
cpufreq: *P1: 1400 MHz, 20000 mW, 10 uS
cpufreq:  P2: 1200 MHz, 18000 mW, 10 uS
cpufreq:  P3: 800 MHz, 16000 mW, 10 uS
cpufreq:  P4: 600 MHz, 12000 mW, 10 uS

luk@travelmate:~ $ dmesg |grep -i acpi
 BIOS-e820: 000000001dee0000 - 000000001deec000 (ACPI data)
 BIOS-e820: 000000001deec000 - 000000001df00000 (ACPI NVS)
ACPI: RSDP (v000 ACER                                  ) @ 0x000f62e0
ACPI: RSDT (v001 ACER   Kestrel  0x20020806  LTP 0x00000000) @ 0x1dee66d8
ACPI: FADT (v001 ACER   Kestrel  0x20020806 PTL  0x00000050) @ 0x1deebf2c
ACPI: HPET (v001 ACER   Kestrel  0x20020806 PTL  0x00000000) @ 0x1deebfa0
ACPI: BOOT (v001 ACER   Kestrel  0x20020806  LTP 0x00000001) @ 0x1deebfd8
ACPI: DSDT (v001 ACER   Kestrel  0x20020806 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
ACPI: HPET id: 0x8086a201 base: 0x0
ACPI: IRQ9 SCI: Edge set to Level Trigger.
ACPI: Subsystem revision 20040816
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
ACPI: Embedded Controller [EC0] (gpe 29)
ACPI: Power Resource [PFN0] (off)
ACPI: Power Resource [PFN1] (off)
PCI: Using ACPI for IRQ routing
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1f.3[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:06.2[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:06.3[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: (supports S0 S3 S4 S5)
ACPI wakeup devices:
ACPI: Processor [CPU0] (supports C1 C2 C3, 8 throttling states)
ACPI: Thermal Zone [THRM] (38 C)
ACPI: Fan [FAN0] (off)
ACPI: Fan [FAN1] (off)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 6 (level, low) -> IRQ 6
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:06.0[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:02:06.2[A] -> GSI 10 (level, low) -> IRQ 10
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ACPI: Sleep Button (CM) [SLPB]
cpufreq: CPU0 - ACPI performance management activated.




```

---

### Post by dave_euser on 2004-12-30
OK, it looks like you're running kernel 2.6.8 - if you check out the changelog in 2.6.9, there's this comment:

```
<davej@redhat.com>
	[CPUFREQ] new Dothan variant for speedstep-centrino
	
	Add support for new Dothan variant (CPUID 0x6d6) to speedstep-centrino.
	Noted to be missing and tested by Athul Acharya.
	
	Signed-off-by: Dominik Brodowski <linux@brodo.de>
	Signed-off-by: Dave Jones <davej@redhat.com>


```

I'm not sure if 2.6.9 is available yet - I'm running Hoary and it is in, so you'll have to check if you can see it from synaptic...besides the above patch, there is a whole wack of other related to Dothan variants of the centrino....

---

### Post by LB06 on 2004-12-31
I've already tried Hoary a few days ago, but it didn't work with 2.6.9 either. :sad:

---

### Post by snop on 2004-12-31
Hi,

Same problem here. I can't get speedstep_centrino module to load:

sudo modprobe speedstep_centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.9-1-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

I own an Acer travelmate 4001Wlmi that uses a 1.5Ghz Dothan. I believed that it's a common processor and that it should'nt be that hard to get it working (specially when using latest kernels).

I'm using latest kernel from Hoary and here's my /proc/cpuinfo:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.50GHz
stepping        : 6
cpu MHz         : 1498.791
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflu
sh dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 2973.69

It works at 1.5 all the time which rises its temperature (and this fires the fan).

Any help would be much appreciated.

Thanks.

SnOp

---

### Post by dave_euser on 2004-12-31
Maybe one of the devs can help here, or someone more familiar with the kernel than I am....digging through the code for the speedstep-centrino module, it looks like everything should work - your cpu is providing model, family and stepping info that matches a known value, ACPI is picking up the available clock speeds, so everything *should* work....so I'm out of ideas....anyone else out there?

Maybe one of you would like to try compiling 2.6.10 by hand and see if the few minor centrino-related patches work.....

good luck, and happy new years!

---

### Post by LB06 on 2004-12-31
Hmm I've tried several other distro's, such as SuSE 9.2 and Arch current, but none of them worked. The best I can get is a more generic way to save power by using generic acpi stuff (I think). It might not be as efficient as the centrino module however.

---

### Post by snop on 2004-12-31
Hi,

I reported the bug:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=5103](http://bugzilla.ubuntu.com/show_bug.cgi?id=5103)

It's really annoying to have the fan spinning most of the time... (and no battery support because of smart batteries...)

SnOp

PD: Do you know if there are any plans to include 2.6.10 in hoary anytime soon ?

---

### Post by xhaker on 2005-01-06
2.6.10 is already in hoary
believe me when i say. still the same problem.

---

### Post by snop on 2005-01-06
Hi,

I also tried 2.6.10 and the problem persists. I reported the bug to Ubuntu developers and they have been really fast answering and seem very kind people. I want to thank Ubuntu developers for his wonderfull job.

SnOp

PD: As I posted before you can follow what's going on checking this bug entry [https://bugzilla.ubuntu.com/show_bug.cgi?id=5103](https://bugzilla.ubuntu.com/show_bug.cgi?id=5103)

---

### Post by xhaker on 2005-01-07
thank you for filling the bug entry :) i even tryed rebuild the kernel but no luck

---

### Post by snop on 2005-01-19
Hi,

I've been able to enable frequency scaling. This guy pointed to the solution:
[http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/acpi/speedstep.html](http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/acpi/speedstep.html)

I just added this to /etc/init.d/local:
modprobe acpi_cpufreq

Then when restarting powernowd (sudo /etc/init.d/powernowd restart) I had frequency scaling!

This makes my laptop stay cooler.

Also, I you own a Travelmate 4000 laptop series check the link I posted about this guy. He did a great job installing Fedora.

Bye

PD: Smartbattery support is coming...

---

### Post by jerome bettis on 2005-01-19
i can't really help you here, but i highly recommend that you fork over the $30 and pick up one of these:
[IMG]http://www.targus.com/us/product_images/PA248U_accessories_b.jpg[/IMG] 
[http://www.targus.com/us/product_details.asp?sku=PA248U](http://www.targus.com/us/product_details.asp?sku=PA248U)

my laptop stays almost cool to the touch with a 7200 rpm hard drive.  usually i leave it on when plugged in, and switch it on and off when i'm on battery.

cpu freq worked out of the box for me.  i'm sure you'll get it working shortly.  good luck

---

### Post by LB06 on 2005-01-19
[QUOTE=snop]PD: Smartbattery support is coming...[/QUOTE]
Do you have any source for this? Not that I won't take your word for it, but I just want to get some details (esp. when).

The battery part is the only piece of hardware in my laptop that doesn't function properly. Everything else functions as it should (although I'm using a more generic way to speedstep than speedstep-centrino). I am really eagerly awaiting this. Will it be in 2.6.11?

---

### Post by snop on 2005-01-20
> 
Do you have any source for this? Not that I won't take your word for it, but I just want to get some details (esp. when).

Sure. You can check ACPI mailing list archive ([http://sourceforge.net/mailarchive/forum.php?forum=acpi-devel](http://sourceforge.net/mailarchive/forum.php?forum=acpi-devel)). There have been lots of threads regarding smart batteries lately. You can even read your battery with some patches they provide (but still they need some work to integrate with the common battery apps that read /sys/.../BAT0 and this kind kind of stuff).

An intersting thread might be this:
[http://sourceforge.net/mailarchive/forum.php?thread_id=6354144&forum_id=6102](http://sourceforge.net/mailarchive/forum.php?thread_id=6354144&forum_id=6102)

> Will it be in 2.6.11?
Let's have faith on acpi developers... But I believe that we won't see this until 2.6.12.

Edit:
Check this:
[http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/acpi/battery.html](http://www.squirrel.nl/people/jvromans/articles/TM4001WLMi/acpi/battery.html)

It seems there's already support for /proc/acpi/battery! I guess we will see all this stuff really soon.

Bye

SnOp

---

### Post by Most1064 on 2007-05-15
> **dave_euser said:**
> take a look at my post in this thread: [http://www.ubuntuforums.org/showpost.php?p=39711&amp;postcount=5](http://www.ubuntuforums.org/showpost.php?p=39711&amp;postcount=5)

should help you out....you'll probably need the speedstep_centrino module installed....then restart powernowd, should start modulating your clock frequency...


[caffeine plants Cash Advance Google food science](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

