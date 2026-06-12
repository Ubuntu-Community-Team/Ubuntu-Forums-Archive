---
title: "How do I tell if speedstep is working?"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by gannon on 2006-11-07
Anyone know how to get it working right? (If it isn't which it doesn't seem to be)

uname -a
```
Linux desktop 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
```

cat /proc/cpuinfo 
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 2.60GHz
stepping        : 9
cpu MHz         : 1200.215
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr 
sse sse2 ss ht tm pbe up cid xtpr
bogomips        : 2403.18
```


lsmod 
```
Module                  Size  Used by
binfmt_misc            11784  1 
rfcomm                 38936  0 
hidp                   32000  2 
l2cap                  23300  10 rfcomm,hidp
bluetooth              48996  5 rfcomm,hidp,l2cap
cpufreq_ondemand        6944  0 
i915                   20608  2 
drm                    72468  3 i915
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
ipv6                  257632  8 
af_packet              21768  2 
dm_mod                 60088  3 
md_mod                 78740  0 
lp                     11972  0 
8139cp                 22528  0 
8139too                27136  0 
mii                     6016  2 8139cp,8139too
tsdev                   8256  0 
serio_raw               7300  0 
evdev                  10496  1 
snd_mpu401              8616  0 
snd_mpu401_uart         8704  1 snd_mpu401
snd_rawmidi            25600  1 snd_mpu401_uart
snd_seq_device          8972  1 snd_rawmidi
psmouse                40072  0 
snd_intel8x0           33436  1 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  12 
snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
rtc                    12596  0 
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
i2c_i810                5380  0 
analog                 11680  0 
i2c_algo_bit            9480  1 i2c_i810
pcspkr                  3072  0 
gameport               15368  1 analog
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
intel_agp              25116  1 
agpgart                33456  3 drm,intel_agp
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
i2c_core               22288  2 i2c_ec,i2c_algo_bit
ext3                  138632  1 
jbd                    55700  1 ext3
ehci_hcd               32520  0 
uhci_hcd               23176  0 
usbcore               130304  3 ehci_hcd,uhci_hcd
ide_generic             1536  0 
ide_cd                 32416  0 
cdrom                  37792  1 ide_cd
ide_disk               17664  3 
piix                   10628  1 
generic                 4868  0 
thermal                14600  0 
processor              26028  1 thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability
```

---

### Post by daller on 2006-11-07
Isn't it working?

The max CPU MHz is 2600!

cpuinfo tells you that it runs at 1200 MHz...

I would call that speedstepping!

Does it increase if you put load on the pc?

---

### Post by gannon on 2006-11-07
I opened 2 videos, nautilus, firefox, system monitor, terminal and had gimp render the IFS fractal and the cpu shot up to 100% use with no change to the cpu speed whenever I read /proc/cpuinfo

---

### Post by daller on 2006-11-08
Hmm...

What release are you running on?

Maybe try installing cpufreqd

---

### Post by gannon on 2006-11-08
I was running on Dapper with no success, but now I'm running on Edgy. Also, I installed cpufreqd, but get a "No Sockets Found" output, and cpufreq-selector gives a "No Cpufreq Support" output.

---

### Post by dannyboy79 on 2006-11-08
> **gannon said:**
> uname -a
Linux desktop 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux 

Looks to me like you don't have the SMP kernel as your first choice. When I do a uname -a, this is what I get: Linux UBUNTU 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

Notice mine has 2.6.15-27-686 where yours says 2.6.17-10-386. I would look into this!

notice how mine also has "SMP PREEMPT" in it.

---

### Post by gannon on 2006-11-08
Don't think that's the issue. IIRC the SMP kernal is only for dual core/ht processors.
I'll try it out anyways though.

---

### Post by gannon on 2006-11-09
I came across this page ( [http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq) ), and here's what I get:
```
[17196122.832000] p4-clockmod: Warning: Pentium 4-M detected. The speedstep-ich or acpi cpufreq modules offer voltage scaling in addition of frequency scaling. You should use either one instead of p4-clockmod, if possible.
root@desktop:~# modprobe speedstep-ich
FATAL: Error inserting speedstep_ich (/lib/modules/2.6.17-10-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-ich.ko): No such device
```

---

### Post by nyinge on 2006-11-09
Ok.  To further complicate the problem...  How would I go about disabling the speed-step?

edit:  I'm having the issue as Gannon.  Since I have my laptop (old) plugged in most of the time, I'd appreciate that extra performance even if it's only for a sec.  :)

---

### Post by dannyboy79 on 2006-11-09
> **gannon said:**
> FATAL: Error inserting speedstep_ich (/lib/modules/2.6.17-10-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-ich.ko): **No such device**[/CODE] 

According to this your computer doesn't have a processor! HA HA. I am just playing around. I wish I could help ya, are you still using the 386 kernel or the SMP (686) kernel?

---

### Post by gannon on 2006-11-09
Well, I did an apt-get install linux-686-smp and rebooted, but I still get the same info as I did before with uname -a

---

### Post by nyinge on 2006-11-13
Hope you're still around.  I know.. it's been 3 days since your last post.  Anyway...

I found this neat little applet, EmiFreq (0.18), in which you can control your desire cpu speed style,  It's a GNOME applet.  You can get it with apt-get like the following:
```
apt-get install emifreq-applet
```

After you install it, right-click on your panel --> Add to Panel...  -->  scroll down to the bottom (its icon somehow doesn't show up for me though).  Hope that works for ya.

---

### Post by dannyboy79 on 2006-11-13
> **gannon said:**
> Well, I did an apt-get install linux-686-smp and rebooted, but I still get the same info as I did before with uname -a

well just because you installed it doesn't mean that it became your first kernel to boot to I am guessing. I forgot how I gopt my machine to boot with the smp kernel. just do some searchs within this forum, that's what I did when I wanted to utilize the hyperthreading of my cpu. good luck.

hang on, i did it for ya, check this out: [http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)

---

### Post by David Corrales on 2006-11-13
Why don't you add the graphical cpu frecuency scaling applet? Right click on the panel->Add to panel->CPU Frecuency Scaling Monitor.

---

### Post by Unicast on 2006-11-13
in /sys/devices/system/cpu/cpu0/cpufreq what are the values for scaling_max_freq and scaling_min_freq?

If scaling_max_freq = scaling_min_freq then you're never going to get your processor to scale up to 2.6Ghz. I had this problem with my laptop for ages, and it took a couple of kernel compiles and a bit of cpufreq.c hacking to sort it out. Right PITA that was!

---

### Post by Anagonda on 2006-11-18
I just upgraded my desktop processor to Pentium M.

And this is what I get:
modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.17-10-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device



I try go with this [http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq)

---

