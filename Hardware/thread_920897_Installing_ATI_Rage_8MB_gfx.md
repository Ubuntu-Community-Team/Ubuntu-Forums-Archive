---
title: "Installing ATI Rage 8MB gfx?"
date: 2008-09-15
forum: Hardware
---

### Post by CH33TAH on 2008-09-15
Im a total newbie when it comes to linux.

Ive got Xubuntu 8.04 installed on my old laptop.

Now, my question is; how do i install a driver for my graphicscard? 
Its a: **ATI Rage Mobility P/M 8MB**

If anyone could write a detailed description of what i got to do, it would be awsome.. 


Thanks in advance,
CH33TAH :)

---

### Post by CH33TAH on 2008-09-16
Bump

Searched alot and i cant find any info on the topic :((

---

### Post by polygone on 2008-09-16
OK, we need to know what model your card is.  I am not a 'guru', by any means, but I've been dealing with drivers on two boxes.  One was ATI and one was nVidia.  So, I'll take a stab at it.

I am assuming you have a display, though, at this point and want to run the desktop effects.  Correct?

Run this:
```
lspci | grep ati
```

This should (key word here, as I am still a *nix noob too) give you the model of your card.  I, also, can't test it because I am at work and have to run linux through virtual box.  Then, we can work on a solution.

---

### Post by ManyBeers on 2008-09-26
> **polygone said:**
> OK, we need to know what model your card is.  I am not a 'guru', by any means, but I've been dealing with drivers on two boxes.  One was ATI and one was nVidia.  So, I'll take a stab at it.

I am assuming you have a display, though, at this point and want to run the desktop effects.  Correct?

Run this:
```
lspci | grep ati
```

This should (key word here, as I am still a *nix noob too) give you the model of your card.  I, also, can't test it because I am at work and have to run linux through virtual box.  Then, we can work on a solution.

I will be watching this thread because my So Mny Vaio laptops video card is also an Ati Rage Mobility M1 8mbs. My Ubuntu install is currently using the Vesa driver.

---

### Post by jocko on 2008-09-26
> **CH33TAH said:**
> Im a total newbie when it comes to linux.

Ive got Xubuntu 8.04 installed on my old laptop.

Now, my question is; how do i install a driver for my graphicscard? 
Its a: **ATI Rage Mobility P/M 8MB**

If anyone could write a detailed description of what i got to do, it would be awsome.. 


Thanks in advance,
CH33TAH :)

The open source driver (named "ati" or "r128") that is already installed by default in ubuntu is the only driver that supports such an old graphics card.
You shouldn't need to do anything to set it up.
Run the command "lsmod" in a terminal and see if you see any line containing "ati", "r128", "radeon" or "vesa".
If you see "vesa", you are using the wrong driver, but if you see any of the others (most likely "r128" for that card) you are already using the correct driver.

---

### Post by ManyBeers on 2008-09-26
> **jocko said:**
> The open source driver (named "ati" or "r128") that is already installed by default in ubuntu is the only driver that supports such an old graphics card.
You shouldn't need to do anything to set it up.
Run the command "lsmod" in a terminal and see if you see any line containing "ati", "r128", "radeon" or "vesa".
If you see "vesa", you are using the wrong driver, but if you see any of the others (most likely "r128" for that card) you are already using the correct driver.

Here is my "lsmod" output
le                  Size  Used by
ppdev                  10372  0 
powernow_k7             9000  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
freq_table              5536  3 powernow_k7,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ipv6                  267780  10 
sbp2                   24072  0 
lp                     12324  0 
loop                   18948  0 
usb_storage            73664  0 
libusual               19108  1 usb_storage
joydev                 13120  0 
ehci_hcd               37900  0 
pcmcia                 40876  0 
snd_via82xx            29464  4 
gameport               16008  1 snd_via82xx
snd_via82xx_modem      16264  0 
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
ac97_bus                3072  1 snd_ac97_codec
snd_mpu401_uart         9728  1 snd_via82xx
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
evdev                  13056  6 
serio_raw               7940  0 
snd_pcm                78596  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
psmouse                40336  0 
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
af_packet              23812  2 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
pcspkr                  4224  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
ac                      6916  0 
button                  9232  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  20 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27276  3 
rsrc_nonstatic         13696  1 yenta_socket
via686a                15244  0 
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               8800  1 snd
i2c_viapro              9876  0 
via_agp                11136  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
agpgart                34760  1 via_agp
i2c_core               24832  1 i2c_viapro
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
8139cp                 24704  0 
pata_acpi               8320  0 
floppy                 59588  0 
ohci1394               33584  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
ieee1394               93752  2 sbp2,ohci1394
uhci_hcd               27024  0 
usbcore               146028  6 usb_storage,libusual,ehci_hcd,usbhid,uhci_hcd
pata_via               13316  2 
ata_generic             8324  0 
libata                159344  3 pata_acpi,pata_via,ata_generic
scsi_mod              151436  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  3 powernow_k7,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

Would you help me to make sure I am using the ATI driver rather than the Vesa one?

---

### Post by jocko on 2008-09-27
> **ManyBeers said:**
> Here is my "lsmod" output
le                  Size  Used by
...

Would you help me to make sure I am using the ATI driver rather than the Vesa one?

That's weird... I don't see any video driver at all in that output.
Try running these commands:
```
grep R128 /var/log/Xorg.0.log
grep VESA /var/log/Xorg.0.log
grep ATI /var/log/Xorg.0.log
grep RADEON /var/log/Xorg.0.log
```

Whichever gives you a bunch of lines starting with "(**) R128(0):" or "(**) VESA(0):" and so on tells you which driver is in use.

---

### Post by ManyBeers on 2008-09-27
> **jocko said:**
> That's weird... I don't see any video driver at all in that output.
Try running these commands:
```
grep R128 /var/log/Xorg.0.log
grep VESA /var/log/Xorg.0.log
grep ATI /var/log/Xorg.0.log
grep RADEON /var/log/Xorg.0.log
```

Whichever gives you a bunch of lines starting with "(**) R128(0):" or "(**) VESA(0):" and so on tells you which driver is in use.

Here you go:
grep VESA /var/log/Xorg.0.log
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 8128 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64RM
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level none
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read failed
mark@ubuntu:~$ grep ATI /var/log/Xorg.0.log
(--) PCI:*(1:0:0) ATI Technologies Inc Rage Mobility P/M AGP 2x rev 100, Mem @ 0xe9000000/24, 0xe8100000/12, I/O @ 0x9000/8
(II) MACH64: Driver for ATI Mach64 chipsets
(--) Chipset ATI 3D Rage Mobility found
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(--) MACH64(0): ATI 3D Rage Mobility graphics controller detected.
(--) MACH64(0): ATI Mach64 adapter detected.
mark@ubuntu:~$ grep RADEON /var/log/Xorg.0.log
mark@ubuntu:~$ grep R128 /var/log/Xorg.0.log
mark@ubuntu:~$

By the way  Jocko I live in Salt lake City. We may have a time zone problem here.  This post was made at 8:00 AM Mountain Time.Saturday Sept.27, 2008

---

### Post by jocko on 2008-09-27
> **ManyBeers said:**
> Here you go:
grep VESA /var/log/Xorg.0.log
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 8128 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64RM
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level none
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read failed
mark@ubuntu:~$ grep ATI /var/log/Xorg.0.log
(--) PCI:*(1:0:0) ATI Technologies Inc Rage Mobility P/M AGP 2x rev 100, Mem @ 0xe9000000/24, 0xe8100000/12, I/O @ 0x9000/8
(II) MACH64: Driver for ATI Mach64 chipsets
(--) Chipset ATI 3D Rage Mobility found
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(--) MACH64(0): ATI 3D Rage Mobility graphics controller detected.
(--) MACH64(0): ATI Mach64 adapter detected.
mark@ubuntu:~$ grep RADEON /var/log/Xorg.0.log
mark@ubuntu:~$ grep R128 /var/log/Xorg.0.log
mark@ubuntu:~$

By the way  Jocko I live in Salt lake City. We may have a time zone problem here.  This post was made at 8:00 AM Mountain Time.Saturday Sept.27, 2008

That looks ok to me. I forgot there was a "mach64" driver as well... and after some googling I see that Rage Mobility was a Mach64 series graphics chip, so you are using the correct driver. The only thing you can do to improve it is to buy a new laptop...

---

### Post by ManyBeers on 2008-09-27
> **jocko said:**
> That looks ok to me. I forgot there was a "mach64" driver as well... and after some googling I see that Rage Mobility was a Mach64 series graphics chip, so you are using the correct driver. The only thing you can do to improve it is to buy a new laptop...
Ok then, thanks

The reason I wanted to know is because I am getting random freezes and I am
trying to root out the culprit. I figure it is either video related, sound related or possibly heat, though it has locked up when the temperature was 
normal and not close to overheating.

---

