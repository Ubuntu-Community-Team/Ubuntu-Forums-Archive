---
title: "How-to get CPU Scaling working with Edgy on Celeron M 420 Laptop (Toshiba L35) ?"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by pentium0 on 2006-11-29
I was lucky enough to get a black friday Toshiba laptop from Worst Buy (L35-S2151), and have got most things working in Edgy.  The CPU is a Celeron M 420 1.6 GHz (detailed specs at end of post).

However, CPU scaling is not wanting to work.  I have tried all the usual steps I believe, including those in the how-to in the forums [here]("http://ubuntuforums.org/showthread.php?t=248867").  I have tried to get scaling working with both the generic and 386 versions of the 2.6.17-10.33 kernel, and even the 2.4.27-12 kernel for 686 (PPro/Celeron/etc) which can't boot and gives a "can't read filesystem" error.

modprobe speedstep-centrino
modprobe acpi-cpufreq
modprobe p4-clockmod

all give the similar error:

FATAL: Error inserting p4_clockmod (/lib/modules/2.6.17-10-generic/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko): No such device



Any tips would be appreciated!




Detailed CPU info:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
stepping        : 8
cpu MHz         : 1600.280
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe constant_tsc up pni monitor tm2 xtpr
bogomips        : 3206.74

---

### Post by patrickfromspain on 2006-11-29
quite odd.. I have a toshiba L10 with a celeron M 370 and cpu scaling works using the p4-clockmod module.

cpatrick@debian:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Celeron(R) M processor         1.50GHz
stepping        : 8
cpu MHz         : 562.500
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up
bogomips        : 2991.22


Maybe you could try dapper? Running the live cd would be enough.

Also... I've heard about Black Fridays other times, what are they? They seem to be very interesting..

---

### Post by pentium0 on 2006-11-29
That's a great idea (try dapper live CD), I'll try it right now.
What kernel does Edgy have you running?  The generic one? Or 686?

Black friday is the day after thanksgiving, called black I've heard because it put retailers back in the black financially.  This year was pretty good for laptops; my toshiba was $250 no rebates, and there were others with better specs for ~$350.  But people had to wait 8+ hrs in line of course :)

---

### Post by radeon on 2006-11-29
How the hell You want to start scaling cpu that has no speedstep? Tell me cause if u can i buy u beer. There is no way you can to this unles you have real pentium m, yonah, meron, turion. Only what you can do is to throtling and this is not equal scaling voltage or FSB, your laptop will always work on 100%.

---

### Post by pentium0 on 2006-11-29
First off, I tried the live dapper CD and CPU scaling was still a no-go.

radeon; you probably are right, but patrickfromspain says that his celeron m 370 (also listed as non-speedstep at intel.com) scales with the p4-clockmod module.

The celeron m 420 appears to be based on yonah, [here]("http://www.reghardware.co.uk/2006/04/11/yonah_celeron_ms_ship/"), but you're right, it may not have speedstep ([intel site]("http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/mobile/processors/index.htm")).  Hmm.  But I've read in forums that some people can get their Celeron-M's to scale their clockspeed by using p4-clockmod instead of the normal speedstep-centrino kernel mod.  

Is it possible that scaling exists for Celeron M's, but isn't called "speedstep"?  I hope so.  If not, I may just switch back to my trusty thinkpad R50 which is definitely speedstep, and sell this thing.  The fan is way too loud, and turns on often when not doing very much CPU load at all.

---

### Post by patrickfromspain on 2006-11-30
I have scaling through the p4-clockmod module, and it works fine ;)

I'm using edgy generic kernel. Also, since a couple of weeks I've been using debian etch: cpufreq also worked fine.

---

### Post by radeon on 2006-11-30
pentium0:

the p4-clockmod module should load but nothing than throttling will work and throttling is always on by self cpu when it is too hot. 

patrickfromspain:

what do you mean by "work", show me the FSB and core volate of this celeron m 370 when laptop is on idle. If it's working than we are milionairs :). Celeron m420 is very fast [like core solo] and cheap, if we can scale it than I will write soft for windows for program-speedstep and sell it fot 50$ :p   

I find such a thing on some forum:

> $ cpufreq-info
cpufrequtils 0.4: cpufreq-info 
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 188 MHz - 1.50 GHz
  available frequency steps: 188 MHz, 375 MHz, 563 MHz, 750 MHz, 938 MHz, 1.13 GHz, 1.31 GHz, 1.50 GHz
  available cpufreq governors: conservative, ondemand, powersave, userspace, performance
  current policy: frequency should be within 990 MHz and 1.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.50 GHz.

now ;) let see 1500*12,5%=188
188*2=376
188*3=563 so on 

and may I remind you 12,5% factor is for throttling. Now give me the data how throttling save battery or lowing fan noise ... as far as i know the profit is like couple of % or in some case there is now profit but only worst workin of cpu.

---

### Post by patrickfromspain on 2006-11-30
Radeon, I'll check how my cpu behaves when not scaled down, as I'm not sure..

Also, what do you mean by 12,5% is the throttling factor?

EDIT: seems you were right, radeon... running the cpu at 1,5Ghz doens't seem to run the system hotter than running it a 562Mhz. If the system is as hot and load as before... what the hell does this scaling? :S ;)

---

### Post by radeon on 2006-11-30
> Also, what do you mean by 12,5% is the throttling factor

as far as I know: when for instance your fan will brak and cpu ... any kind mobile or not get to high temperature like 80C then throttling is comming with help. It disable cpu power in 12,5% steps. Scaling I mean real scaling like speedstep is the lowering of FSB and voltage of core. Celeron m420 as far as I remeber is 1600MHz and 1,3V ... always, and for instance AMD Turion 2Ghz and 1,3V when do nothing or we just want to play mp3 or look web can be 800MHz, 0,9V.

The only way out:

1. get new notebook or cpu
2. use arctic silver 5 between cpu and cooler - even 4-6C advantage, but You have to open the box 
3. use cooling pad
4. if there is posibility twaek down fan rpm. 

sorry for my bad english ...

---

### Post by lowie82ph on 2006-12-03
hi,

i also have the same problem. i can't get frequency scaling work on my acer travelmate 2441 notebook, which also have a yonah based celeron m. i'm using ubuntu edgy. 

hey patrickfromspain, can you show how did you get scaling working(in step-by-step)? thanks... :p

---

### Post by mpalla on 2006-12-07
Hi,

I have a laptop with a celeron

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Celeron(R) CPU 2.80GHz
stepping	: 9
cpu MHz		: 2100.000
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
bogomips	: 5592.04
```

and right now, using Edgy, the scaling does work only for the upper freqs (2.8, 2.45, 2.1). I've just added the p4_clockmod module (without any errors). It was the same with Dapper, but after some major upgrade it did recognize and use correctly all the freqs supported by the cpu. So, I think that it should be somethink wrong in the code somewhere, or am I missing something?

```
Module                  Size  Used by
binfmt_misc            13448  1 
radeon                118816  2 
drm                    74644  3 radeon
ipv6                  272288  16 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  2 
p4_clockmod             7108  0 
speedstep_lib           5764  1 p4_clockmod
freq_table              6048  2 cpufreq_stats,p4_clockmod
lp                     12964  0 
rt2500                188004  1 
pcmcia                 40380  0 
joydev                 11200  0 
tsdev                   9152  0 
psmouse                41352  0 
snd_ali5451            25356  1 
snd_ac97_codec         97696  1 snd_ali5451
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
yenta_socket           28812  2 
usbhid                 45152  0 
serio_raw               8452  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
natsemi                30688  0 
ati_agp                10636  1 
agpgart                34888  2 drm,ati_agp
pcspkr                  4352  0 
snd_pcm                84612  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
evdev                  11392  2 
i2c_ali1535             7940  0 
i2c_ali15x3             8708  0 
i2c_core               23424  3 i2c_ec,i2c_ali1535,i2c_ali15x3
soundcore              11232  1 snd
snd_page_alloc         11400  1 snd_pcm
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
generic                 5764  0 
alim15x3               13324  0 [permanent]
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
```

---

### Post by patrickfromspain on 2006-12-07
> **lowie82ph said:**
> hi,

i also have the same problem. i can't get frequency scaling work on my acer travelmate 2441 notebook, which also have a yonah based celeron m. i'm using ubuntu edgy. 

hey patrickfromspain, can you show how did you get scaling working(in step-by-step)? thanks... :p
Yeah, for sure. Anyway, I have realized that it doesn't really do anything: the laptop doesn't really run cooler and it isn't louder without cpu scaling.

Here it goes, in a terminal do the following:

sudo modprobe p4-clockmod

then add a cpu frequency applet to a panel and you should have working cpu scaling.

---

### Post by mvephoto on 2007-03-27
Hi,

I'm not entirely sure, but I seem to read somewhere that the Acer 2441 doesn't allow cpu scaling. period.

I'd be interested to learn if you did manage it, though.

---

