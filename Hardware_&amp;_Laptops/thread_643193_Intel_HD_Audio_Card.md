---
title: "Intel HD Audio Card"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by mcw00t on 2007-12-17
I have no sound on Ubuntu 7.1 using the Intel HD Audio card. When I try to install other drivers, I get this error:

> root@ubuntu:/alsa-driver-1.0.15rc1# ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I'm very new to Linux, so please help me out!

Thanks in advance

---

### Post by XVampireX on 2007-12-17
you need to do: sudo apt-get install build-essential

afterwards do the same ./configure --with-cards=hda-intel and it should be fine...

---

### Post by mcw00t on 2007-12-17
> jon@ubuntu:~/Desktop/alsa-driver-1.0.15rc3$ ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/jon/Desktop/alsa-driver-1.0.15rc3
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


That's the readout I was given, but again, I'm really not sure how to do this...

Sorry to be a pain

---

### Post by mcw00t on 2007-12-17
Sorry for the bump, but I really need help with this.

---

### Post by tgalati4 on 2007-12-17
Normally Intel sound chips work out of the box, sometimes only mild tweaking is needed.

In a terminal, post the output of:

>lspci -vv

and

>lsmod

---

### Post by mcw00t on 2007-12-17
Output of lsmod
> root@ubuntu:/home/jon# lsmod
Module                  Size  Used by
snd_rtctimer            4512  1 
ipv6                  281444  10 
ppdev                  10244  0 
af_packet              25352  2 
acpi_cpufreq           10696  1 
cpufreq_stats           7488  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
battery                11012  0 
button                  9104  0 
container               5504  0 
sbs                    19848  0 
video                  18060  11 
ac                      6276  0 
dock                   11124  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7812  1 ecb
ieee80211_crypt_wep     6272  1 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     13252  0 
parport                38216  3 ppdev,parport_pc,lp
loop                   19588  0 
snd_hda_intel         296480  1 
snd_pcm_oss            43392  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                80516  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35456  0 
snd_seq_midi            9600  0 
snd_rawmidi            25856  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
uvcvideo               49156  0 
snd_seq                54768  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          2304  1 uvcvideo
videodev               29568  1 uvcvideo
ipw3945               119584  1 
snd_timer              24452  3 snd_rtctimer,snd_pcm,snd_seq
v4l1_compat            15364  2 uvcvideo,videodev
sdhci                  18956  0 
nvidia               6222896  26 
hci_usb                19228  0 
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            18560  2 uvcvideo,videodev
mmc_core               28932  1 sdhci
bluetooth              58980  1 hci_usb
ieee80211              36040  1 ipw3945
ieee80211_crypt         7168  2 ieee80211_crypt_wep,ieee80211
i2c_core               26880  1 nvidia
snd                    56708  15 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9312  1 snd
serio_raw               8196  0 
intel_agp              25748  0 
agpgart                35284  2 nvidia,intel_agp
psmouse                40208  0 
shpchp                 34964  0 
pci_hotplug            33460  1 shpchp
evdev                  11136  4 
ext3                  134536  1 
jbd                    59688  1 ext3
mbcache                 9860  1 ext3
sg                     36764  0 
sr_mod                 17956  0 
sd_mod                 30976  4 
cdrom                  37664  1 sr_mod
ata_generic             8580  0 
ohci1394               37040  0 
ieee1394               98360  2 sbp2,ohci1394
tg3                   111236  0 
ata_piix               17668  3 
libata                125424  2 ata_generic,ata_piix
scsi_mod              148844  5 sbp2,sg,sr_mod,sd_mod,libata
uhci_hcd               26512  0 
ehci_hcd               36108  0 
usbcore               139912  5 uvcvideo,hci_usb,uhci_hcd,ehci_hcd
thermal                14600  0 
processor              32200  2 acpi_cpufreq,thermal
fan                     5892  0 
fuse                   48404  3 
apparmor               41624  0 
commoncap               8320  1 apparmor


lspci output is too big to copy from terminal (it cuts off lost of it)

---

### Post by mcw00t on 2007-12-17
> root@ubuntu:/home/jon# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0e:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)


lspci without -vv

---

### Post by xeth_delta on 2007-12-17
please post the output of:

```
lspci | grep -i audio
```

Did you install build-essential as XVampireX said?

Xeth

---

### Post by mcw00t on 2007-12-17
> root@ubuntu:/home/jon# lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Yes I did, and I was presented with:

> The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux). 
At the end of the configure script (3rd post for full output)

---

### Post by tgalati4 on 2007-12-17
So we have determined that you have on-board Intel ICH8 Intel HD audio and you have the modules loaded (and a crapload of other stuff).

Have you tried any of the Intel switches?

I have an earlier version (ICH7) 5.1 HD audio.

Here are the switches that I use in my /etc/modprobe.d/alsa-base

options snd-hda-intel model=5stack-digout

This activates 5.1 sound, the front headphone and mic jacks and the digital output.

There are a lot of switches to choose from.  You need to find out what the actual hardware codec is.  For me, it's an ALC880.

ALC880
3stack 3-jack in back and a headphone out
3stack-digout 3-jack in back, a HP out and a SPDIF out
5stack 5-jack in back, 2-jack in front
5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
6stack 6-jack in back, 2-jack in front
6stack-digout 6-jack with a SPDIF out
w810 3-jack
z71v 3-jack (HP shared SPDIF)
asus 3-jack (ASUS Mobo)
asus-w1v ASUS W1V
asus-dig ASUS with SPDIF out
asus-dig2 ASUS with SPDIF out (using GPIO2)
uniwill 3-jack
fujitsu Fujitsu Laptops (Pi1536)
F1734 2-jack
lg LG laptop (m1 express dual)
lg-lw LG LW20/LW25 laptop
tcl TCL S700
clevo Clevo laptops (m520G, m665n)
test for testing/debugging purpose, almost all controls can be
adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y
auto auto-config reading BIOS (default)

Only after you have tried all of these switches and they still don't work, then I would resort to compiling more recent drivers.  Also to continue compiling you need to verify that the source code directories exist or change their location with the --with-kernel=dir option.

---

### Post by mcw00t on 2007-12-17
Sorry, but I have no idea how I would go about doing that.

I had put this at the bottom as what was meant to be a fix:

options snd-hda-intel model=auto

---

### Post by xeth_delta on 2007-12-17
Do you have the headers for your kernel installed?

You can find out what kernel version you have with:

```
uname -r
```

Check whether you have the kernel headers for the version you are running::

```
aptitude search linux-headers
```

If you don't have them, install them:

```
sudo aptitude install linux-headers-<your version>
```

Xeth

---

### Post by mcw00t on 2007-12-17
Right, it turns out I didn't have the headers installed.

I've now downloaded and installed them. What do I do from here?

---

### Post by xeth_delta on 2007-12-17
> **mcw00t said:**
> Right, it turns out I didn't have the headers installed.

I've now downloaded and installed them. What do I do from here?

configure as you were doing before, in the alsa driver directory:

```
./configure
```

then compile
```
make
```

install
```
sudo make install
```

Do not delete the source directory, as you will need it if you want to remove them.

---

### Post by xeth_delta on 2007-12-17
Also, make sure you have a directory / soft link called /usr/src/linux. If it does not exist, create it:

```
cd /usr/src
sudo ln -s linux-<your version> linux
```

---

### Post by mcw00t on 2007-12-17
Right, I've managed to run the configure, make, make install scripts, but I don't know what to to when it says to edit my kernel module. These are the instructions I've left to do:

7) Edit your kernel module config (either /etc/modprobe.conf or
   /etc/modules.conf, depending on the kernel version). If you are not
   sure, what to do, you may try the alsaconf script available in
   the alsa-utils package.

8 ) Run 'modprobe snd-xxxx' where xxxx is the name of your card.
   Note: All ALSA ISA drivers support ISA PnP natively, so you don't need
         isapnptools any more.  Don't use both together.  It will
         conflict.  For disabling the ALSA ISA PnP support, specify
         --with-isapnp=no configure switch.

---

### Post by tgalati4 on 2007-12-17
>sudo nano /etc/modules

Put the appropriate modules command at the bottom of the file.

As an alternative or in addition, you can put the option switches that I discussed earlier in 

>sudo nano /etc/modprobe.d/alsa-base

Since the default behavior is:

options snd-hda-intel model=auto

You need to be more creative with your switch selection.  Try 5stack.

---

### Post by mcw00t on 2007-12-17
What would be the appropriate command? or where would I find the command if it's not arbitary?

---

### Post by xeth_delta on 2007-12-17
May I suggest installing the alsa utilities? They should include, if I am not mistaken, alsaconf, which will help you configure the sound:

```
sudo alsaconf
```

---

### Post by mcw00t on 2007-12-17
Again, I apologise for my ignorance, but how would I go about this? If I type in 'sudo alsaconf' is comes up with a bash command not found

---

### Post by xeth_delta on 2007-12-17
> **mcw00t said:**
> Again, I apologise for my ignorance, but how would I go about this? If I type in 'sudo alsaconf' is comes up with a bash command not found

Sorry about that. You have to download and install the alsa utilities: [http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download")

Unpack with tar -xzf, enter the directory:
```
./configure
make
sudo make install
```

---

### Post by mcw00t on 2007-12-17
Ah right! What version do you recommend? Or does it not matter?

---

### Post by xeth_delta on 2007-12-17
> **mcw00t said:**
> Ah right! What version do you recommend? Or does it not matter?

I'd say use the stable one, 1.0.15. While you are it, you could also install an updated set of libraries (alsa=lib). Same steps as explained in my previous post.

---

### Post by mcw00t on 2007-12-17
I have the libraries installed now, however, when I go to install the utilities, I get this

checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

---

### Post by xeth_delta on 2007-12-17
> **mcw00t said:**
> I have the libraries installed now, however, when I go to install the utilities, I get this

checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

You nedd to install some extra packages, I'll be back soon with their names.

---

### Post by xeth_delta on 2007-12-17
Try this:

```
sudo aptitude install libncurses5 libncurses5-dev
```

If you look at the error "checking for initscr in -lncurses... no", the "-lncurses" refers to the ncurses library, **lib**ncurses the linker will link against.

---

### Post by mcw00t on 2007-12-17
Yeah, I understand that one now, got ncurses installed, and am installing the utilities as I type this!

---

### Post by mcw00t on 2007-12-17
right, i've run alsaconf, owever, still no sound. Is there any way of unmuting that I may need to do other than in the mixer?

---

### Post by xeth_delta on 2007-12-17
> **mcw00t said:**
> right, i've run alsaconf, owever, still no sound. Is there any way of unmuting that I may need to do other than in the mixer?

Did alsaconf recognize your card? Check whether you have /etc/init.d/alsasound or /etc/init.d/alsa. If you do, try:
```
sudo /etc/init.d/alsasound restart
```
or
```
sudo /etc/init.d/alsa restart
```

What laptop model and brand do you have? You can also try alsamixer. and if none of those work, post your current output from lsmod.

---

### Post by mcw00t on 2007-12-17
jon@ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_intel         296480  1 
snd_pcm_oss            43392  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                80516  2 snd_hda_intel,snd_pcm_oss
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35456  0 
snd_seq_midi            9600  0 
snd_rawmidi            25856  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54768  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56708  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9312  1 snd
ipv6                  281444  10 
ppdev                  10244  0 
acpi_cpufreq           10696  1 
cpufreq_stats           7488  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
af_packet              25352  2 
battery                11012  0 
button                  9104  0 
container               5504  0 
sbs                    19848  0 
video                  18060  11 
ac                      6276  0 
dock                   11124  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7812  1 ecb
ieee80211_crypt_wep     6272  1 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     13252  0 
parport                38216  3 ppdev,parport_pc,lp
loop                   19588  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
uvcvideo               49156  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29568  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
nvidia               6222896  26 
hci_usb                19228  0 
v4l2_common            18560  2 uvcvideo,videodev
bluetooth              58980  1 hci_usb
ipw3945               119584  1 
sdhci                  18956  0 
ieee80211              36040  1 ipw3945
i2c_core               26880  1 nvidia
mmc_core               28932  1 sdhci
ieee80211_crypt         7168  2 ieee80211_crypt_wep,ieee80211
intel_agp              25748  0 
serio_raw               8196  0 
agpgart                35284  2 nvidia,intel_agp
psmouse                40208  0 
shpchp                 34964  0 
pci_hotplug            33460  1 shpchp
evdev                  11136  4 
ext3                  134536  1 
jbd                    59688  1 ext3
mbcache                 9860  1 ext3
sg                     36764  0 
sr_mod                 17956  0 
cdrom                  37664  1 sr_mod
sd_mod                 30976  4 
ata_generic             8580  0 
tg3                   111236  0 
ohci1394               37040  0 
ieee1394               98360  2 sbp2,ohci1394
ata_piix               17668  3 
libata                125424  2 ata_generic,ata_piix
ehci_hcd               36108  0 
uhci_hcd               26512  0 
usbcore               139912  5 uvcvideo,hci_usb,ehci_hcd,uhci_hcd
scsi_mod              148844  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                14600  0 
processor              32200  2 acpi_cpufreq,thermal
fan                     5892  0 
fuse                   48404  3 
apparmor               41624  0 
commoncap               8320  1 apparmor


my output, and it's a custom built laptop.

---

### Post by xeth_delta on 2007-12-17
Is you laptop based on any particular brand? I ask you this because you might need to modify a file and change some lines:

```
sudo nano /etc/modprobe.d/alsa-base
```

For instance, I use on my laptop the option

```
options snd-hda-intel model=5
```
which I found recommended for my Macbook in the file: alsa-driver-1.0.15/alsa-kernel/Documentation/ALSA-Configuration.txt. It should be in the driver source package you downloaded.

---

### Post by mcw00t on 2007-12-17
It's not as far as I know, I can list the specs if it helps?

---

### Post by xeth_delta on 2007-12-17
> **mcw00t said:**
> It's not as far as I know, I can list the specs if it helps?

Yes, please list them. Do you perhaps have a link to the barebones system?

So, do you have **/etc/init.d/alsasound**? If so, try again restarting and then run **dmesg**. Please post some of the last lines **dmesg** will return.

---

### Post by mcw00t on 2007-12-17
Intel Core 2 Duo T7300 2.00GHz
2Gb 667MHz Corsair DDR2 RAM
Nvidia GeForce 8600M GT
160GB HDD (60GB Linux Partition, incl. Swap Space)
Intel ICH8 HD Sound Card

Any more specs?

and yes I do have that, I'l restart it now.

---

### Post by mcw00t on 2007-12-17
From dmesg

[   33.114263] EXT3 FS on sda6, internal journal
[   33.443793] ieee80211_crypt: registered algorithm 'WEP'
[   34.619908] No dock devices found.
[   34.633831] ACPI: AC Adapter [ACAD] (on-line)
[   34.655396] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   34.666622] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   34.733436] input: Power Button (FF) as /class/input/input3
[   34.733452] ACPI: Power Button (FF) [PWRF]
[   34.733490] input: Lid Switch as /class/input/input4
[   34.733502] ACPI: Lid Switch [LID0]
[   34.733533] input: Power Button (CM) as /class/input/input5
[   34.733544] ACPI: Power Button (CM) [PWRB]
[   34.898883] ACPI: Battery Slot [BAT1] (battery present)
[   34.952221] NET: Registered protocol family 17
[   36.035908] ppdev: user-space parallel port driver
[   36.240991] NET: Registered protocol family 10
[   36.241055] lo: Disabled Privacy Extensions
[   36.411474] audit(1197940066.708:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5112 profile="/usr/sbin/cupsd"
[   36.524144] apm: BIOS not found.
[   36.830682] Failure registering capabilities with primary security module.
[   46.333960] eth1: no IPv6 routers present
[  742.209045] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[  742.429533] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 23
[  742.429557] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 2335.483691] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 2335.695232] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 23
[ 2335.695293] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 2335.744730] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS.

---

### Post by xeth_delta on 2007-12-17
Hmmm, there seems to be a problem:
> **mcw00t said:**
> [ 2335.744730] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS.

Try the following and tell me the error messages:
```
sudo /etc/init.d/alsasound stop
```

Then load the alsa module manually:

```
sudo modprobe snd-hda-intel
```

---

### Post by xeth_delta on 2007-12-17
Ok, I found something in alsa-driver-1.0.15/alsa-kernel/Documentation/ALSA-Configuration.txt:

```

Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
                ATI SB450, SB600, RS600,
                VIA VT8251/VT8237A,
                SIS966, ULI M5461

        ALC268
          3stack        3-stack model
          toshiba       Toshiba A205
          acer          Acer laptops
          auto          auto-config reading BIOS (default)

```

So, I'd say you can try those four options in /etc/modprobe.d/alsa-base, for example:
```
options snd-hda-intel index=0 model=acer
```

Then restart the alsasound and check dmesg

---

### Post by mcw00t on 2007-12-18
Oh Dear is all I can really say to tis problem.

I spoke to a linux user today, and he had a look at it for me, and this is what he said:

"Well, it looks like it's outputting, but to where, I have no idea, it just isn't the speakers."

---

### Post by xeth_delta on 2007-12-18
> **mcw00t said:**
> Oh Dear is all I can really say to tis problem.

I spoke to a linux user today, and he had a look at it for me, and this is what he said:

"Well, it looks like it's outputting, but to where, I have no idea, it just isn't the speakers."

Can you confirm that it is only the output? can you use an audio player and not get any complain from it about a problem with the driver?

From the dmesg output you posted, it seemed like there were problems when loading the modules. Did you get to try using the options I suggested?

---

### Post by mcw00t on 2007-12-18
> **xeth_delta said:**
> Can you confirm that it is only the output? can you use an audio player and not get any complain from it about a problem with the driver?

From the dmesg output you posted, it seemed like there were problems when loading the modules. Did you get to try using the options I suggested?

Well, he suggested I remove alsa completely, which I did, the reinstall ALL of the drivers & base. Then I ran a normal test from the utils, which is when he said 'it seems as though it thinks it's outputting, but it must be to the wrong place'

And yes, when using Audacious I get no errors at all, just no sound either!

---

### Post by xeth_delta on 2007-12-18
> **mcw00t said:**
> Well, he suggested I remove alsa completely, which I did, the reinstall ALL of the drivers & base. Then I ran a normal test from the utils, which is when he said 'it seems as though it thinks it's outputting, but it must be to the wrong place'

And yes, when using Audacious I get no errors at all, just no sound either!

Can you check the output of dmesg when restarting alsasound. Is the error message still there?

For example, the message I get in my working system is:

```
[   16.732000] hda_codec: STAC922x, Apple subsys_id=106b2200
```

[EDIT]: > Then I ran a normal test from the utils, which is when he said 'it seems as though it thinks it's outputting, but it must be to the wrong place'
And yes, when using Audacious I get no errors at all, just no sound either!
As said, that might be caused by a wrong configuration. Sorry, for repeating, please try different option combinaions and restart alsasound, if you have not tried that yet.

---

### Post by mcw00t on 2007-12-18
ok, I have no entry for hda_codec, would this be easier for you if you were to remote desktop? because really, I'm getting desparate now.

---

### Post by xeth_delta on 2007-12-18
> **mcw00t said:**
> ok, I have no entry for hda_codec, would this be easier for you if you were to remote desktop? because really, I'm getting desparate now.

I am not sure that is quite a good idea, from a security point of view. :) Should not let a stranger access your system, especialy with root privileges.

Let's do something else, post the contents of /etc/modprobe.d/alsa-base. I will show you what to modify.

---

### Post by mcw00t on 2007-12-18
> **xeth_delta said:**
> I am not sure that is quite a good idea, from a security point of view. :) Should not let a stranger access your system, especialy with root privileges.

Let's do something else, post the contents of /etc/modprobe.d/alsa-base. I will show you what to modify.

Hey, I trust you you could have told me commands that would have destroyed my system a million times over by now and I'd be none the wiser (other than the fact nothing would work)!

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd$
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --q$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe$
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --q$
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modp$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq$
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto

NOTE: I tried changing the last part to acer/3sack etc, but to no avail!

---

### Post by xeth_delta on 2007-12-18
Ok, first make a copy of the file, just in case, have it as back-up. Just be patient a bit longer, i think you're getting close to a working sound system.

Now, make your file look like this:
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd$
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --q$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe$
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --q$
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modp$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq$
# Prevent abnormal drivers from grabbing index 0
#options snd-bt87x index=-2
#options cx88-alsa index=-2
#options saa7134-alsa index=-2
#options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
#options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto
install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel
```

After saving the file as above:
```
sudo /etc/init.d/alsasound restart
```
If it does not work, post the last lines that dmesg will print.

---

### Post by mcw00t on 2007-12-18
I got errors

root@ubuntu:/home/jon# /etc/init.d/alsasound restart
Shutting down sound driver: done
Starting sound driver: snd-hda-intel done
/usr/sbin/alsactl: set_control:961: failed to add user control #15 (Device or resource busy)

and for dmesg this is all I get

[ 4364.291957] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 4364.508148] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 23
[ 4364.508175] PCI: Setting latency timer of device 0000:00:1b.0 to 64

---

### Post by xeth_delta on 2007-12-18
Ah, I just noticed... Your lines are ending in a $
Did you copy from nano? open the file with another editor, say gedit and post the contents again.

---

### Post by mcw00t on 2007-12-18
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto

There we go

---

### Post by xeth_delta on 2007-12-18
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
#options snd-bt87x index=-2
#options cx88-alsa index=-2
#options saa7134-alsa index=-2
#options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
#options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto
install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel

```

Try again :)

---

### Post by mcw00t on 2007-12-18
I can't figure out a way of changing it without using nano. Is it just the last line that's been added, or is there more to it than that?

---

### Post by xeth_delta on 2007-12-18
> **mcw00t said:**
> I can't figure out a way of changing it without using nano. Is it just the last line that's been added, or is there more to it than that?

The last line and commenting out (#) several other option lines for other soundcards.

you can open the file as follows:
```
sudo gedit /etc/modprobe.d/alsa-base
```

---

### Post by tgalati4 on 2007-12-18
You might need braces {} to match the syntax found earlier in the file:

$CMDLINE_OPTS && { /sbin . . .

I assumed you tried a simple blacklist of cs46XX?

---

### Post by mcw00t on 2007-12-18
Right, I restarted it, and I got an error saying "No Volume Control GStreamer plugins and/or devices found"

---

### Post by xeth_delta on 2007-12-18
Hmmm, I am not sure what else to say. What is the output of dmesg after the restart?

Please, try also the option:
```
options snd-hda-intel index=0 model=...
```
Where you replace the dots with the different possible models for your card. Same process.

---

### Post by mcw00t on 2007-12-18
jon@ubuntu:~$ dmesg
[ 4364.291957] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 4364.508148] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 23
[ 4364.508175] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 6833.104162] ACPI: PCI interrupt for device 0000:00:1b.0 disabled


That's it...

---

### Post by xeth_delta on 2007-12-18
> **mcw00t said:**
> jon@ubuntu:~$ dmesg
[ 4364.291957] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 4364.508148] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 23
[ 4364.508175] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 6833.104162] ACPI: PCI interrupt for device 0000:00:1b.0 disabled


That's it...

No mention of hda-intel... Let's see:
Please post the output of:
```
lsmod | grep -i snd
```
and
```
sudo modprobe snd-hda-intel
```

---

### Post by mcw00t on 2007-12-18
snd_page_alloc         11400  0 (for lsmod)

jon@ubuntu:~$ sudo modprobe snd-hda-intel
[sudo] password for jon:
sh: /lib/alsa/modprobe-post-install: not found
FATAL: Error running install command for snd_hda_intel

(for modprobe)

---

### Post by xeth_delta on 2007-12-18
> **mcw00t said:**
> snd_page_alloc         11400  0 (for lsmod)

jon@ubuntu:~$ sudo modprobe snd-hda-intel
[sudo] password for jon:
sh: /lib/alsa/modprobe-post-install: not found
FATAL: Error running install command for snd_hda_intel

(for modprobe)

It is because of the last line. Comment out the part containing /lib/alsa/modprobe-post-install:
```
install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && #/lib/alsa/modprobe-post-install snd-hda-intel
```

---

### Post by mcw00t on 2007-12-18
Comment out? Sorry, not familiar with terminology yet!

---

### Post by mcw00t on 2007-12-18
Ok, weird stuff happened.

After running modprobe, I re-ran lsmod, and got the following output:

jon@ubuntu:~$ lsmod | grep -i snd
snd_rtctimer            4512  1 
snd_hda_intel         296480  1 
snd_pcm_oss            43392  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                80516  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35456  0 
snd_seq_midi            9600  0 
snd_rawmidi            25856  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54768  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56708  15 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9312  1 snd

---

### Post by xeth_delta on 2007-12-18
Ok, modules are loaded now. I am out of ideas, sorry. Hopefully someone with more knowledge on the issue will write soon.

For now what what I can suggest is to try different combinations of the options I gave you earilier (also with index=0), restart aslasound try a sound player. If it does not work check dmesg for errors.

Let us know how it goes.

---

### Post by wholias809 on 2007-12-18
I'm really sorry if this has been posted before but this is what worked for me with a similar card, IH7, but it is listed for the IH8 i believe

found on this thread
[http://ubuntuforums.org/showthread.php?t=623764](http://ubuntuforums.org/showthread.php?t=623764)

this link
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)


pretty much says this 
system->administration->software sources
from there go to the updates tab,
if its not already, check unsupported updates

then go to the terminal and type

sudo apt-get install linux-backports-modules-generic

once again sorry if this is double post

---

### Post by Bartje on 2007-12-19
What the hell!!!!! I had a hard time getting my soundcard working after upgrading to Gutsy, now there's an update, and it doesn't work anymore!!!!!! rebuilding my Alsa again! Will I have to do this every time there's an update??????

---

### Post by mcw00t on 2007-12-19
YES! I have sound working! Changing the part in bold from auto:

options snd-hda-intel model=**acer**
install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel 

in alsa-base seemed to do the trick, however instead of restarting just alsa, I had to reboot.

I'm quite obviously very happy about this, however, I still don't have working microphones, any ideas for this?

---

### Post by xeth_delta on 2007-12-19
> **mcw00t said:**
> YES! I have sound working! Changing the part in bold from auto:

options snd-hda-intel model=**acer**
install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel 

in alsa-base seemed to do the trick, however instead of restarting just alsa, I had to reboot.

I'm quite obviously very happy about this, however, I still don't have working microphones, any ideas for this?

Great to know that! About the microphone, probably some configuration option, too. That is beyound me, though. Maybe it would be a good idea to create a new thread for that problem.

---

### Post by xeth_delta on 2007-12-19
> **Bartje said:**
> What the hell!!!!! I had a hard time getting my soundcard working after upgrading to Gutsy, now there's an update, and it doesn't work anymore!!!!!! rebuilding my Alsa again!!!!!!! Will I have to do this every time there's an update??????

Hmmm, it might be that you need to recompile the drivers when the kernel is updated. It is not that difficukt, though.

As far as I know, the reason for this is that the interface between the kernel and a given module has to correspond with its version.

---

### Post by xeth_delta on 2008-01-03
An update on this thread. People having problems with an intel soundcard which includes a realtek codec, and possibly other cards containing also a realtek codec might want to have a look at the following link: [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

---

