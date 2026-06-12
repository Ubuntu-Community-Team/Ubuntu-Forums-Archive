---
title: "thinkpad x60s overheating with ubuntu 904"
date: 2009-05-31
forum: Hardware
---

### Post by jdanoz on 2009-05-31
Hello,

recently I installed Ubuntu 9.04 to my Lenovo Thinkpad x60s, but I have noticed that sometimes ubuntu power off the machine without any warnings or messages, simply shutdowns.

I suppose that the cpu temperature is very high, so the machine is self powering off to prevent that cpu burns.

I'm using the thinkpad_acpi module (I think it comes with 9.04).

Here is the output of a few commands:

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)

lsmod:

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
binfmt_misc            16776  1 
ppdev                  15620  0 
i915                   65540  2 
drm                    96296  3 i915
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
btusb                  19608  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
snd_seq_dummy          10756  0 
ecb                    10752  2 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
mmc_block              17668  2 
iwl3945                97912  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nsc_ircc               29328  0 
thinkpad_acpi          66560  0 
pcmcia                 44748  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
mac80211              217208  1 iwl3945
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
led_class              12036  2 iwl3945,thinkpad_acpi
video                  25360  0 
irda                  197180  1 nsc_ircc
nvram                  16396  1 thinkpad_acpi
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw              13316  0 
cfg80211               38032  2 iwl3945,mac80211
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
pcspkr                 10496  0 
output                 11008  1 video
joydev                 18368  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
crc_ccitt              10112  1 irda
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

acpi -t:

     Battery 0: Charging, 42%, 00:29:08 until charged
     Thermal 0: ok, 67.0 degrees C
     Thermal 1: ok, 66.0 degrees C

hddtemp /dev/sda1:

/dev/sda1: TOSHIBA MK8032GSX: 49°C

cat /proc/cpuinfo:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           L2400  @ 1.66GHz
stepping	: 8
cpu MHz		: 1667.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm
bogomips	: 3325.04
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           L2400  @ 1.66GHz
stepping	: 8
cpu MHz		: 1667.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm
bogomips	: 3325.11
clflush size	: 64
power management:

The CPU temperature is normally (with Ubuntu 9.04) at 65-75 (average), and I have seen a maximum of 80 ºC, I think that when it increases a bit more than 80 C, then the machine is automatically shutdown.

Could you give me any idea, please?

Thanks in advance,

Best regards,
Jorge

---

### Post by jdanoz on 2009-06-01
Hello,

In Windows, yesterday, the temp was 60-65 ºC. I think that the higher temperatures could be due to larger times of activity with the computer, isn't it?

Today, when I powered on the computer, in Ubuntu the temperature is 49-53 C average.

acpi -t: 

     Battery 0: Discharging, 28%, 00:28:54 remaining
     Thermal 0: ok, 52.0 degrees C
     Thermal 1: ok, 52.0 degrees C

regs,
Jorge

---

### Post by jdanoz on 2009-06-01
after almost one hour... the temperature in ubuntu is again at 63-68-70 ºC average...

---

### Post by pablolie on 2009-06-04
i am running 9.04 with an x60s, and i don't think the temperature is that much higher than in WinXP.

---

### Post by jdanoz on 2009-06-04
Hello pablolie,

What is your CPU temperature under Ubuntu?

regs,
Jorge

---

### Post by pablolie on 2009-06-05
no part of the X60s feels particularly warm to the touch, and certainly not warmer than it does running the XP OS it came with, so I have not felt compelled to measure it. i am too busy trying to get it to truly connect remotely to my corporate network while running Ubuntu... :-)

---

### Post by roystudios on 2009-07-15
I have had the same problem with the last version of ubuntu - about once a week I had the x60 machine restarting with a msg in /var/log/messages saying the CPU had hit critical temperature (127) and was shutting down. With XP (which I have use on this machine as well) it seems to regulate the temperature far better through judicious use of fan control. Maybe we just need to look at how Ubuntu regulates fan control. Ill think on.
PS: this happens more when the system is docked than out in the real world, so may be poor heat dissipation.

---

### Post by HoboGarden on 2009-07-15
I have a thinkpad t61.  While our models aren't the same, I'm still interested in why your laptop is overheating.  Could you install a system monitor like conky so we can find out your cpu usage while doing simple tasks like web browsing.  It would also give us insight on the temperature of your cpu and gpu while doing those tasks.

A part of me suspects something is wrong with the video driver.  

Btw you can increase your fan speed by following this:
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed#Using_a_stock_kernel](http://www.thinkwiki.org/wiki/How_to_control_fan_speed#Using_a_stock_kernel)

add the following to /etc/modprobe.d/options: options thinkpad_acpi fan_control=1
restart system
# sudo -s
# echo level disengaged > /proc/acpi/ibm/fan 

it will allows your fan to go the maximum which is around 5000 rpm.  It keeps my computer cool at the maxmium of 60 C but still doesn't help with the cpu problem.

I don't know why but just scrolling, using firefox and moving windows can use up 30-40% cpu power.

---

