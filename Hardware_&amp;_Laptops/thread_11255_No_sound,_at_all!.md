---
title: "No sound, at all!"
date: 2005-01-15
forum: Hardware &amp; Laptops
---

### Post by TaNeK on 2005-01-15
Hi!

Hi all!

I installed Ubuntu yesterday, converting from 4 weeks of Debian and before that WinXP, and I like it best of the three, There really only is one big setback: I get no sound! No system sound, no sound from any XMMS plugin nor any other application. When I try plaing sound with XMMS I get the following error:
```

Couldn't open audio

Please check that your soundcard is configured properly
Your'e have the correct output plugin selected
No other program is blocking the soundcard.
```

I have apt-get installed all alsa-packages I ever needed in Debian (where I never got sound working very good either), and alsaconf cannot run. I have no real clue to what I am to do to get this working... Sound is very important to me, as I play games quite often and listen to music almost 24/7...

Help appreciated!

---

### Post by Vesperan on 2005-01-15
Hi Tanek,
could you try putting acpi_irq_isa=7 into your kernel line of grub config please? I had a similar problem, and after discovering this thread: [How to: Dell Latitude D800 Laptop](http://ubuntuforums.org/showthread.php?t=5464) it cleared up for me. It did help however, that I am on a D600 laptop.

Alternately, I also got sound working by recompiling the kernel with built in file system support and no ramdisk being loaded. But the above was much easier, and the default Ubuntu kernel is fine.

---

### Post by TaNeK on 2005-01-16
Hi Vesperan!

I'll try doing that, as a kernel recompile just won't work for me, and I, like you, think that the default kernel seem ok :).

I'll post again with results!

---

### Post by cdean on 2005-01-16
Can you post the multimedia device line in lspci for your soundcard?

---

### Post by TaNeK on 2005-01-16
0000:00:0d.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
and :
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)

None of them are working, and the SiS-integrated crap could just as good stay that way, I only use my soundblaster (ensoniq)

---

### Post by TaNeK on 2005-01-16
adding acpi_irq_isa=7 didn't do anything :( no on a laptop :)

---

### Post by cdean on 2005-01-16
Check out lsmod and see if es1371 is loaded.  If it's not, take a look at [http://64.233.167.104/search?q=cache:RtY2AXDOcLwJ:www.macewan.org/index.php%3Fm%3D20040808+Ensoniq+5880+AudioPCI+linux+module&hl=en](http://64.233.167.104/search?q=cache:RtY2AXDOcLwJ:www.macewan.org/index.php%3Fm%3D20040808+Ensoniq+5880+AudioPCI+linux+module&hl=en).

---

### Post by TaNeK on 2005-01-17
Module                  Size  Used by
isofs                  37240  2
rfcomm                 38108  0
l2cap                  25412  5 rfcomm
proc_intf               3840  0
cpufreq_powersave       1792  0
cpufreq_userspace       5336  0
freq_table              4292  0
ds                     18500  0
yenta_socket           21056  0
pcmcia_core            68660  2 ds,yenta_socket
button                  6680  0
ac                      4876  0
battery                 9484  0
ipv6                  258180  8
af_packet              22344  2
ipt_limit               2560  2
ipt_state               2112  140
ipt_LOG                 6592  2
ipt_REJECT              7040  2
ip_conntrack_ftp       72308  0
ip_conntrack_irc       71412  0
ip_conntrack           34432  3 ipt_state,ip_conntrack_ftp,ip_conntrack_irc
iptable_filter          2944  1
ip_tables              18112  5 ipt_limit,ipt_state,ipt_LOG,ipt_REJECT,iptable_filter
audio                  47680  0
8139cp                 20352  0
8139too                25792  0
mii                     5120  2 8139cp,8139too
snd_ens1371            24420  2
sis900                 20100  0
crc32                   4352  3 8139cp,8139too,sis900
snd_intel8x0           35564  3
snd_ac97_codec         67908  2 snd_ens1371,snd_intel8x0
snd_mpu401_uart         7872  1 snd_intel8x0
joydev                  9792  0
tsdev                   7296  0
usbhid                 31680  0
hci_usb                13888  2
bluetooth              48516  7 rfcomm,l2cap,hci_usb
snd_usb_audio          71328  3
snd_rawmidi            25088  3 snd_ens1371,snd_mpu401_uart,snd_usb_audio
snd_seq_device          8136  1 snd_rawmidi
snd_pcm_oss            53160  0
snd_mixer_oss          19520  6 snd_pcm_oss
snd_pcm                95332  4 snd_ens1371,snd_intel8x0,snd_usb_audio,snd_pcm_oss  <----------------- this one right?
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
pwc                    52208  0
videodev                9920  1 pwc
snd_timer              25028  1 snd_pcm
snd                    55524  17 snd_ens1371,snd_intel8x0,snd_ac97_codec,snd_mpu401_uart,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  7 audio,snd
ohci_hcd               21060  0
usbcore               115876  8 audio,usbhid,hci_usb,snd_usb_audio,pwc,ohci_hcd
pciehp                 96236  0
shpchp                 99436  0
pci_hotplug            33776  2 pciehp,shpchp
sis_agp                 8132  1
agpgart                33704  1 sis_agp
floppy                 59348  0
analog                 11808  0
gameport                4672  3 snd_ens1371,snd_intel8x0,analog
pcspkr                  3688  0
rtc                    12600  0
nls_iso8859_1           4096  1
nls_cp850               4928  1
vfat                   14592  1
fat                    46144  1 vfat
nls_cp437               5760  3
ntfs                  101332  1
md                     48648  0
dm_mod                 57660  1
capability              4616  0
commoncap               7168  1 capability
nvidia               4821492  12
parport_pc             34944  1
lp                     10820  0
parport                40904  2 parport_pc,lp
evdev                   9536  0
ide_cd                 41732  2
cdrom                  39648  1 ide_cd
mousedev               10316  1
psmouse                19784  0
reiserfs              241968  1
ext2                   70504  0
ext3                  124712  2
jbd                    61144  1 ext3
mbcache                 9156  2 ext2,ext3
ide_generic             1472  0
ide_disk               18816  8
sis5513                16584  1
ide_core              136344  4 ide_cd,ide_generic,ide_disk,sis5513
unix                   28528  740
fan                     4044  0
thermal                13072  0
processor              17456  1 thermal
font                    8448  0
vesafb                  6624  0
cfbcopyarea             3776  1 vesafb
cfbimgblt               3136  1 vesafb
cfbfillrect             3712  1 vesafb


Looks like it's loaded, and used, I wonder by whom... As I'm not using it, one of the two might be the system sound, right?

---

