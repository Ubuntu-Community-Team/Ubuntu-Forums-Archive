---
title: "[SOLVED] PC speaker beeps every few minutes"
date: 2008-12-25
forum: Hardware
---

### Post by AopicieR on 2008-12-25
Hi,

my computer is the Asus A6VM-Q004H laptop. I have the following very annoying problem under Ubuntu: the PC speaker beeps every few minutes. The beeps seem to occur randomly: sometimes there are two beeps within 5 minutes, sometimes there isn't a single beep for a whole hour. It doesn't matter whether I'm sitting at the laptop or what I'm doing with it, it also beeps when it's just standing there without any programs running. The beep is always the same and lasts approximately one second (maybe a bit less). 
I was using Windows XP before and there wasn't a single beep during two years.
I've tried unloading the drivers with 
sudo modprobe -r pcspkr
and by adding
blacklist pcspkr
to my /etc/modprobe.d/blacklist, but without any effect.

At first I thought that I could live with it, but it is starting to annoy the heck out of me. So I'll be very grateful for any suggestions.

---

### Post by pytheas22 on 2008-12-25
The next time you hear a beep, please immediately open a terminal, run the following commands and post the output:
```

dmesg | tail -50
lsmod | grep pc
```

---

### Post by Jose Catre-Vandis on 2008-12-25
try
xset -b
or
setx -b

in ~/.bashrc

and/or

set bell-style none
in ~/.inputrc

Or change the frequency of the beep (in shell)
setterm -blength 0

the number is the frequency, so &#8216;0&#8242; turns it off.

---

### Post by AopicieR on 2008-12-25
Here are the outputs: 
dmesg:
```

[   19.388248]  =======================
[   19.388656] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:26/device:27/input/input7
[   19.404028] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.415825] parport_pc 00:08: reported by Plug and Play ACPI
[   19.415854] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   19.747421] nvidia 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.747430] nvidia 0000:03:00.0: setting latency timer to 64
[   19.747590] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   21.195340] cs: IO port probe 0x100-0x3af: clean.
[   21.196781] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.197164] cs: IO port probe 0x820-0x8ff: clean.
[   21.197454] cs: IO port probe 0xc00-0xcf7: clean.
[   21.198076] cs: IO port probe 0xa00-0xaff: clean.
[   22.102868] lp0: using parport0 (interrupt-driven).
[   22.203082] Adding 1984016k swap on /dev/sda3.  Priority:-1 extents:1 across:1984016k
[  148.734719] EXT3 FS on sda2, internal journal
[  150.146933] type=1505 audit(1230245530.170:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3910
[  150.147209] type=1505 audit(1230245530.170:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3910
[  150.245670] ip_tables: (C) 2000-2006 Netfilter Core Team
[  150.885321] ACPI: WMI: Mapper loaded
[  151.699051] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  151.750195] apm: BIOS not found.
[  151.799362] ppdev: user-space parallel port driver
[  154.432051] Bluetooth: Core ver 2.13
[  154.434035] NET: Registered protocol family 31
[  154.434041] Bluetooth: HCI device and connection manager initialized
[  154.434045] Bluetooth: HCI socket layer initialized
[  154.462326] Bluetooth: L2CAP ver 2.11
[  154.462333] Bluetooth: L2CAP socket layer initialized
[  154.495753] Bluetooth: SCO (Voice Link) ver 0.6
[  154.495760] Bluetooth: SCO socket layer initialized
[  154.518448] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  154.518455] Bluetooth: BNEP filters: protocol multicast
[  154.553960] Bridge firewalling registered
[  154.554597] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  154.597695] Bluetooth: RFCOMM socket layer initialized
[  154.597927] Bluetooth: RFCOMM TTY layer initialized
[  154.597933] Bluetooth: RFCOMM ver 1.10
[  158.684435] skge eth0: enabling interface
[ 2061.502271] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[ 2062.259524] NET: Registered protocol family 17
[ 2065.698502] skge eth0: Link is down.
[ 2253.141031] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[ 2261.911437] PPP generic driver version 2.4.2
[ 2262.099014] padlock: VIA PadLock Hash Engine not detected.
[ 2262.131820] PPP MPPE Compression module registered
[ 2262.349505] GRE over IPv4 tunneling driver
[ 2271.293014] NET: Registered protocol family 10
[ 2271.296179] lo: Disabled Privacy Extensions
[ 2281.940033] eth0: no IPv6 routers present

```

lsmod:

```

pci_slot               12552  0 
pcmcia                 43052  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              29960  2 snd_pcm,snd_seq
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp

```

The beep occured when I had just reconnected my PC to the internet which should correspond to the messages containing eth0 in the dmesg output.

Jose's suggestions did not have any effect.

Edit: I've just heard another beep and the output of dmesg has not changed.

---

### Post by pytheas22 on 2008-12-25
That's strange.  What is the total output of:
```

lsmod
```

Also, I assume you tried this already, but just in case: if you double-click on your volume icon in the Gnome panel (or type 'alsamixer' in a terminal), you should be presented with a sound-control utility that should include a section for the PC speaker.  Did you try muting it there?

---

### Post by hysteresis on 2008-12-25
My desktop PC speaker used to beep when the CPU was too hot.

---

### Post by AopicieR on 2008-12-25
lsmod gives
```

pci_slot               12552  0 
pcmcia                 43052  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              29960  2 snd_pcm,snd_seq
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
Module                  Size  Used by
ipv6                  263972  8 
ip_gre                 19076  0 
sha1_generic           10368  0 
arc4                    9984  0 
ecb                    10880  0 
crypto_blkcipher       25476  1 ecb
ppp_mppe               14852  0 
ppp_generic            32668  1 ppp_mppe
slhc                   14208  1 ppp_generic
af_packet              25728  2 
ppdev                  15620  0 
speedstep_centrino     15360  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
container              11520  0 
pci_slot               12552  0 
iptable_filter         10752  1 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
lp                     17156  0 
joydev                 18368  0 
pcmcia                 43052  0 
evdev                  17696  12 
serio_raw              13444  0 
psmouse                45200  0 
snd_hda_intel         381488  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
mmc_core               58268  1 sdhci
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
nvidia               6900560  28 
i2c_core               31892  1 nvidia
snd_seq_dummy          10884  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
video                  25104  5 
output                 11008  1 video
battery                18436  0 
ac                     12292  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
asus_laptop            24440  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class              12164  1 asus_laptop
button                 14224  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  3 
ata_generic            12932  0 
pata_acpi              12160  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
ohci1394               37936  0 
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
skge                   48144  0 
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  4 usbhid,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

I don't use gnome but alsa-mixer doesn't contain a section for the PC speaker. Maybe because I've unloaded the drivers.

The CPU being too hot is impossible, I'm only running firefox right now and the fan is not even working. But I guess the beep has to come from the BIOS or whatever, Ubuntu should not be able to beep without the drivers, should it? But why did it never occur in Windows? Maybe Ubuntu is sending the BIOS false information concerning the CPU temperature? I don't know whether this makes any sense.

---

### Post by pytheas22 on 2008-12-25
I don't see any modules in your list that would be able to drive the PC speaker, as far as I know.  And since you also don't seem to have a PC speaker in alsa, I think the only thing to conclude is that the beeping is beyond Ubuntu's control.

[This thread]("https://www.linuxquestions.org/questions/linux-general-1/pc-speaker-beeping-occasionally-337847/") describes a similar problem that came down to CPU overheating.  On the other hand, it's weird that nothing's getting sent to dmesg if your machine is getting too hot, but if this is all happening because of BIOS, that might explain why dmesg doesn't mention it.  It's also of course weird that the beeping doesn't occur in Windows, but it's possible that either Windows is suppressing it somehow or that Ubuntu runs hotter than Windows for some reason.

You can [install some stuff]("http://www.bradtrupp.com/ubuntu-cpu-temperature.html") to monitor machine temperature to see if it really is getting hot, or you could do CPU-intensive stuff (e.g. compile something big or render some video) to see if that triggers more beeping (you may also want to play some 3D game to give the GPU a workout; that could also be the source of overheating).  You could also check BIOS to see if there are any options regarding beeping.

Beyond that, unfortunately, the only answer I can think of is to unplug the PC speaker...

---

### Post by AopicieR on 2008-12-28
Thank you for your suggestions.
I've just installed lm-sensors and the CPU temperature is indeed surprisingly high considering I'm not running a single program(!), namely around 70°C. 

Windows XP manages the CPU frequency dynamically and reduces it to 40% for most of the time. I'm not using a desktop manager and I don't know how to make Ubuntu reduce the frequency. I'll ask google, but any suggestions will be appreciated.

Edit: I've found the following tutorial which desribes exactly what I was looking for:
[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

However, this does not seem to be the answer to the initial question as a beep just occured with the CPU temperature being around 50°C.

---

### Post by AopicieR on 2009-01-05
I have to push this topic again. The beeps are incredibly annoying and very loud. Is it possible to physically unplug the PC speaker in a laptop? Or are there any other possible reasons besides CPU temperature?

---

### Post by pytheas22 on 2009-01-05
I can't think of anything besides overheating...but that itself was just speculation.  More importantly, your dmesg output doesn't mention anything that would relate to the beeping.

I would check BIOS to see if there's an option to turn off the speaker.  You should also be able to unplug it physically if you open up your laptop case, but it's hard to say where exactly you should look.  If you google your laptop model, however, you may be able to find disassembly instructions to help you take it apart.  Keep in mind that disassembling the machine probably voids the warranty, etc.

---

### Post by AopicieR on 2009-01-06
I'm checking sensors from time to time and the CPU temperature is stable around 50°C. 
Actually my hard disk is making strange noises under Ubuntu from time to time and I start to suspect that they are related to the beeps. They occur when no hard drive activity is shown by the corresponding lamp and when there really isn't any reason for activity. I'll google on the issue.

---

### Post by AopicieR on 2009-01-06
Sorry, a network error occured.

---

### Post by AopicieR on 2009-01-07
My guess seems to have been correct.
I've entered hdparm -B 255 /dev/sda and I've written it into my /etc/hdparm.conf as described in 
[http://eric.biven.us/2008/10/09/my-hard-drive-is-clicking-again-so-im-stopping-it-cold-when-ubuntu-boots/](http://eric.biven.us/2008/10/09/my-hard-drive-is-clicking-again-so-im-stopping-it-cold-when-ubuntu-boots/)
and I haven't heard a beep in hours.
Strange thing but I really hope that this solves the problem.

---

### Post by pytheas22 on 2009-01-07
hmmm, that's strange, but I'm glad it seems to have fixed the problem.  Please confirm later on if this does prove to be a solution.

---

### Post by AopicieR on 2009-01-08
I'm pretty sure now that this was indeed the problem.
I set hdparm -B back to its default value and a beep occured shortly afterwards. After setting it back to 255, I have now been beep-free for several hours again.
Thanks for your help, I'll mark the thread as solved.

---

### Post by star3x on 2009-01-10
Hi, I have the same problem the computer beeps.

This thread solved the problem (I hope)but in a little different way.
When I use hdparm -B 254 the beep stops but using ....apm = 254.... in /etc/hdparm.conf does not. I have now tried with: 
command_line {
    hdparm -B 245 /dev/sda
}

I will report the result of this.

I'am running ubuntu 8.10 on a ThinkPad T61

// Robert

---

### Post by AopicieR on 2009-01-12
Glad it seems to help others. 
What do you see after typing 
hdparm -B 255 /dev/sda ?
You should see "power management disabled" or so.
When writing it into your hdparm.conf, it should automatically be set to 255 after reboot. Try 
hdparm -I /dev/sda | grep power
after reboot. You should see "power management disabled." or something similar (can't test it right now).
Good luck.

---

### Post by star3x on 2009-01-12
I am really glad to get rid of the beeping,

If I use the hdparm -B 255 it says "setting Advanced power management level to disabled" and 254 say .....level to 0xfe (254).

Setting:
command_line {
      hdparm -B 254 /dev/sda
} 
has been working for 2 days, I will try to set apm = 255 and see what hdparm -I gives me, checked 2 days ago but don't remember, and at that time I just tried with 254.

---

