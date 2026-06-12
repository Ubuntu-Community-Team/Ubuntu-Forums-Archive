---
title: "Alsa, kernel 2.6 and sound trouble"
date: 2005-02-13
forum: Hardware &amp; Laptops
---

### Post by arjaybe on 2005-02-13
Alsa fails to utilize my sound card under kernel 2.6.  I've run into this behavior with Ubuntu, MEPIS, Beatrix and Kanotix.  A copy of this message is going to each forum.  Sound works for me when I select the 2.4 kernel in MEPIS.

Alsaconf fails to find my sound card - ISA non-plug-and-play SB16.

Alsamixer fails with this message:

alsamixer: function snd_ctl_open failed for default: No such device

Alsactl store fails with this message:

alsactl: save_state:1194: No soundcards found...

This happens when a system sound fails (in KDE):

Error while initializing the sound driver:
device /dev/dsp can't be opened (No such device)
The sound server will continue, using the null output device.

In hope for sound,
jim

---

### Post by Xian on 2005-02-14
[QUOTE=arjaybe]This happens when a system sound fails (in KDE):

Error while initializing the sound driver:
device /dev/dsp can't be opened (No such device)
The sound server will continue, using the null output device.[/QUOTE]
That looks like a permissions issue. If you login as root in one of your other distros do you get this same error message? I would try a chmod command and change the file permissions on /dev/dsp to allow general user access.

---

### Post by Xian on 2005-02-14
[QUOTE=arjaybe]Sound works for me when I select the 2.4 kernel in MEPIS.[/QUOTE]
Oh, and when you do get sound in this system you might want to post the output of a "lsmod" command so we can see exactly what modules are being correctly loaded in order to get sound working. Also, after you su to root in that 2.4 box post the output of a "lspci -v" command.

---

### Post by arjaybe on 2005-02-14
lsmod (in kernel 2.4 with working sound)
Module                  Size  Used by
snd_sb16                8044  1
snd_opl3_lib            6912  1 snd_sb16
snd_sb16_dsp            7680  1 snd_sb16
snd_pcm_oss            42024  0
snd_mixer_oss          14464  1 snd_pcm_oss
snd_pcm                61320  2 snd_sb16_dsp,snd_pcm_oss
snd_timer              17284  2 snd_opl3_lib,snd_pcm
snd_page_alloc          6024  1 snd_pcm
snd_sb16_csp           16768  1 snd_sb16
snd_sb_common           8832  3 snd_sb16,snd_sb16_dsp,snd_sb16_csp
snd_hwdep               6532  2 snd_opl3_lib,snd_sb16_csp
snd_mpu401_uart         4992  1 snd_sb16
snd_rawmidi            16420  1 snd_mpu401_uart
snd_seq_device          5128  2 snd_opl3_lib,snd_rawmidi
snd                    34916  15 snd_sb16,snd_opl3_lib,snd_sb16_dsp,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_sb16_csp,snd_sb_common,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               3936  1 snd
parport_pc             26048  1
lp                      6700  0
parport                23240  2 parport_pc,lp
ipv6                  185568  15
af_packet              11912  0
ds                      8964  0
yenta_socket           12288  0
pcmcia_core            36292  2 ds,yenta_socket
8250                   11488  0
serial_core            13824  1 8250
hfs                    32132  0
minix                  21380  0
ntfs                   99308  0
nls_iso8859_1           3072  6
nls_cp437               4608  2
ne2k_pci                5216  0
8390                    6400  1 ne2k_pci
crc32                   3200  1 8390
w83781d                20224  0
i2c_sensor              1792  1 w83781d
i2c_isa                 1152  0
i2c_core               11796  3 w83781d,i2c_sensor,i2c_isa
thermal                 6800  0
processor               8880  1 thermal
fan                     1548  0
button                  2840  0
battery                 5900  0
ac                      1804  0
floppy                 44112  0
uhci_hcd               22928  0
ohci_hcd               14980  0


 lspci -v
0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
        Subsystem: ALi Corporation ALI M1541 Aladdin V/V+ AGP System Controller
        Flags: bus master, slow devsel, latency 64
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [b0] AGP version 1.0

0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if10 [OHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at df800000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: ALi Corporation M7101 Power Management Controller [PMU]
        Flags: medium devsel

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (rev c3)
        Flags: bus master, medium devsel, latency 0

0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
        Flags: medium devsel, IRQ 10
        I/O ports at d800 [size=32]

0000:00:0b.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01) (prog-if 00 [VGA])
        Flags: stepping, medium devsel, IRQ 11
        Memory at df000000 (32-bit, non-prefetchable) [size=16K]
        Memory at e7800000 (32-bit, prefetchable) [size=8M]
        Expansion ROM at 000c0000 [disabled] [size=64K]

0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c1) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        I/O ports at d400 [size=16]

But the sound card is a SB16 ISA

Xian:  I'll try to chmod /dev/dsp next time I'm in one of my kernel 2.6 installs.

---

### Post by arjaybe on 2005-02-14
I now have sound from my ISA Soundblaster 16 using the 2.6 kernel.  I did it by removing Alsa and using the OSS driver (sb).

I put this in /etc/modules-whatever:

sb io=0x220 irq=5 dma=1 dma16=5

Sound, glorious sound.

---

