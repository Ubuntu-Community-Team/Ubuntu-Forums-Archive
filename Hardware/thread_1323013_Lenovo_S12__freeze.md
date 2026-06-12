---
title: "Lenovo S12  freeze"
date: 2009-11-11
forum: Hardware
---

### Post by the_MKay on 2009-11-11
Hi,

a few days ago i bought a Lenovo S12 and installed a crypted Ubuntu Karmic on it.
The problem is, that the system freezes really often. But when i hit a key or move the mouse the system moves on.

I have the Lenovo S12 with Atom processor and Intel GMA gfx.

Can anyone help me?

Best regards,
MKay

---

### Post by bejurne on 2009-11-14
I have the same problem. Only that I do not use encryption.

It happens quite randomly, or at least I couldn't spot a pattern yet. Sometimes even during boot.

After hitting a key the system resumes as if nothing happened.

I suspect problems with the power-manager.

---

### Post by the_MKay on 2009-11-14
The same problem occurrs on a second s12 of a friend with Jaunty and Karmic Live-CD.
I also tested a debian live-cd, which shows me a kernel failure message. I used the dialog to send the kernel diagnostic report to the developers :-)
So maybe its a kernel-problem.

---

### Post by bejurne on 2009-11-14
I did some trial and error and came across the BIOS setting "SATA controller working mode". I changed this from AHCI to Compatibility and the problem seems to be gone for now.

Give this a try and see if it works.

---

### Post by the_MKay on 2009-11-14
Hm, i already tried that this morning, but nothing changed. ... I will try it again :)

---

### Post by bejurne on 2009-11-14
It could be pure coincidence for me. As I said this was pure trial and error. 
I have no idea if AHCI could actually be causing this...

Good luck!

---

### Post by kslen on 2009-11-17
I've got the same issues.

I only get the hdd read/write freeze issue when I'm wired to the lan through a cable. AHCI is the current S-ATA mode on my machine and the performance is equally horrific with either setting. Luckily I don't get the chills when connected through WiFi. :)

The overall performance in Ubuntu 9.10 is horrible. All animations barely have a frame a second and it takes forever for windows to redraw.

Being a newbie to Ubuntu I'd appreciate if someone could give some pointers on where to start hunting down a solution. I've read numerous threads about people having trouble with the Intel 945 GME chip, but haven't found anything which has helped so far.

lscpu
```

Architecture:          i686
CPU(s):                2
Thread(s) per core:    2
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 28
Stepping:              2
CPU MHz:               1600.000
L1d cache:             24K
L1i cache:             32K
L2 cache:              512K

```lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```uname -a
```

Linux pluto 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

```lsmod
```

Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
usb_storage            52544  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
lib80211_crypt_tkip     8636  0 
wl                   1272936  0 
snd_hda_codec_realtek   203328  1 
lib80211                6432  2 lib80211_crypt_tkip,wl
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 10272  0 
snd_timer              22276  2 snd_pcm,snd_seq
bridge                 47952  0 
iptable_filter          3100  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
stp                     2272  1 bridge
ip_tables              11692  1 iptable_filter
uvcvideo               59080  0 
bnep                   12060  0 
x_tables               16544  1 ip_tables
lp                      8964  0 
videodev               36736  1 uvcvideo
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
parport                35340  2 ppdev,lp
v4l1_compat            14496  2 uvcvideo,videodev
serio_raw               5280  0 
soundcore               7264  1 snd
btusb                  11856  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
tg3                   109600  0 
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

```Other quirks worth mentioning:
- Flash in fullscreen eats CPUs alive. I am under the impression that this is a common issue and not necessarily related to the overall performance issue Ubuntu seem to have on this machine. 
- Cards inserted into the reader is not automatically mounted by the system.
- Gnome window list won't let me choose a program unless I drop the pointer directly on top of the list item. Moving from one item directly to another item = no go and getting ever more frustrating.

---

### Post by haabingaa on 2009-11-20
I too had this problem with my Lenovo S12.  It seems switching from AHCI to compatibility resolved the issue, so far anyway...

---

### Post by bejurne on 2009-11-20
Just a quick heads up. The problem is gone for me since I switched the AHCI mode.

But I would be really interested in the reasons though. Did anyone get behind this?

---

### Post by Rifester on 2009-11-20
How do you like your S12?   I am considering purchasing one.   Other then the problems mentioned how is the linux compatibility?  Anything you don't like about it?

Mark

---

### Post by dazzlindarryl on 2009-12-16
Just bought one of these netbooks, in the packaging there is an extra insert that mentions switching the SATA controller working mode to compatibility before installing a new OS from a windows XP disk, so it makes sense that compatibility mode makes a difference.

However, after installing Ubuntu 9.10 onto the netbook and having a problem with it freezing randomly and looking at this forum, I switched to compatibility mode and it is still freezing, although it seems to be freezing less often.

It always unfreezes with a touch of the mouse or keyboard, so it isn't terrible, but slightly annoying especially if you leave it copying data.

So, it hasn't completely gone away, but it is happening less often.

---

### Post by kron4eg on 2009-12-20
same problem on my and my friend's lenovo s12, will try to change controller mode

---

### Post by kron4eg on 2009-12-20
> **MRife said:**
> How do you like your S12?   I am considering purchasing one.   Other then the problems mentioned how is the linux compatibility?  Anything you don't like about it?

Mark

working everything, out of box

---

### Post by kron4eg on 2009-12-20
> **kron4eg said:**
> same problem on my and my friend's lenovo s12, will try to change controller mode

just tested, it stopped to freeze, after I switched to Compatibility mode

---

### Post by Dedi Landsman on 2010-03-24
Hi, a few days ago, i just bought the Lenovo S12 [Intel Atom]. wanted to try the Netbook remix, Live USB before going ahead with a full install. yes there are problems, it badly freezes, without even being able to get out of the GUI with ctrl+alt+f2-6 for shutting down at a command line, Key combinations for shut down also wont work, realy bad feeze. i have read now this thread, and want to ask you guys [or anyone else, with the Lenovo S12]: has the switching sata controller to Compatibility mode really solved things, does the freezing attacks really gone away after that, is that the whole issue?
thanks for any help

---

### Post by lyncis on 2010-12-16
Guys from [CentOS forum]("https://www.centos.org/modules/newbb/viewtopic.php?topic_id=25415&forum=37") suggest to add **noapic** kernel option to get rid of freezes. Also, on some other forum I've seen **noapic nolapic** or **noapic acpi=off** options to completely solve this problem with Lenovo S12.

---

### Post by luckyredhot on 2011-11-22
Compatibility mode for IDE does not help.
Kernel option **noapic acpi=off **has perfectly solved an issue with sound freezes on Ubuntu 11.10.
Thank you, guys!

---

