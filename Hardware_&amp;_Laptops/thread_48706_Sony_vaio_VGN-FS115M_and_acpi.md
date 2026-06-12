---
title: "Sony vaio VGN-FS115M and acpi"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by hannes_ on 2005-07-13
Hi,

is there any1 out there who get it working?

Its not working for me, and i dont have any clue how to fix it.

without it there is no chance of getting any speedstep working and so on?

Any help would be nice.

Thnx

---

### Post by varunus on 2005-07-13
What is the output of "lsmod"?  Also, what processor is in the computer?  Even if ACPI doesn't work for other things, scaling should be possible.

---

### Post by hannes_ on 2005-07-13
here is my lsmod

> 
root@vaio-anders:/home/hannes # lsmod
Module                  Size  Used by
nls_cp437               5600  1
vfat                   13824  1
fat                    41760  1 vfat
sd_mod                 17776  2
usb_storage            71936  1
ipt_limit               2368  8
iptable_mangle          2720  0
ipt_LOG                 6880  8
ipt_MASQUERADE          3488  0
iptable_nat            26376  1 ipt_MASQUERADE
ipt_TOS                 2368  0
ipt_REJECT              6848  1
ip_conntrack_irc       71664  0
ip_conntrack_ftp       72528  0
ipt_state               1824  6
ip_conntrack           46420  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3584  1
ip_tables              18464  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
nvidia               3923452  14
ipv6                  257888  8
speedstep_lib           3940  0
proc_intf               3908  0
freq_table              4004  0
cpufreq_userspace       4348  0
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
orinoco_cs              9032  1
orinoco                42828  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 22244  3 orinoco_cs
apm                    20716  2
e100                   33920  0
mii                     4896  1 e100
ipw2200                71820  0
firmware_class          9984  1 ipw2200
ieee80211              23332  1 ipw2200
ieee80211_crypt         5640  1 ieee80211
ohci1394               34596  0
yenta_socket           21344  1
pcmcia_core            57984  3 orinoco_cs,pcmcia,yenta_socket
i2c_i801                8364  0
i2c_core               22320  1 i2c_i801
hw_random               5300  0
ehci_hcd               32708  0
uhci_hcd               32816  0
usbcore               119000  4 usb_storage,ehci_hcd,uhci_hcd
snd_hda_intel          17408  1
snd_hda_codec          72160  1 snd_hda_intel
snd_pcm_oss            53920  0
snd_mixer_oss          20288  2 snd_pcm_oss
snd_pcm                94568  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26116  1 snd_pcm
snd                    57380  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  2 snd
snd_page_alloc          9988  2 snd_hda_intel,snd_pcm
pci_hotplug            33488  0
intel_agp              22140  1
agpgart                33608  2 nvidia,intel_agp
pcspkr                  3496  0
rtc                    12472  0
nls_utf8                1952  3
ntfs                  110512  2
md                     47440  0
dm_mod                 59420  1
capability              4648  0
commoncap               7712  1 capability
sonypi                 25080  0
sr_mod                 17188  0
sbp2                   23816  0
scsi_mod              127552  4 sd_mod,usb_storage,sr_mod,sbp2
ieee1394              108312  2 ohci1394,sbp2
parport_pc             37252  0
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_cd                 41700  0
cdrom                  40220  2 sr_mod,ide_cd
evdev                   9344  0
mousedev               11288  1
tsdev                   7520  0
psmouse                21320  0
ext3                  137256  1
jbd                    60536  1 ext3
mbcache                 8356  1 ext3
ide_generic             1312  0
piix                   10340  1
ide_disk               20416  5
ide_core              129356  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   28276  978
processor              22452  0
fbcon                  37504  71
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  1
cfbcopyarea             3808  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3488  1 vesafb


the cpu is 

Intel® Pentium® M Prozessor 70, 533 MHz FSB, Support for Enhanced Intel SpeedStep® Technologie

thnx

---

### Post by varunus on 2005-07-13
What is in the folder /proc/acpi?

It looks like you're using APM instead of ACPI...try entering the following:

```
sudo rmmod apm
sudo /etc/init.d/acpid restart
sudo /etc/init.d/acpi-support restart

``` 

You also may want to try entering

```
sudo modprobe sony-acpi
``` 

It looks like speedstep should be working from your lsmod.  Try adding the frequency scaling monitor to your panel.

Good luck.

---

### Post by hannes_ on 2005-07-14
Hi, first of all thx for your reply.

Ok i did what u told me to do, but still there is no chance to get this speedstep panel working.

It always tells me my CPU doesnt support it...

Is there a chance to set the cpu running fullspeed? 

Well for example when I`m downloading something from the net with about 600 kbs everything slows down, and my mouse is not working, better jumps over the screen. Well everything is lagging :/ And this cant be. In windows the cpu runs smooth, how to get this working on lin?

This is what i get when i`m inserting the modules.
> 
root@vaio-anders:/home/hannes # modprobe sonypi
root@vaio-anders:/home/hannes # modprobe sony_acpi
FATAL: Error inserting sony_acpi (/lib/modules/2.6.10-5-686/kernel/drivers/acpi/sony_acpi.ko): No such device


thx and greets

---

### Post by varunus on 2005-07-19
Sorry for late reply, hannes.

Did the acpi command work, at least?  You said the sony_acpi one didn't work...If the ACPI command didn't work, it looks like you're using APM, which is very strange...

Try entering "sudo modprobe speedstep-centrino" into a terminal.  This should fix your speedstep problems, I think.  If it does, add the line "speedstep-centrino" to /etc/modules.

---

### Post by hannes_ on 2005-07-19
[QUOTE=varunus]Sorry for late reply, hannes.

Did the acpi command work, at least?  You said the sony_acpi one didn't work...If the ACPI command didn't work, it looks like you're using APM, which is very strange...

Try entering "sudo modprobe speedstep-centrino" into a terminal.  This should fix your speedstep problems, I think.  If it does, add the line "speedstep-centrino" to /etc/modules.[/QUOTE]
 well thx for your reply.

here is what i get (for your first posting)
```

root@vaio-anders:/home/hannes # rmmod apm
ERROR: Module apm is in use
root@vaio-anders:/home/hannes # /etc/init.d/acpid restart
root@vaio-anders:/home/hannes # /etc/init.d/acpi-support restart
root@vaio-anders:/home/hannes # modprobe sony-acpi
FATAL: Error inserting sony_acpi (/lib/modules/2.6.10-5-686/kernel/drivers/acpi/sony_acpi.ko): No such device
root@vaio-anders:/home/hannes #

```

and inserting the centrino speedstep module gets the following:
```

root@vaio-anders:/home/hannes # modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.10-5-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
root@vaio-anders:/home/hannes #
```

thnx Hannes

---

### Post by hannes_ on 2005-07-19
[QUOTE=hannes_]well thx for your reply.

here is what i get (for your first posting)
```

root@vaio-anders:/home/hannes # rmmod apm
ERROR: Module apm is in use
root@vaio-anders:/home/hannes # /etc/init.d/acpid restart
root@vaio-anders:/home/hannes # /etc/init.d/acpi-support restart
root@vaio-anders:/home/hannes # modprobe sony-acpi
FATAL: Error inserting sony_acpi (/lib/modules/2.6.10-5-686/kernel/drivers/acpi/sony_acpi.ko): No such device
root@vaio-anders:/home/hannes #

```

and inserting the centrino speedstep module gets the following:
```

root@vaio-anders:/home/hannes # modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.10-5-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
root@vaio-anders:/home/hannes #
```

thnx Hannes[/QUOTE]
 dmesg shows the following:
```

speedstep-centrino: obtaining ACPI data failed
speedstep-centrino: found unsupported CPU with Enhanced SpeedStep: send /proc/cpuinfo to Jeremy Fitzhardinge <jeremy@goop.org>
Access to /proc/cpufreq is deprecated and will be removed from (new) 2.6. kernels soon after 2005-01-01

```

---

