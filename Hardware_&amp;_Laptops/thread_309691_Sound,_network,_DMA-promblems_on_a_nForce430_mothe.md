---
title: "Sound, network, DMA-promblems on a nForce430 motherboard"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by rascal on 2006-11-30
Hi!

I just installed Edgy on my new computer, but it seems that there is no sound, no networking and the whole system feels sluggish. Here are the specs:

ASRock ALiveNF6G-DVI which uses the NVIDIA NF6100-430 chipset
AMD Athlon 64 3500+
1GB DDR2

The biggest problem atm seems to be that the hard drive does not go into the DMA mode. Hdparm says:

```

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 312581808, start = 0

```

When I try to turn DMA on, it says

sudo hdparm -d1 /dev/hda

```
/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
```

Copying files makes the cpu usage go to 100% and renders the whole system pretty much useless. DMA was on on this hard drive on my last system.


Also the sound and network abilities are not picked up, even though nVidias site says that they should be. Here's what lspci says:

```
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 03f4 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)
00:07.0 Bridge: nVidia Corporation Unknown device 03ef (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:08.1 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:09.0 PCI bridge: nVidia Corporation Unknown device 03e8 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation Unknown device 03d0 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

It seems that the network adapter is not even detected even though it is enabled in BIOS. Kind of strange...

If someone could point out how to get sound, networking or DMA enabled, I would greatly appreciate it!

---

### Post by rascal on 2006-12-03
Just a quick bump...

More information about my system:

/dev/hda is a Samsung Spinpoint 160GB drive set as master
/dev/cdrom is a LG DVD-burner set as slave

hdparm -tT /dev/hda says

```
/dev/hda:
 Timing cached reads:   2520 MB in  2.00 seconds = 1259.26 MB/sec
 Timing buffered disk reads:    6 MB in  3.24 seconds =   1.85 MB/sec

```

which is really slow.

hdparm -i /dev/hda says


/dev/hda:

```
 Model=SAMSUNG SP1614N, FwRev=TM100-24, SerialNo=S016J10XA29052
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 *mdma2 
 UDMA modes: udma0 udma1 udma2 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7
```

The problem seems to be that ubuntu doesn't realize that the drive supports udma-5 and sets is to multiword dma2. I can manually set the drive to udma5 from bios but it makes no difference. DMA doens't work on my dvd-drive either which makes watching dvd's impossible.

Hope that someone can help me with this problem.

---

### Post by Peter2K on 2006-12-05
Hi,

unfortunable, I have the problem with unrecognized network and audio on an Asus M2N board too. It was a fortune what the SATA-disk is working. The lspci looks similar on my side. It was from a live-CD and I am waiting for the full Dist now.

Regards,
Peter

---

### Post by tommcd on 2006-12-05
Rascal,
You should not have the hard drive and cdrom drive on the same IDE channel if you can avoid it. If the motherboard has 2 IDE channels put the hard drive on IDE 1 and the cdrom on IDE 2. Set them both to master.
For troubleshooting sound problems see this:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by rascal on 2006-12-05
> **tommcd said:**
> Rascal,
You should not have the hard drive and cdrom drive on the same IDE channel if you can avoid it. If the motherboard has 2 IDE channels put the hard drive on IDE 1 and the cdrom on IDE 2. Set them both to master.
For troubleshooting sound problems see this:


Hi and thanks for replying :)

I only have one IDE-bus (strange mobo), but I have tried connecting ONLY the harddrive and the problem doesn't go away. I have also tried switching to a different IDE-cable but it didn't help.

---

### Post by Longfield on 2006-12-05
Hello here,

I have set me up a cool and silet system with an ASUS M2N-MX motherboard, and I have exactly the same problem. The lspci looks exactly the same as yours so the system doesn't recognize the nforce 430 peripherals (and that's why the needed drivers are not loaded and this results in poor performance on disk and no sound and network).

I've added an external PCI Ethernet card to be able to do the updates (and post this message ;) ), but even with the really up to date packages the situation is the same.

It is quite strange because nforce is not brand new, so they must be rather well supported now.

I already have checked if a BIOS update was available, but it is not the case.

I am now going to investigate the silly and hidden BIOS option.

---

### Post by Longfield on 2006-12-05
Hummmm, I think I have found out why it doesn't work.

This is taken from linux-2.6.18 Changelog:

```

Author: Ayaz Abdulla <aabdulla@nvidia.com>
Date:   Thu May 25 13:10:38 2006 -0400

    [PATCH] pci_ids: add new device ids
    
    This patch adds new device ids for MCP61 and MCP65 chips.
    
    Signed-Off-By: Ayaz Abdulla <aabdulla@nvidia.com>
    
    Signed-off-by: Jeff Garzik <jeff@garzik.org>

commit eb91f61b2294ccdb914df255164ada70dbbf2d58

```

Since we have only 2.6.17 kernel with ubuntu, I think we don't have the ids needed to recognize our MCP61 peripherals ...

This is very boring. I don't want to compile a custom kernel for my ubuntu (I moved from Gentoo because I was tired to do this kind of maintenance) but I will need a 2.6.18 kernel to be able to use my whole hardware !

Someone knows when ubuntu new kernel is going to be released ?

---

### Post by rascal on 2006-12-05
> **Longfield said:**
> Hummmm, I think I have found out why it doesn't work.

Since we have only 2.6.17 kernel with ubuntu, I think we don't have the ids needed to recognize our MCP61 peripherals ...


I wonder if the new kernel will also help with the dma-problems and not only sound&network? I might as well try to compile the new kernel when I have some more free time.

---

### Post by wuher on 2006-12-12
> **Longfield said:**
> Someone knows when ubuntu new kernel is going to be released ?

Same problems here with nForce430...If anyone has any info about the new Ubuntu with 2.6.18 kernel release date, please post here. Thanks.

---

### Post by tommcd on 2006-12-13
If you are open to trying another distro, Zenwalk 4.0 uses the 2.6.18 kernel:

[http://zenwalk.org/](http://zenwalk.org/)
Zenwalk is not quite as noob friendly as ubuntu, but it is a light, fast distro with up to date apps. Their repositories do not contain anywhere near as much software as ubuntu's though. Nevertheless, it is pretty col distro, based on Slackware.

---

### Post by Longfield on 2006-12-13
I have tried to compile a 2.6.19 ubuntu kernel using this [howto]("howto") (made a few slight changes).

This has worked quite well. Now my kernel recognizes the devices (can't give you the exact LSPCI output because I'm at work now). There is also the kernel config problem, I've made a make oldconfig from 2.6.17-10 config, but there are still a lot of options to check.

However, this kind of breaks my ubuntu compatibility, because I will have to do extra work to have the NVIDIA binary driver for instance, I won't have kernel security patches backported and so on ...

My question are for the guys who know the ubuntu community and releases well (I've only been here since late Dapper):

- do ubuntu kernel devs backport some patches for hardware support in the official kernel package ?

- who should I ask so that the needed patch is included in edgy official kernel package ?

P.S: There is also the possibility to install a feisty kernel which by default is 2.6.19 at the moment, but I really don't feel like having a feisty package on a edgy install and even less going to feisty now (I want a stable and easy to maintain distro).

---

### Post by Longfield on 2006-12-14
I'm going to answer myself once more (but at least people who have an interest in this thread will have my info).

I got a kernel package update with my work laptop this morning, maybe they have added the patch we need (but this is unsure, since nobody answered me if the kernel devs did integrate that kind of patches).

And if you want to contact the ubuntu kernel guys, here is the address to do it: [email]kernel-team@lists.ubuntu.com[/email]

---

### Post by rascal on 2006-12-14
> **Longfield said:**
> I'm going to answer myself once more (but at least people who have an interest in this thread will have my info).

I got a kernel package update with my work laptop this morning, maybe they have added the patch we need (but this is unsure, since nobody answered me if the kernel devs did integrate that kind of patches).


I dowloaded the updated kernel but still no sound/network.

---

### Post by lanig on 2006-12-31
Compiling the kernel for using this motherboard is quite easy. Something I couldn't obtain is to have at the same time several kernels configured with non-free video driver. 

So first, compilation of the kernel.
First follow the how-to [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

When you are at the make menuconfig step,
if you are booting from a SATA disk
Select the Device drivers item, then Serial ATA (prod) and select...NVIDIA SATA support.
I choosed it as **BUILTIN**  because I thought that the kernel would not be able to mount the root file system but as booting is done through a an initrd, maybe this is not needed.
. Start the compilation and find something interesting to do ;)

At the end of the compilation, install the image but not the headers.

Now a few step that could probably be improved.
Check that the system boots well with your new kernel. If you have no other graphic card than the built-in chip, chances are that your Xorg doesn't start.

remove your ubuntu linux-image (apt-get remove --purge linux-image....) and linux-headers (same way), install your own linux-headers and run the nvidia non free installer.
reboot (or maybe sudo /etc/init.d/gdm start) it should be ok.

There are probably a way of using the nvidia installer to be able to have at the same time several kernels configured with non-free video driver. If you know how, please tell!

---

### Post by victor_c26 on 2007-01-03
I just order the same motherboard from newegg just an hour ago.

So what are the problems really? Just sound and networking don't work?

I'm going to use a SATA drive with the new system. Will the DMA issues carry over, or is that something I shouldn't worry about?

Anything else that's affected by this issue? USB ports, etc?

I have a spare creative Live sound card here, and I'm going to use a Wi-Fi Foxconn card for it anyway.

---

### Post by rascal on 2007-01-07
> **victor_c26 said:**
> I just order the same motherboard from newegg just an hour ago.

So what are the problems really? Just sound and networking don't work?

I'm going to use a SATA drive with the new system. Will the DMA issues carry over, or is that something I shouldn't worry about?

Anything else that's affected by this issue? USB ports, etc?

I have a spare creative Live sound card here, and I'm going to use a Wi-Fi Foxconn card for it anyway.

If you are using a SATA-drive, there shouldn't be any other problems except sound and network.

---

### Post by victor_c26 on 2007-01-08
I completely forgot about the installer. Will DMA be disabled during installation, or just when Ubuntu is installed?

Should I use the alternate installation ISO?

---

### Post by lanig on 2007-01-13
As a followup, I have just discovered some USB problems with this ASROCK ALIVENF6-G  : scanner and FLash card in card reader don't  work.

lspci
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)

If you plan to buy a new motherboard, STAY AWAY of  ASROCK ALIVENF6-G for the time being!
:twisted:

---

### Post by damobbb on 2007-01-17
I have an Asus M2N-MX board with the nForce 430/GeForce 6100 combo and
got networking operational by downloading the source for the 2.6.18.6 kernel
from kernel.org, copying in the config from Ubuntu's 2.6.17 kernel and then
just building and installing that the usual way. See this HOWTO for details:

  [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

I did not relink the "dash"/"bash" shell, did not apply any patches, and did
not change any of the configuration settings for the kernel and it all worked.
Later I installed the video drivers and they worked ("ppracer" was OK) until
I rebooted and now any OpenGL app just brings down X immediately. This
is a known issue with the current video driver, so I might get an older one
and try that out.

Some post somewhere else suggests running "update-pciids" to make "lspci"
produce more meaningful output. I haven't tried it on the nForce 430 machine
yet, but it did download a new "/usr/share/misc/pci.ids" file that has new
entries for that chipset when I tried it on another machine just now.

I have yet to get audio working, but I haven't tried very hard yet. I might
wait until 7.04 (or whatever) to arrive before I waste too much time on it.

---

### Post by damobbb on 2007-01-19
The "update-pciids" thing works fine for the Asus M2N-MX. The "lspci"
command now recognises all of the nVidia bits and bobs.

The nVidia forums suggested that my X crash problem is because the
driver installation is bad (perhaps some update to a package clobbered
the non-DEB installed copy of the driver's GLX library). I'll try installing
the driver again; that should fix it--it worked the first time I installed it.
I just might have to do it on a regular basis.

The audio problems are reported to be corrected by ALSA 1.0.14rc1
which is incorporated into Linux 2.6.20-rc5, so I think I'll just patch my
current kernel with that version of ALSA rather than wait for (K)Ubuntu
to move to 2.6.20. I'm on 2.6.18.6 now, because 2.6.19.1 would not
boot.

---

### Post by damobbb on 2007-01-21
Replying to myself again to record progress....

Finally, I've got networking, video and audio working perfectly on the Asus
M2N-MX (nForce 430/GeForce 6100) board.

As per my posts above, I downloaded and compiled the 2.6.18.6 kernel
and installed it. That sorted out the networking problem. I downloaded
and installed the nVidia video drivers (version 9746) and, after a slight
glitch with an update to the "nvidia-glx" package and a re-install of the
nVidia drivers, video works perfectly. If you are going to use the nVidia
installer, make sure you uninstall the "nvidia-glx" package, as they are
more-or-less the same thing and automatic packages updates break the
nVidia install.

For audio, I downloaded and installed the ALSA drivers, libraries, and
utilities from source according to the instructions on the ALSA site for
the "snd-hda-intel" driver. All that for the latest version 1.0.14-rc2.
(You'll need at least 1.0.14-rc1, from what I've been reading around the
place.) Before that, I uninstalled the "alsa-utils" package (maybe I
should uninstall others, but I do have an older "alsa-base" installed and
maybe that is needed). Once compiled and installed, it still didn't work.
Other sources recommended the following module options:

  options snd-hda-intel model=6stack-dig

Most other posts recommend different options, but they all complain of
stuttering, high-pitched tones, and requiring reboots to recover from
muting a channel. Anyway the above didn't do it either, so I kind of
accidentally ran "alsaconf" and it added a few aliases so that my module
configuration to make it look like this:

  alias snd-card-0 snd-hda-intel
  alias sound-slot-0 snd-hda-intel
  options snd-hda-intel model=6stack-dig

I moved them all into a new "nvidia-asus" file in "/etc/modprobe.d"
that now contains those three lines and this one for the network driver:

  alias eth0 forcedeth

I added "snd-hda-intel" to the "/etc/modules" file just to be sure that the
module is loaded and now audio works perfectly! (I'm listening to some
nice FLAC stuff through Amarok as I type.)  The OpenGL games like
"ppracer" work great with fast frame rates and sound.

My case (an Antec NSX1300) does not support High Definition Audio on
its front panel, but the headphone socket still works OK. The sound
quality from the rear motherboard connector is much better, though.

I'm using Kubuntu 6.10 that came with kernel 2.6.17, but if you want
support for the network, you'll need 2.6.18.x and if you don't want to
install ALSA stuff manually, you'll need 2.6.20 (not yet released). That
could be a long wait if you want it all in an official (K)Ubuntu release,
so the compile-from-source option for the kernel, ALSA and the nVidia
drivers is probably the way to go. Just follow their respective
instructions and it isn't too difficult.

---

### Post by alfredio on 2007-01-22
Hi damobbb,
I want to post some other good news for the m2n-mx owners.

I'm using debian, but I can't see no difference for this topic (since we're both using custom kernels and alsa drivers/utils/tools). So I post my results here, to be in topic :D

I uninstalled both alsa-base and alsa-utils packages. Then I compiled/installed the 1.0.14rc2 from alsa-project.org, and i got the snd_hda_intel module to load correctly without the need of specifying any option.

I believe that when kernel 2.6.20 AND alsa 1.0.14 will be released and packaged, then all m2n-mx related issues shall disappear automagically.

By now the only way I see to get thins working is to compile from source. I was able to compile and install the 2.6.20-rc5 kernel "the debian way" (or ubuntu way, if you prefer) that is using the kernel-package. So this operation did not soiled my installation. However the alsa driver installation was totally not debianized. I think I will continue with a temporary installation, until everything is packaged, and then I'll go for a fresh and clean install.

---

### Post by rascal on 2007-01-25
Just wanted to post and tell that I've upgraded to Feisty, and I'm experiencing no problems with networking, sound or DMA :) There are some other (mainly usability) problems in Feisty so I wouldn't recommend people to upgrade just yet.

---

### Post by cropr on 2007-02-02
I am experiencing the same issue when installing Kubuntu Edgy on a ALiveNF6G motherboard
I have solved it using following steps:
[LIST=1]
[*]I downloaded and burned Feist Herd 2 on a CD
[*]I installed Kubuntu Edgy the normal way
[*]I rebooted the machine using the Feisty CD.  I don't install Feisty but I am using the Feist CD as a Live CD
[*]I mounted the the partition where edgy was installed as /edgy
[*]I copied the /lib/modules directory from the Fiesty Live CD to the /edgy/lib/modules directory
[*]I copied the contents of the /boot directory of Feisty Live  to /edgy/boot directory
[*]I added a section in /edgy/boot/grub/menu.lst before the automatic kernel list, copying an existing section and modifying the copy to reflect the feisty boot files
[*]I did a sudo chroot /edgy and then a grub-install
[*]I rebooted the system selecting the newly created boot option which should be at the top
[*]I have sound and networking in edgy, (I posted this message using edgy)
[/LIST]

---

### Post by leszek44444 on 2007-02-04
Hello everybody,

(sorry for bad english).
i planned to show to a friend how easy it is to install ubuntu(edgy).
No luck, he had a asrock alive nf6g motherboard ... (so no network and no sound).
That will learn me to always verify compatibility.

Like that was already said, the problem is that this motherboard is not compatible with the kernel provided with edgy.
It is possible to put the kernel provided with feisty (the next version of ubuntu still in development), but keep in mind this is a temporary solution which could lead to problems.

So when Feisty will be released (in april), i advice you to reinstall ubuntu.

_**HOWTO**_

* install ubuntu edgy. No sound and no network.
* download ubuntu feisty herd 3 and burn the cd:
[http://cdimage.ubuntu.com/releases/feisty/herd-3/](http://cdimage.ubuntu.com/releases/feisty/herd-3/)
* start the computer with the feisty cd, DON'T INSTALL.
* you now have access to the network. connect to the internet.
* open a terminal and mount the edgy root partition ( / )
(replace /dev/sda1 by the good partition :
/dev/sda1  =  1st partition of the first SATA harddisk,
/dev/sda2  =  2nd partition of the first SATA harddisk,
/dev/hda1  =  1st partition of the Primary ATA Master harddisk, ...)
```
sudo bash
mkdir -p /media/edgy
mount /dev/sda1 /media/edgy
```
* copy the nameservers addresses:
```
cp /etc/resolv.conf /media/edgy/etc/
```
* move to the edgy partition:
```
chroot /media/edgy
```
* you should be able to access internet from there, test with:
```
ping www.google.be
```
* replace the repositories to access the feisty packages and update the packages list:
```
sed -i -e "s/edgy/feisty/g" /etc/apt/sources.list
aptitude update
```
* install the new kernel:
```
aptitude install linux-image-2.6.20-6-generic linux-headers-2.6.20-6-generic
libc6 linux-headers-2.6.20-6 libc6-i686 libc6-dev
linux-restricted-modules-2.6.20-6-generic linux-restricted-modules-common -P
```
* go back to edgy repositories:
```
sed -i -e "s/feisty/edgy/g" /etc/apt/sources.list
aptitude update
```
* reboot

_**Installation of proprietary nvidia drivers**_

the classic installation method of the nvidia drivers don't work (the nvidia drivers in the edgy repositories are compiled for the kernel provided with edgy, if you install them there is a "API Mismatch" error.)

You should then compile the nvidia drivers for your new kernel:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg1.run
sudo sh ./NVIDIA-Linux-x86-1.0-9631-pkg1.run
```

---

### Post by Longfield on 2007-02-10
I had left out that topic for a few weeks because I had no time to work on it.

Now I have installed Feisty (32-bits version, I want w32codecs, skype and wine without to much pain). With Feisty's 2.6.20 kernel, networking, sata, dma work perfectly.

Sound works, but I have a very annoying high-pitched noise on a channel and normal sound on another channel.

From what I have read in the previous, alsa 1.0.14-rc1 is needed. And that's exactly the version which is included by Feisty's kernel: 
```

valentin@lsro1pc307:/usr/src/linux-source-2.6.20$ cat include/sound/version.h
/* include/version.h.  Generated by alsa/ksync script.  */
#define CONFIG_SND_VERSION "1.0.14rc1"
#define CONFIG_SND_DATE " (Tue Jan 09 09:56:17 2007 UTC)"

```

Maybe the problem now comes from alsa-libs ?

---

### Post by vgsangiuliano on 2007-02-13
Hi I installed Ubuntu feisty herd 3 and nvidia video drivers on asrock alivenf6g-Dvi now audio, lan , video works fine but I usb ports on motherboard doesn't work.
Anyone can help me?
Thank you

---

### Post by Longfield on 2007-02-15
I found the fix for my sound problem! 

The snd-hda-intel module needs an option at load time:

Simply add the following line to your /etc/modprobe.d/alsa-base

```
options snd-hda-intel model=3stack

```

Finally I have all my hardware well supported ! Time to enjoy it !

---

### Post by bishop1981 on 2007-05-23
> **Longfield said:**
> I found the fix for my sound problem! 

The snd-hda-intel module needs an option at load time:

Simply add the following line to your /etc/modprobe.d/alsa-base

```
options snd-hda-intel model=3stack

```options snd-hda-intel model=3stack

Finally I have all my hardware well supported ! Time to enjoy it !

Jeah! 
I did the same thing and irritating "high tweeee!" sound disappeared. First I was confused where is my alsa-base file, but I installed it afterwards.
 ```
sudo aptitude install linux-sound-base alsa-base alsa-utils ubuntu-minimal
```
I also downloaded new alsa-driver package form alsa homepage. I had already newest, but I took rc-package [1.0.14rc4.]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc4.tar.bz2")

My sound chip is build-in Nvidia MCP61 and motherboard asus m2n-mx/dvi2. Now I can enjoy movies :popcorn:

---

### Post by nss0000 on 2007-05-23
P2K:

Yep this is a well-known problem. I run an ASUS-m2n/Dapperx64 system - I installed a "legacy" NIC and SB16 workalike soundcard... which work without issue.

---

### Post by brt on 2007-06-25
hmm, strange i still have problems with a brand new m2n-mx on feisty-amd64 :(

onboard net works, but is very slow at rsync from remote servers (30-100KB/s, stalling connections, permanent "eth0 up / down" reported), but lan-transfers are quick  as usual ! 

i checked and tried alot, but the only way i could fix it was to plugin in another NIC, a good old realtek8139 (now i get the usual 300-400KB/s), and i disabled onboard lan in the bios :(

---

