---
title: "acpi events on Lenovo/IBM Thinkpad R51e"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by basilisk on 2006-03-05
Hey, 
I managed to install Breezy on my Thinkpad R51e. From a clean install the system would not respond to closing the lid and would crash when trying to suspend to disk or RAM. 
After moving to a 686 kernel, messing around to get the latest fglrx/madwifi drivers, and adding the following kernel options to grub:
noapic nolapic acpi_sleep=s3_bios
the machine will suspend to disk and wakeup using the acpi scripts in
/etc/acpi
The machine still will not wake from a suspend to RAM and will not respond to closing the lid or any of the IBM fn keys or the power button.
cat /proc/acpi/button/lid/LID/state
properly returns:
state:      open
or 
state:      closed 
but the computer does not actually do anything. I tried using acpi_listen and I see nothing when pressing any of the buttons. So it seems like something is intercepting the messages? Or the events are disabled? 
I know enough Linux to be dangerous, not enough to really know where to go next. Below are the output from dmesg | grep -i acpi  and  lsmod: 
```

basilisk@StinkPad:/etc/acpi$ dmesg | grep -i acpi
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[ 8], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[ 9], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[ A], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[ C], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[ D], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[ E], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[ F], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[10], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[11], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[13], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[14], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[15], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[16], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[17], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[18], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[19], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[1A], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[1B], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[1C], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[1D], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[1E], disabling event
[4294776.702000]     ACPI-0701: *** Error: acpi_ev_gpe_dispatch: No handler or method for GPE[1F], disabling event
[4294784.088000] ACPI: AC Adapter [AC] (off-line)
[4294784.191000] ACPI: Power Button (FF) [PWRF]
[4294784.191000] ACPI: Lid Switch [LID]
[4294784.191000] ACPI: Sleep Button (CM) [SLPB]
[4294784.447000] ibm_acpi: IBM ThinkPad ACPI Extras v0.8
[4294784.447000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[4294793.926000] ACPI: Battery Slot [BAT0] (battery present)
[4294793.948000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294867.493000] ACPI: PCI interrupt for device 0000:04:02.0 disabled
[4294867.505000] ACPI: PCI interrupt for device 0000:04:00.0 disabled
[4294867.660000] ACPI: PCI interrupt for device 0000:00:14.5 disabled
[4294867.661000] ACPI: PCI interrupt for device 0000:00:13.2 disabled
[4294868.223000] ACPI: PCI interrupt for device 0000:00:13.1 disabled
[4294868.324000] ACPI: PCI interrupt for device 0000:00:13.0 disabled
[4294910.081000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294910.346000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294910.346000] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294910.611000] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294911.072000] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294911.072000] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294911.072000] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294911.072000] ACPI: PCI Interrupt 0000:00:14.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294911.253000] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[4294911.264000] ACPI: PCI Interrupt 0000:04:02.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[4294927.909000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4296095.976000] ACPI: PCI interrupt for device 0000:04:02.0 disabled
[4296095.988000] ACPI: PCI interrupt for device 0000:04:00.0 disabled
[4296096.555000] ACPI: PCI interrupt for device 0000:01:05.0 disabled
[4296096.555000] ACPI: PCI interrupt for device 0000:00:14.5 disabled
[4296096.556000] ACPI: PCI interrupt for device 0000:00:13.2 disabled
[4296097.118000] ACPI: PCI interrupt for device 0000:00:13.1 disabled
[4296097.219000] ACPI: PCI interrupt for device 0000:00:13.0 disabled
[4304718.409000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4304718.674000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4304718.674000] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4304718.938000] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4304719.399000] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4304719.399000] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4304719.399000] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4304719.399000] ACPI: PCI Interrupt 0000:00:14.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4304719.401000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4304719.606000] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[4304719.617000] ACPI: PCI Interrupt 0000:04:02.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11

```

And here is the results from lsmod:
```

Module                  Size  Used by
fglrx                 457836  7
nvram                   8488  1
binfmt_misc            11496  1
speedstep_centrino      7636  1
cpufreq_powersave       1696  0
cpufreq_stats           5252  0
cpufreq_userspace       4316  1
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
freq_table              4388  2 speedstep_centrino,cpufreq_stats
tc1100_wmi              6692  0
video                  15748  0
battery                 9348  0
ibm_acpi               17684  0
container               4384  0
i2c_acpi_ec             5472  0
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0
pcc_acpi               11104  0
sony_acpi               5324  0
ac                      4708  0
dev_acpi               11108  0
hotkey                  9284  0
ipv6                  251232  6
af_packet              21768  4
parport_pc             35236  0
parport                35912  1 parport_pc
rtc                    12344  0
pcspkr                  3396  0
wlan_scan_sta          14784  1
ath_pci                97860  0
ath_rate_sample        12992  1 ath_pci
wlan                  197756  4 wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               188816  3 ath_pci,ath_rate_sample
yenta_socket           25292  0
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  2 yenta_socket,rsrc_nonstatic
snd_atiixp             20288  1
snd_ac97_codec         83932  1 snd_atiixp
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_atiixp,snd_pcm
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
ati_agp                 9036  0
agpgart                34792  2 fglrx,ati_agp
nls_iso8859_1           4000  1
vfat                   13440  1
fat                    52668  1 vfat
nls_cp437               5664  2
ntfs                  108144  1
tsdev                   7776  0
evdev                   9664  0
psmouse                30116  0
mousedev               11616  1
reiserfs              262320  1
thermal                13000  0
processor              22812  2 speedstep_centrino,thermal
fan                     4484  0
tg3                    96772  0
ehci_hcd               34248  0
ohci_hcd               20644  0
usbcore               118044  3 ehci_hcd,ohci_hcd
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  5
ide_generic             1376  0
atiixp                  6032  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,atiixp
unix                   26896  557
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
vesafb                  7992  1
cfbcopyarea             4608  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3872  1 vesafb
softcursor              2272  1 vesafb
capability              4712  0
commoncap               6816  1 capability


```

---

### Post by basilisk on 2006-03-12
So I have continued to mess around with this computer and figured I would post changes/findings here for anyone else with this laptop. 
From the instructions [here]("http://forums.gentoo.org/viewtopic.php?t=122145") I checked the DSDT of this machine. It compiles with no errors or warnings. I also looked through the code for a OS name check  there is some checking but only to disable features.  So it seems any issues would  be with the Linux ACPI implimentation?
Using ACPI=off the Thinkpad specific hotkeys and sound will work. I also see the nice overlay when adjusting sound/brightness etc. However, I was out all my power management features which is not good for a laptop.
Leaving ACPI on and digging deeper I was able to track down my previous boot up ACPI errors to something in the /etc/hotplug/isapnp.rc script. If this script does not load I do not recieve any boot errors. I have this script disabled for now, this prevents kernel modules for the paralell port and the internal PC speaker from loading.  
I also found I get more consistant suspend to disk (hibernate) results if I use the following kernel options:
pci=usepirqmask pci=noacpi pnpacpi=off
And I comment out refrences to saving/re-loading the video state in /etc/acpi/prepare.sh and /etc/acpi/resume.sh I (vbetool VBESTATE type stuff)

So where am I left with this machine? 
[LIST]
[*]Still get nothing from acpi_listen
[*]I now have sound 
[*]The on screen overlays and lid/hotkey functionality are not there. 
[*]No ACPI fan control. 
[*]The computer will sleep to disk and return. 
[*]The comptuer will sleep to RAM but will not return. (the HD spins up but thats it) 
[/LIST]
   I have tried passing in many different kernel options, even building out my own 2.6.15.6 kernel but still cant get everything there.

---

### Post by ranf on 2006-03-13
Let's look at what others have to say about this machine:
[http://tuxmobil.org/ibm.html](http://tuxmobil.org/ibm.html)

---

### Post by basilisk on 2006-03-13
Thanks, good site! 
It should be mentioned that from the IBM/Lenovo documentation the R51e is closest to the R50e and R52. 
This is also a decent resource: [http://www.thinkwiki.org]("http://www.thinkwiki.org")
At this time there just seems to be a general lack of information about this specific model out there, must be something better at its pricepoint. Maybe that is why it was on sale! 
-G

---

### Post by David Persson on 2007-01-26
Ubuntu Edgy and Thinkpad R51e doesn’t work for me.
Booting without kernel parameter noapic causes my complete usb-hub including mouse to quit function after ca. 3 minutes.
ACPI isn’t working from the very beginning on. Therefore maybe Hibernation isn’t working. During boot process I get these errors without the noapic option:

…
ACPI Error (evgpe-0711): No handler or method for GPE[16], disabling event [20060707]
…
…
…

I already checked the DSDT but it’s all ok. See Posts above.

Before Ubuntu Edgy I had FC5 installed on this notebook. Similiar problems…

Any Suggestions?
Maybe you can help me with these???

David

---

