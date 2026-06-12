---
title: "How can I apply speedstep patch?"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by Bicet on 2005-03-30
As in Title, I need it deperately, cause I have a dothan and I'm able to vary the speed  only between 600 and 1600 mHZ, but I know that there's a Kernel Patch, but I don't remember where I read about it...

---

### Post by alastair on 2005-03-31
Explain :

Where is this patch?
What references have you seen for this?
How do you know you need it?
Have you tried "powernowd" (installed by default - see : man powernowd)

---

### Post by Bicet on 2005-03-31
[QUOTE=alastair]Explain :

Where is this patch?
What references have you seen for this?
How do you know you need it?
Have you tried "powernowd" (installed by default - see : man powernowd)[/QUOTE]
 i read in this forum about the patch, i t was formerly for 2.6.10 kernel of Fedora and it supports speedstep_centrino.
I know that I need it cause my cpu change frequencies in a non modular way (minimum&maximum anything else)like it does with p4_mod_clock (form 200Mhz to 1600Mhz).
I think that's all.

---

### Post by alastair on 2005-03-31
I'm running latest Hoary v5 on a thinkpad t40p (centrino).

I have (via "lsmod") :

speedstep_centrino   7892  1
processor    22708  2 speedstep_centrino,thermal

I'm just using "powernowd" (and no custom config) - so speedstep_centrino is loaded here.

In my /var/log/syslog, I see :

ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU] (supports 8 throttling states)
ACPI: Thermal Zone [THM0] (29 C)

Do you have something different in your syslog? 

uname -r = 2.6.10-4-386

---

### Post by Bicet on 2005-04-01
[QUOTE=alastair]I'm running latest Hoary v5 on a thinkpad t40p (centrino).

I have (via "lsmod") :

speedstep_centrino   7892  1
processor    22708  2 speedstep_centrino,thermal

I'm just using "powernowd" (and no custom config) - so speedstep_centrino is loaded here.

In my /var/log/syslog, I see :

ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU] (supports 8 throttling states)
ACPI: Thermal Zone [THM0] (29 C)

Do you have something different in your syslog? 

uname -r = 2.6.10-4-386[/QUOTE]
 This is my lsmod 

```

acpi_cpufreq            6052  0
speedstep_lib           4068  0
proc_intf               4004  0
cpufreq_powersave       1632  0
cpufreq_userspace       4348  1
cpufreq_ondemand        6300  0
freq_table              4036  1 acpi_cpufreq
pcmcia                 22692  2
video                  15940  0
battery                 9988  0
ipt_TCPMSS              4352  1
ipt_tcpmss              2240  1
iptable_filter          3616  1
ip_tables              19136  3 ipt_TCPMSS,ipt_tcpmss,iptable_filter
container               4320  0
button                  6480  0
pcc_acpi               11008  0
sony_acpi               5928  0
ac                      4676  0
ipv6                  265984  11
af_packet              22504  2
pppoe                  14528  2
pppox                   3688  1 pppoe
ppp_generic            30356  6 pppoe,pppox
slhc                    7456  1 ppp_generic
ohci1394               35332  0
yenta_socket           22048  0
pcmcia_core            59936  2 pcmcia,yenta_socket
8139too                26432  0
8139cp                 20896  0
mii                     4960  2 8139too,8139cp
ipw2200                74412  0
firmware_class         10176  1 ipw2200
ieee80211              23844  1 ipw2200
ieee80211_crypt         5736  1 ieee80211
snd_intel8x0           33280  4
snd_ac97_codec         77088  1 snd_intel8x0
snd_pcm_oss            54212  0
snd_mixer_oss          20320  3 snd_pcm_oss
snd_pcm                98280  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25828  2 snd_pcm
snd                    56900  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  3 snd
snd_page_alloc          9956  2 snd_intel8x0,snd_pcm
i2c_i801                8492  0
i2c_core               22768  1 i2c_i801
ehci_hcd               33732  0
usbhid                 32800  0
uhci_hcd               34000  0
usbcore               122552  4 ehci_hcd,usbhid,uhci_hcd
pci_hotplug            34480  0
intel_agp              22652  1
agpgart                34600  1 intel_agp
pcspkr                  3496  0
rtc                    12696  0
nls_utf8                1952  2
ntfs                  112272  2
md                     48720  0
dm_mod                 62204  1
capability              4648  0
commoncap               7872  1 capability
fglrx                 237088  9
tsdev                   7680  0
evdev                   9536  1
sr_mod                 17636  0
joydev                  9920  0
sbp2                   24360  0
scsi_mod              130304  2 sr_mod,sbp2
ieee1394              111448  2 ohci1394,sbp2
psmouse                21992  0
mousedev               11608  1
parport_pc             37860  0
lp                     11656  0
parport                37800  2 parport_pc,lp
ide_cd                 42756  0
cdrom                  41500  2 sr_mod,ide_cd
reiserfs              270864  1
ext2                   68520  0
ext3                  141000  0
jbd                    62136  1 ext3
mbcache                 8612  2 ext2,ext3
ide_generic             1312  0
ide_disk               21056  5
piix                   10628  1
ide_core              133068  4 ide_cd,ide_generic,ide_disk,piix
unix                   28884  985
thermal                13288  0
processor              22420  2 acpi_cpufreq,thermal
fan                     4388  0
fbcon                  38592  71
font                    8160  1 fbcon
bitblit                 5632  1 fbcon
vesafb                  6788  1
cfbcopyarea             3968  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3616  1 vesafb

```

This is my /var/log/syslog

ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)

speedstep-centrino: invalid ACPI data
speedstep-centrino: no table support for CPU model "Intel(R) Pentium(R) M processor 1.60GHz"

if I try to modprobe speedstep_centrino I got back this error
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.10-5-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Operation not permitted

---

### Post by alastair on 2005-04-01
[QUOTE=Bicet]
speedstep-centrino: invalid ACPI data
speedstep-centrino: no table support for CPU model "Intel(R) Pentium(R) M processor 1.60GHz"
[/QUOTE]

This looks bad. It /looks/ like there's something wrong with either your ACPI data table, or Linux ACPI code. It /might/ be worth looking to see if there is a BIOS update you could apply, and see if the ACPI data is fixed or .... do some web research on your computer model (e.g. search google) and see if others have this problem e.g.

google for : "speedstep-centrino: no table support for CPU model"

It might be that you need to use a different "speedstep" module. Powernowd tries to figure this out (see : /usr/share/powernowd/cpufreq-detect.sh) but might be wrong.

---

### Post by alastair on 2005-04-01
On the other hand .... I find this :

[http://localhost.ruhr.de/~stefan/acerTM292/](http://localhost.ruhr.de/~stefan/acerTM292/)

Referencing this :

[http://thread.gmane.org/gmane.linux.kernel.cpufreq/1999](http://thread.gmane.org/gmane.linux.kernel.cpufreq/1999)

There's a patch against kernel 2.6.8 there, which /might/ be straightforward to apply to 2.6.10 (or whatever you are running). This means you need to grab the kernel sources, see if the patch applies and see if it builds ...

---

### Post by Bicet on 2005-04-02
[QUOTE=alastair]On the other hand .... I find this :

[http://localhost.ruhr.de/~stefan/acerTM292/](http://localhost.ruhr.de/~stefan/acerTM292/)

Referencing this :

[http://thread.gmane.org/gmane.linux.kernel.cpufreq/1999](http://thread.gmane.org/gmane.linux.kernel.cpufreq/1999)

There's a patch against kernel 2.6.8 there, which /might/ be straightforward to apply to 2.6.10 (or whatever you are running). This means you need to grab the kernel sources, see if the patch applies and see if it builds ...[/QUOTE]
 Thnx a lot I will give it a try ;)

---

### Post by Bicet on 2005-04-02
It works like a charm, and also my fan is not speeding up for nothing ;) 
You don't know how happy you make me 
:))

---

