---
title: "No Sound - Dell Latitude LS"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by Chiaro on 2006-06-18
I can't quite get the sound working! Xubuntu(and Ubuntu before it) reported there being no audio device....any help?

---

### Post by coeus on 2006-06-19
This may solve the problem

1.  Open a terminal session
2.  ```

sudo modprobe nm256

```
3. reboot

---

### Post by Chiaro on 2006-06-19
"giovanni@lappy586:~$ sudo modprobe nm256
Password:
FATAL: Module nm256 not found."

---

### Post by coeus on 2006-06-19
Ooops, that was a typo.
try
```

sudo modprobe snd_nm256

```

---

### Post by Chiaro on 2006-06-21
Ok, I'll give it a try.

---

### Post by Chiaro on 2006-06-21
Nogo.

```

giovanni@lappy486: ~$ sudo modprobe snd_nm256
Password:
giovani@lappy486: ~$
```

I reboot and it still says I don't have audio.

---

### Post by coeus on 2006-06-22
Can you post the output from the following two commands

```

lspci
lsmod

```

---

### Post by Chiaro on 2006-06-22
```
giovanni@Lappy486:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1211
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)

```

```
giovanni@Lappy486:~$ lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
af_packet              22920  0
ipv6                  265600  6
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
joydev                 10048  0
tsdev                   8000  0
pcmcia                 40508  0
3c59x                  45608  0
mii                     5888  1 3c59x
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
floppy                 62148  0
pcspkr                  2180  0
psmouse                36228  0
serio_raw               7300  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
ltserial               11056  0
ltmodem               566638  1 ltserial
i2c_piix4               9104  0
i2c_core               21904  2 i2c_acpi_ec,i2c_piix4
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  1 intel_agp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               129668  2 uhci_hcd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

---

### Post by coeus on 2006-06-22
The lspci command shows that the the sound card is not being detected at the hardware level, so it I think that perhaps it is not being initialised by Plug and Play.  I believe that Linux in general does not initialise PnP devices so you will need to do this in BIOS.

1.  Power up the laptop
2.  At the initial DELL splash screen, hit F2 to go to BIOS setup
3.  Go to Advanced and change Plug & Play O/S to No
4.  F10 to save and exit

See if your sound works, else post the result of the lspci command after your have made this change.

---

### Post by Chiaro on 2006-06-22
It didn't work, so here you go:

```
giovanni@Lappy486:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1211
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)

```

---

### Post by coeus on 2006-06-23
Well I am sorry to say that I am out of ideas.  The last two lines of output from lspci on this machine is:

```

0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)

```

So I am not sure why the sound card is not showing up for you.  Did you have any other operating system installed on the laptop before you tried Xubuntu and if so, did the sound card work then?  From what I can see, I don't think the problem is with Xubuntu or Linux as such, it seems to be more to do with the sound card being disabled at a hardware level, although I cannot find any such options in the BIOS setup.  Maybe somebody else has some ideas.

---

### Post by Chiaro on 2006-06-23
Windows XP didn't work with the sound either...

---

