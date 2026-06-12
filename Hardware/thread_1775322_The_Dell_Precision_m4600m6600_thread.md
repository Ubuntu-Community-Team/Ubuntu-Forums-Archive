---
title: "The Dell Precision m4600/m6600 thread"
date: 2011-06-04
forum: Hardware
---

### Post by polypus74 on 2011-06-04
I'm thinking about getting a dell precision m4600 and wondering if anybody has yet tried to install ubuntu (or some other distro) one of these puppies. 

I've been trying to get the drones at dell chat to give me information on the status of the certified version as outlined here:

[http://www.ubuntu.com/certification/hardware/201101-6977](http://www.ubuntu.com/certification/hardware/201101-6977)

But of course have learned nothing.

I'm thinking about just jumping the gun, buying one, and just trying my luck, but was hoping to get some feedback off of you guys first, and to start a thread where news about install woes could be posted as it trickles in. 

Is it a good idea at this point to just buy it, or should I wait? 

cheers,
_c

---

### Post by mjbommar on 2011-06-22
Just ordered one Monday, should be arriving in the next two weeks.  I'll let you know how it goes.

I know the M4600 supports RHEL and Ubuntu in some regions.  I've had smooth sailing on the M4300/4400/4500 with Ubuntu over the last few years, so I expect more of the same.

---

### Post by pmcloone on 2011-06-23
Hi,

Got one of these for work a few days ago, immediately wiped windows off it and put ubuntu on, running 10.10 (I would have gone with the most recent - but I have yet to find a machine running 11.04 that can successfully connect to a Xilinx JTAG pod). The certification is correct when it says Hibernate doesn't work.

The other problem is that my system has a ATI Mobility FirePro 5950 - and while the proprietary driver provided via the "Additional Drivers" menu does work, it places an "AMD Unsupported hardware" logo at the bottom right-hand corner that I haven't figured out yet how to get rid of. (It's not a problem unique to this configuration and seems to have propped up elsewhere).

I asked Dell tech support and was immediately dismissed with an unsupported configuration (I guess the certified one is for an nvidia card, after all). I also contacted AMD and did get a response, but they wanted a picture and I have yet to remember to bring a camera, since the watermark is in hardware and doesn't appear on screen captures. Oy.

All in all, though, works fine besides the watermark and hibernate issues.

---

### Post by pvandoren on 2011-06-28
We just received one M6600 today, and are installing Ubuntu 10.04 LTS right now.  (Keeping to LTS due to the tools we use).  

The first glitch I've seen so far, is the ethernet jack wasn't recognized when plugged into the docking station but the wireless is working.. (Which is funny because it's usually the other way around)..  I'm downloading the normal updates now, and will look into this issue and give you a status when I know more.

Pete

---

### Post by metos on 2011-06-29
Hello

I installed ubuntu 11.04 64b on a M4600 (with ati video card) and I experience some problems.
Many times, suspend cannot be resumed. screen still black and the keyboard is not responding (caps or num lock don't react), it there just the keyboard backlight that react on keypress
When suspend success to resume, I've some process using high cpu load

In these 2 cases, I have to power down and restart to be able to work.

---

### Post by pvandoren on 2011-06-29
[QUOTE=pvandoren;10992196The first glitch I've seen so far, is the ethernet jack wasn't recognized when plugged into the docking station but the wireless is working..[/QUOTE]

Ok got the Ethernet working had to install the latest e1000e drivers manually.  They are part of the Maveric backport, but that had another issue in that the system would hang on restarts.

Other issue found is the ATI M8900 propriotary drivers are not out yet, but installed the latest catalysis drivers and it works.  There's some issue with multi-display, in that it didn't like one of the external monitors for some reason, (Seemed like it was numbering it wrong) but I finally got it in a configuration it liked.

Pete

---

### Post by pmcloone on 2011-06-30
Yeah, metos, I've had similar instability issues even without trying to change power states. The recent kernel update seems to have cleared them up, though.

Additionally, beyond my problems outlined earlier with the watermark and being unable to hibernate, I also have yet to get any sound of the built-in speakers. Haven't tried headphones or anything like that yet. Keep forgetting to bring them in.

---

### Post by metos on 2011-07-01
I just updated some packages about ati and xserver
I'll see if that fix my problem

I olso noticed other troubles
- when I ask for restart the computer, it freezes on shutdowning logs. I have to maintain power button down until il stop and then power up to start
- I sometimes had this same issue on shutdown request, but most of the times the computer stops correctly

other fact, I cant ajust touchpad pointer speed or acceleration
I searched on the web, tried many additionnal pointer manager, but that not affect the pointer moving.

and, so far, I never noticed sound problem.

---

### Post by Salline on 2011-07-05
Hi folks,

first time post for me here, so please be gentle... ;)

I received my new m4600 about two weeks ago, swapped the 500GB HDD for an SSD and threw in the 11.04 DVD.
Apart from hibernate everything works quite fine and the system is blazingly fast.
However, I also occasionally encounter the freeze during shutdowns/reboots but it's not that much of an issue for me since it seems the system halts anyway, it just doesn't power off/reboot properly. Also happens only infrequently.

Also, I noticed that the hibernate issues started when I switched from the i7-GPU to the nVidia Quattro in the BIOS (can't remember the name of the option right now, but the description said something about "only use this with Win7"). Before that, hibernating worked fine but 3D performance was horrible (well, enough for Unity but not much more).

Ah well, maybe a kernel update will fix this and hopefully soon.

Another thing that really irks me is that there don't seem to be any events generated when docking/undocking the laptop, making it impossible to switch monitor configurations on the fly. This isn't much of an issue when docking, but when you undock the notebook, the internal screen will stay black, leaving me unable to switch that using the NVidia control panel.

I noticed, however, that when docking there seems to be a new USB hub (or something) being registered and ACPI events for this are generated. Does anyone here have an idea on how that might be usable in order to trigger some scripts for switching the monitor configurations on the fly?
I appreciate any help on this... =)


Kind regards,

Salline

P.S.: Anybody know of an adapter for the media bay so I could put in the original HDD alongside with my SSD? Since I usually don't need the builtin DVD drive I'd just put that one into an external box...

---

### Post by gkcr2d2 on 2011-07-21
> **Salline said:**
> 
Also, I noticed that the hibernate issues started when I switched from the i7-GPU to the nVidia Quattro in the BIOS (can't remember the name of the option right now, but the description said something about "only use this with Win7"). Before that, hibernating worked fine but 3D performance was horrible (well, enough for Unity but not much more).


The option should be named "nvidia Optimus".
(this option switch automatically IGP card and Nvidia quadro card)

---

### Post by pan88 on 2011-07-22
Hi together. 

I'm new to the forum. I found this thread via google. I own a precision m4600 for about a week now.

I also had the restart problem. After using google for about 5 hours I found a solution that worked for me.

In /etc/default/grub I added in the line GRUB_CMDLINE_LINUX_DEFAULT="reboot=pci"

After that just update-grub2 and restarting is working for me now.

I still have some problems with the touchpad. It is not recognized as a touchpad, just as a mouse. For that reason it is not disabled when I use the keyboard and thats really annoying. Anybody an idea how to fix that?

Thx.

Regards pan

---

### Post by serxyz on 2011-07-22
Hello,

I've just installed Ubuntu 10.04.3 on my new DELL precision M6600. I have the same problem reported above (#pvandoren) with the wired eth0 internet connexion, it does not work. (The wireless works fine, though). I post below some relevant information (lspci, ifconfig, lshw). I would appreciate any suggestion. Is it a matter of some missing drivers?

Thanks a lot in advance. 

[Ser]

=================================================================
$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Cougar Point KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.7 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 8 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c4f (rev 04)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 0e3b (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0beb (rev a1)
03:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
0a:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
0b:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 11f7 (rev 05)
0b:00.1 SD Host controller: O2 Micro, Inc. Device 8320 (rev 05)
0b:00.2 Mass storage controller: O2 Micro, Inc. Device 8330 (rev 05)
=================================================================
$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31296 (31.2 KB)  TX bytes:31296 (31.2 KB)

pan0      Link encap:Ethernet  HWaddr 36:c6:83:03:45:27  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:d7:d4:b2:c0  
          inet addr:18.111.19.22  Bcast:18.111.31.255  Mask:255.255.224.0
          inet6 addr: fec0::9:224:d7ff:fed4:b2c0/64 Scope:Site
          inet6 addr: 2002:126f:18af:9:224:d7ff:fed4:b2c0/64 Scope:Global
          inet6 addr: fe80::224:d7ff:fed4:b2c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20171634 (20.1 MB)  TX bytes:331739 (331.7 KB)
=================================================================
$ sudo lshw -C network; lsb_release -a; rfkill list
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:e1e00000-e1e1ffff memory:e1e80000-e1e80fff ioport:8040(size=32)
  *-network
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:d4:b2:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=18.111.19.22 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:e1d00000-e1d01fff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
=================================================================

...................................................................
> **pvandoren said:**
> We just received one M6600 today, and are installing Ubuntu 10.04 LTS right now.  (Keeping to LTS due to the tools we use).  

The first glitch I've seen so far, is the ethernet jack wasn't recognized when plugged into the docking station but the wireless is working.. (Which is funny because it's usually the other way around)..  I'm downloading the normal updates now, and will look into this issue and give you a status when I know more.

Pete

---

### Post by pan88 on 2011-07-26
Hi again.

I have some problem with the cpu frequency.

cpufreq-info:
======================================================
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.20 GHz, 2.00 GHz, 1.90 GHz, 1.80 GHz, 1.70 GHz, 1.60 GHz, 1.50 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz, 1.10 GHz, 1000 MHz, 900 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 1.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.20 GHz:0,00%, 2.20 GHz:0,00%, 2.00 GHz:0,00%, 1.90 GHz:0,00%, 1.80 GHz:6,83%, 1.70 GHz:0,19%, 1.60 GHz:0,21%, 1.50 GHz:0,29%, 1.40 GHz:0,31%, 1.30 GHz:0,37%, 1.20 GHz:0,28%, 1.10 GHz:0,21%, 1000 MHz:0,23%, 900 MHz:0,28%, 800 MHz:90,80%  (135030)
======================================================

Hardware limit of 2200 Mhz is detected, but the gevernor only allows up to 1800. Why? and how to fix that?

It seems that there is no acpi_cpu module loaded. So the kernel has some problem detecting the cpu?

lsmod
=============================================
Module                  Size  Used by
msr                    12908  0 
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   21708  0 
fat                    61374  1 vfat
usb_storage            53538  0 
uas                    17996  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28167  4 
snd_hda_codec_idt      71137  1 
arc4                   12529  2 
nvidia              10709116  47 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlagn                333717  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
dell_wmi               12681  0 
sparse_keymap          13898  1 dell_wmi
iwlcore               167503  1 iwlagn
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72195  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
psmouse                73535  0 
mac80211              294370  2 iwlagn,iwlcore
videodev               82052  1 uvcvideo
ppdev                  17113  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17078  1 videodev
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178528  3 iwlagn,iwlcore,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
coretemp               13490  0 
parport_pc             36959  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
sdhci_pci              13989  0 
xhci_hcd               77643  0 
e1000e                159096  0 
firewire_ohci          40370  0 
ahci                   25951  3 
firewire_core          62646  1 firewire_ohci
libahci                26642  1 ahci
sdhci                  27387  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
====================================

I installed turbostat, as mentioned below:
[http://ubuntuforums.org/archive/index.php/t-1635241.html](http://ubuntuforums.org/archive/index.php/t-1635241.html)

The cpu frequency stops at 1800Mhz, even at 100% load. So Intel Turbo Boost is also not working.

cat /proc/cpuinfo
=========================
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4389.33
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
==============================================

Can anyone help?

/edit:

I'm using Ubuntu 11.04-64bit and Dell Bios Rev A04

Thx

---

### Post by serxyz on 2011-08-24
Fixed.

=====================================================
$ lspci -nn | grep -i ethernet

00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)
=====================================================
1) Go to: <http://downloadcenter.intel.com/>
2) Search for: "82579&#8243;
3) Select: "Linux" in the "Operating System" section
4) Download: e1000e-1.5.1.tar.gz
=====================================================
5) Make Install:

$ sudo -s
$ cd ~/Downloads/
$ tar xfz e1000e-1.5.1.tar.gz
$ cd e1000e-1.5.1/src
$ make install
=====================================================
6) With 2.6 based kernels also make sure that older e1000e drivers are removed from the kernel, before loading the new module:

$ sudo rmmod e1000e
$ sudo modprobe e1000e
=====================================================
7) Load the module using either the insmod or modprobe command:

$ modprobe e1000e
$ insmod /lib/modules/<KERNELVERSION>/kernel/drivers/net/e1000e/e1000e.ko
=====================================================

Hope that helps! (it worked for me)

[serXYZ]

See also:

<http://giantdorks.org/alain/fix-for-non-working-wired-ethernet-on-dell-latitude-e6520-with-intel-82579-based-adapter-running-ubuntu-10-04-lts-lucid/>

---

### Post by metos on 2011-08-24
quick tip for those who have an ATI card
the ati catalist manager asks for reboot each time you modify dual monitor configuration.


I made a simple bash script with the xrandr command who switch the monitors configuration when I dock in or undock the computer. (no reboot and no sudo rights needed)


otherwise, I still have my slow system problem when I resume from suspend mode

---

### Post by loic13410 on 2011-09-14
Hi there,
@metos:  could you please post your bash script for docking/undocking monitor switch  ?
Thanks,
Regards,
Loic

---

### Post by metos on 2011-09-14
use xrandr to know the name of the connected display then adapt the following scripts

to extend display : 
```

#!/bin/bash
xrandr --output LVDS --mode 1920x1080 --output DFP3 --mode 1600x1200 --right-of LVDS

```

to back to single screen
```

#!/bin/bash
xrandr --output LVDS --mode 1920x1080 --output DFP3 --off --output DFP2 --off

```
maybe you'll have to modify or add line in xorg.conf to define or extend the maximum display size allowed


more details here : [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

I made various scripts for my different cases of use (on other dell monitor, on a TV via HDMI, ...).
this works very well and that's instantly switched.

I tryed to use 2 external monitors together (via the 2 DVI ports on my dock) but this seems not supported by video card.

---

### Post by loic13410 on 2011-09-15
Thanks metos for these informations. I'll try all that as soon as my M4600 is delivered (next week).

Loic

---

### Post by Salline on 2011-09-28
For configuring external displays, I'm successfully using the disper and autodisper tools.
It needs a bit of fiddling around, but you can comfortably bind it to a key combination and setup your displays the way you want them.

Basically, you connect your displays and then use disper to setup your screen.
Then you can save this configuration under a unique identifier using autodisper.
It will also remember which displays (i.e. name of the display) are connected where and use that information to automatically switch to the correct mode later on.

This way, I can simply switch to dual external monitors when I get to work, and switch back to the built-in display when I'm on the road.

I also wrote some scripts that I are activated by udev when I dock/undock and these will in turn call autodisper, so I can comfortably just dock my NB and it will switch to the external monitors. Docking/undocking can be recognized by the presence of a certain USB-device.

Some links to point you guys in the right direction:
[https://github.com/wertarbyte/auto-disper](https://github.com/wertarbyte/auto-disper)
[http://www.favias.org/post/automatic-screen-configuration-auto-disper](http://www.favias.org/post/automatic-screen-configuration-auto-disper)
[http://blog.alex.bepple.de/276/](http://blog.alex.bepple.de/276/)

Also, here is the wrapper script that is called upon docking/undocking and after the gnome-login:
Filename: /sbin/display-setup-wrapper
```
#!/bin/bash
/bin/sleep 1
USER=`whoami`
if [ "$USER" == "<MY_USERNAME>" ]
then
    export DISPLAY=:0
    /home/<MY_USERNAME>/.Xdbus
    /usr/local/bin/autodisper -c --force
    /home/<MY_USERNAME>/.runsynergy

else
    /bin/su - MY_USERNAME -c "export DISPLAY=:0; . /home/<MY_USERNAME>/.Xdbus; /usr/local/bin/autodisper -c --force; /home/<MY_USERNAME>/.runsynergy"
fi

```
(Note: I'm using synergy to control several machines with a single mouse/keyboard. Whenever your desktop changes, you need to restart synergy or you'll get strange results. That's what the .runsynergy stuff in the script is for. If you don't use synergy simply delete that part...)

UDEV-rules for docking/undocking
(put this in /etc/udev/rules.d/80-dell-docking.rules)
```

KERNEL=="1-1.1" RUN+="/sbin/display-setup-wrapper"

```Also, a nifty feature of autodisper is that you can run a script (~/.autorandr/<CONFIG_NAME>/postswitch) after a switch has occured.
I just send a notification to the desktop (running gnome) showing me which config was activated...

```

#!/bin/bash
notify-send -t 10 "Auto Display Configuration" "Config \"Work\" is activated"

```Sorry I don't have more details at the moment, it's been a while since I did that and I don't remember the specifics from the top of my head (and I'm too busy atm to investigate further).

Hope it helps some of you guys.

Kind regards,

Salline

P.S.: Anyone solved the hibernate-issues yet? Standby works on my machine, hibernate doesn't... :(

---

### Post by frantek on 2011-10-09
Hi M660 users,

I currently have a Vostro 3750 and I'm not too stisfied due to the powermanagement and mainly due to the damm Alps touchpad which is not recognized as touchpad and does not work very well. Tapping is not disabled while typing which is pretty annoying.

So my question is: How are your experiences with the touchpad in the M660 ?

TIA

---

### Post by loic13410 on 2011-10-11
Hello,

I have M4600 with ATI FireGL 1Go DDR5 video card and the docking station. Is there a way to use the built in monitor PLUS two external monitors using the dvi output of the docking station ?
I have tryed many ways without success, I can have bultin + 1 externa, 2 externals but not the 3 monitors.
Can anyone help please ?

Thanks,

Regards,

Loic

---

### Post by francoisfaure on 2011-10-15
Hello,
I do not manage to correctly install the nvidia driver on my M4600 with an NVidia Quadro, and Ubuntu 11.10 64bits. 
I used the «Additional drivers» (i.e. jockey-gtk) application to install the «NVIDIA accelerated graphics driver (version current) [Recommended]». It took ten minutes to download and install the driver, then told I had to reboot.
Once rebooted, the driver installer says that the driver is activated and in use, but  «nvidia-settings» says that it is not installed, and that I should run «nvidia-xconfig» as root.  I run it,  shut down, but I can not reboot any more: the cursor keeps blinking. The failsafe reboot in text mode does not allow me to switch back to the previous xorg.conf file because it mounts the file system in read-only mode (!) so I have to re-install from scratch.

I have also tried the following variants with the same result:
- 11.10 32 bits, 11.04 64 bits
- NVIDIA accelerated graphics driver post-release updates) (version current-updates)

Any ideas ?
Thanks in advance,

---

### Post by francoisfaure on 2011-10-16
Hi,
thanks to _[this post]("http://www.michaelbommarito.com/blog/2011/07/11/natty-narwhal-on-the-precision-m4600/")_, I realized that I had to disable Optimus in the BIOS. Now the driver seems to work fine. 
However, there are other issues, such as the nautilus file navigator crashing when I open some folders, such as Desktop.

---

### Post by francoisfaure on 2011-10-22
Hi,
I successfully installed ubuntu 11.10 Oneiric Ocelot 64 bits (i.e. amd64) on my Dell Precision M4600 with Nvidia Quadro 2000M  thanks to differents posts. So here are my two cents: a summary of what worked for me.

1. Disable Optimus video mode in the bios. ([http://www.michaelbommarito.com/blog/2011/07/11/natty-narwhal-on-the-precision-m4600/](http://www.michaelbommarito.com/blog/2011/07/11/natty-narwhal-on-the-precision-m4600/)) This solves two problems:
- the nvidia driver can now work (activate it using «Additional Drivers» in the System Settings)
- shut down works. No need to edit /etc/default/grub as suggested in some posts

2. Do not install nautilus-open-terminal, to avoid crashes when opening some directories ([http://askubuntu.com/questions/65443/nautilus-on-ubuntu-11-10-keeps-crashing](http://askubuntu.com/questions/65443/nautilus-on-ubuntu-11-10-keeps-crashing)). I hope they will fix this soon, however, because it is a useful option  

Remaining issues:
- the webcam image is terrible, while on Windows it is acceptable
- hibernation does not work, as noticed in other posts

The following are customizations I find useful:
- disable login sound: ([http://maketecheasier.com/disable-login-sound-in-ubuntu-oneiric-quick-tips/2011/09/15](http://maketecheasier.com/disable-login-sound-in-ubuntu-oneiric-quick-tips/2011/09/15))

- configure the workspace other than 2x2: [http://pof.eslack.org/2011/10/03/change-workspace-configuration-on-ubuntu-11-10/](http://pof.eslack.org/2011/10/03/change-workspace-configuration-on-ubuntu-11-10/)

---

### Post by zemlinc on 2011-10-22
High power consumption

Hi, 

I recently installed Ubuntu 11.10 on a Dell Precision m4600 and have way too high power consumption: According to PowerTOP, Ubuntu uses between 30-40W, which makes my 62.2 Wh battery last less than 2 hrs.  This is AFTER I installed and activated pm-utils.  I also tried Ubuntu 11.04, with very similar results.

I would greatly appreciate helpful comments!

Christian

---

### Post by davydden on 2011-11-04
Hi everyone,

I wonder if anyone is using Raid0 (2xHDD) + mini SSD? I'm thinking to buy that configuration, but would prefer to be sure that it works ok under Ubuntu (use 11 on my desctop now).

Cheers,
Denis.

---

### Post by Tamale on 2011-11-19
I just got 11.10 64bit running on my new m6600 (with the ATI firepro m8900) as well.. good news is I haven't even bothered with the proprietary ATI driver.. the default open-source ones seem to be doing just fine with both unity and gnome3..

my main beef isn't with the laptop or any hardware issues, it's just with unity and gnome3 in general.. I really want to use compiz for things like per-window transparency, but I don't want to have to use gnome-fallback because it blows donkey cahones..

---

### Post by neil499 on 2011-11-22
> **davydden said:**
> Hi everyone,

I wonder if anyone is using Raid0 (2xHDD) + mini SSD? I'm thinking to buy that configuration, but would prefer to be sure that it works ok under Ubuntu (use 11 on my desctop now).

Cheers,
Denis.

I'm running that same configuration (2xHDD + miniSSD) on my work laptop (OpenSuse 11.4)...

Apparently, the hardware RAID (Intel Matrix Storage) insists on booting off the RAID0 partion and I can' seem to force it to use the non-raided drive. (I wanted RAID0 for /home and did not care about raiding everything else), so I was forced to use software raid. (Sort of defeats the purpose of getting a hardware RAID.)

Good luck.

- Neil

---

### Post by k0d3g3ar on 2012-01-03
Hi all, 

I'm considering purchasing a M6600 to coincide with Ubuntu 12.04 LTS release coming up.  I've been using a M6300 for years with Ubuntu (NVidia graphics) and its been brilliant.  I've a large multi-monitor desktop setup, and I was hoping to just swap out the laptop for the new one, upgrade Ubuntu and get some memory capacity & speed improvements.

The thing I keep running into is graphics resolution.  I have 2 x 1920x1200 monitors (native LCD) that were matched to the previous standard size of the M6300.  But the Dell specs show the M6600 to support max resolution of 1920x1080 which won't match my monitors.  I don't want to have to shell out a ton of cash for 2 big new monitors to go with a new laptop, and a buddy of mine said that the max resolution may simply be a restriction on Windows drivers and not be an issue with the Nvidia drivers for Linux.

Does anyone know if this is true?  Can the Nvidia drivers for this laptop support more resolution than what Dell advertises as the maximum?

Thanks in advance for any assistance.

K

---

### Post by gberardi on 2012-02-04
> **k0d3g3ar said:**
> Hi all, 
The thing I keep running into is graphics resolution.  I have 2 x 1920x1200 monitors (native LCD) that were matched to the previous standard size of the M6300.  But the Dell specs show the M6600 to support max resolution of 1920x1080 which won't match my monitors.  I don't want to have to shell out a ton of cash for 2 big new monitors to go with a new laptop, and a buddy of mine said that the max resolution may simply be a restriction on Windows drivers and not be an issue with the Nvidia drivers for Linux.

Does anyone know if this is true?  Can the Nvidia drivers for this laptop support more resolution than what Dell advertises as the maximum?


I was curious as well. I just replaced my Precision M90 with an M6600, and while I'm disappointed that the resolution of 1920x1200 dropped to 1920x1080 on the laptop's screen, I was wondering if there were any technical limitations that prevented it from taking advantage of larger external monitors. 

Unfortunately, I still have an old CRT, so the max resolution I was able to get out of it was much less than 1920x1080, and I don't have access to a larger monitor. I suppose I could try hooking it up to my 1080p television, but that still doesn't answer the question of how big a monitor could the m6600 support.

It seems other Dell customers wondered the same. 

This one suggests that you won't get above 1280x800 on certain monitors without an adapter.: [http://en.community.dell.com/support-forums/laptop/f/3519/p/19406623/19949525.aspx#19949525](http://en.community.dell.com/support-forums/laptop/f/3519/p/19406623/19949525.aspx#19949525) 

This one suggests that it's possible to get 1920x1200 without an adapater but again, it seems to depend on the monitor: [http://en.community.dell.com]("http://en.community.dell.com/support-forums/laptop/f/3519/p/19406004/19946970.aspx#19946970")[URL="http://en.community.dell.com/support-forums/laptop/f/3519/p/19406004/19946970.aspx#19946970"]/support-forums/laptop/f/3519/p/19406004/19946970.aspx#19946970 
[/URL]

---

### Post by vladeta on 2012-06-23
Hello,

I have a problem in ubuntu 12.04 with my Dell M4600:  nVidia quadro 2000M, i7-2860 16GB ram, 128GB SSD Dell/Samsung, 750GB HDD and  IPS RGB laptop display.  When it is connected via DP++ to external Dell U2311H monitor it hangs on boot or at wake from suspend. If I detached DP cable it boots normally.
I have tried all combinations that I have found, as adding to grub "no splash" "boot=pci" "acpi=off" etc. I have also changed in nvidia X settings that external monitor is the primary one and also tried to delete monitor.xml file. There is no change it hangs each time.
It starts to load deamons then both screens are blank and then completely hangs with beep sound. 

What I discovered is if I detach cable wait 2 sec after grub starts booting and then physically connect DP cable while the ubuntu still booting everything works normally and I have picture on my external screen while the laptop screen is off, just as I wanted.  
Do  you  maybe know how to solve this issue. Thank You.

---

### Post by Askel on 2012-10-13
Hello

I'm planning on buying a Dell m4600 in the near future. I'd like to have some tips on how well it performs with ubuntu. Here I read about problems people have, but are there owners who use it without any issues at all? If you own one, please write here about how it works with linux. What works and what doesn't and how you solved problems.

//Askel

---

### Post by pvandoren on 2012-10-15
You should be good to go with the M4600.

Problem area would be graphics.  We have a M6600 running ubuntu 12.04.  With the latest bios update all the remaining issues went away.  (Main issue was it would hang on shutdown/restart)

It has the AMD graphics card, and is using the standard ubuntu drivers with no problem. (in a triple head solution)

NVidia you'll need to use the proprietary drivers. and will only be able to have 2 displays. (twin-view)

I also have a M6700 that I'm using.  Right now It's running but the graphic support is still lacking, and a bit buggy.  Again we have the AMD graphics option, but I have to use a hacked version of the proprietary drivers.  This only supports a dual head system, instead of the triple head, and currently has some artifacts that occurs.

Areas I suggest upgrades on (not necessarily though dell), is RAM and a SSD hard drive.  They make a big difference in performance.

Hope this helps.

Pete

---

### Post by Askel on 2012-12-31
Thought I'd share my experience after I bought the Dell Precision M4600 in October.

The specs are:
CPU: i7 quadcore 2,4 GHz
Ram: 16 GB 1333MHz
GPU: Nvidia Quadro K2000M 2GB
HDD: 320 GB
Screen: FullHD

I did mess up my first install by trying Bumblebee. It only messed up the OS and I couldn't get it back to workingcondition. I had no HDMI or Displayport with it, so I reinstalled the system.

Now I run Ubuntu 12.04 LTS with proprietary Nvidia-drivers and everything (almost) works great. Displayport, HDMI has video but no sound, other than that I havn't encountered any problems. I have a port-replicator and it works great with that to. All mediabuttons and Fn-keys work out of the box. Both USB2 and USB3 works. I havn't tried the eSata and the Firewire-ports yet. Suspend & resume works without any issue.

I love the computer, and I still havn't regreted the switch from Apple, even though some things takes a little more readning and learning to get done than with the mac. But the computer is big. Enormously big for a 15". My Swissgear-backpack is made for a 15,6" but the computer hardly fits there.

BTW if anyone has a tip for a good sleeve for the M4600 I'd be glad to know it.

---

### Post by am17torres on 2013-04-17
I know this thread has gotten a bit stale, but I am trying to figure out if I can all three of my screens working. I have the dell precision m4600 i7 plus an nvidia gpu (not sure which one) in a docking station. I have already disabled the optimius option from the bios. I also followed the steps for install jockey, going to software sources -> additional drivers -> using nvidia binary xorg driver, kernel module and VDPAU library from nvidia-current (Proprietary, tested) but made my display much worse. I've tried all the nvidia options listed. Using the X.Org X server gave me the best result which is two external monitors at the correct 1080 resolution. However my laptop screen is blank.

When I go into the displays option and turn on the laptop screen i get the following error:
The selected configuration for displays could not be applied
could not assign CRTCs to outputs:
Trying modes for CRTC 96
CRTC 96: trying mode 640x480@59Hz with output at 640x480@0Hz (pass 0)
CRTC 96: trying mode 640x480@59Hz with output at 640x480@0Hz (pass 1)
    could not assign CRTCs to outputs:
Trying modes for CRTC 96
CRTC 96: trying mode 1920x1080@60Hz with output at 1920x1080@60Hz (pass 0)
    output DP-1 does not have the same parameters as another cloned output:
existing mode = 104, new mode = 105
existing coordinates = (3840, 18), new coordinates = (1920, 18)
existing rotation = normal, new rotation = normal
CRTC 96: trying mode 1280x1024@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1280x1024@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1152x864@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1024x768@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 800x600@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 640x480@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 720x400@70Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1920x1080@60Hz with output at 1920x1080@60Hz (pass 1)
    output DP-1 does not have the same parameters as another cloned output:
existing mode = 104, new mode = 105
existing coordinates = (3840, 18), new coordinates = (1920, 18)
existing rotation = normal, new rotation = normal
CRTC 96: trying mode 1280x1024@75Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 1280x1024@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 1152x864@75Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 1024x768@75Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 800x600@75Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 640x480@75Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 1)
CRTC 96: trying mode 720x400@70Hz with output at 1920x1080@60Hz (pass 1)
Trying modes for CRTC 95
CRTC 95: trying mode 1920x1080@60Hz with output at 1920x1080@60Hz (pass 0)
    could not assign CRTCs to outputs:
Trying modes for CRTC 96
CRTC 96: trying mode 1920x1080@60Hz with output at 1920x1080@60Hz (pass 0)
    output DP-3 does not have the same parameters as another cloned output:
existing mode = 104, new mode = 105
existing coordinates = (3840, 18), new coordinates = (0, 0)
existing rotation = normal, new rotation = normal
CRTC 96: trying mode 1280x1024@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1280x1024@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1152x864@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1024x768@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1024x768@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 800x600@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 800x600@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 640x480@75Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 640x480@60Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 720x400@70Hz with output at 1920x1080@60Hz (pass 0)
CRTC 96: trying mode 1920x1080@60Hz with output at 1920x1080@60Hz (pass 1)
    output DP-3 does not have the same parameters as another cloned output:
existing mode = 104, new mode = 105


I also know when I'm using windows if I do a dxdiag, it shows that my laptop screen is using the integrated intel chip while the two external displays are using nvidia.

Any tips or ideas would be very helpful.

---

### Post by ivotron on 2013-05-03
> **Askel said:**
> Thought I'd share my experience after I bought the Dell Precision M4600 in October.
Now I run Ubuntu 12.04 LTS with proprietary Nvidia-drivers and everything (almost) works great. Displayport, HDMI has video but no sound, other than that I havn't encountered any problems. I have a port-replicator and it works great with that to.

I hope @askel can still read this. When you mention that HDMI/DP work OK, does that statement consider having an external monitor running the same session? I'd really appreciate if you could share more about this. I've been unable to have HDMI/DP work.

---

### Post by Askel on 2013-05-10
> **ivotron said:**
> I hope @askel can still read this. When you mention that HDMI/DP work OK, does that statement consider having an external monitor running the same session? I'd really appreciate if you could share more about this. I've been unable to have HDMI/DP work.

Yes, I have the external monitor connected via DP connected to the portreplicator. A bit of an issue though is that I have to disconnect the DP-cable from boot until Ubuntu have started to load. If I have it connected when GRUB loads Ubuntu starts loading and then both screens just go black. When I disconnect it during starup and then plugs it in it works just fine. I havn't tried with more than one screen at a time though.

The proprietary driver I use is Nvidia version current-updates 304.88-0ubuntu0.0.1. None of the others showing under "additional drivers" works.

Hope any of this helps.

//Askel

---

### Post by Askel on 2013-05-27
> **ivotron said:**
> I hope @askel can still read this. When you mention that HDMI/DP work OK, does that statement consider having an external monitor running the same session? I'd really appreciate if you could share more about this. I've been unable to have HDMI/DP work.

Did you get it to work?

---

### Post by Marty_Leisner on 2014-02-27
I've had a m6600 for a bit over a year.  I'm using the Radeon version 

I had ubuntu 12.10 on it -- it was a pain to install.

The system regularly overheated -- not sure how I fixed it.  (but the temperature/shutdown has always been an issue -- I run
it as "conversative" or "powersave" -- ondemand seems to take too much power (and make too much heat).

I trashed my system, so I wanted to reinstall.   Not easy!!

The trying to install various flavors of ubuntu, mint and debian consistently gets on overtemp and a shutdown.
Running psensors and watching whats going on, the graphics seems to hit up and then shut down.

The bios tests don't indicate a problem.

I'm going to make a usb key with the flgrx drivers present and switch them in and see if it helps.

But its SOOOO painful (I've installed linux on dozens of machines over the years and this is the most painful [often times, something doesn't work, you
fix later -- but "shutdown on overtemp"])

BTW, I did an upgrade on the bios (to A15 -- just for grunts -- doesn't seem to help)

And I'm running one core/no hyperthreading (to see if that helped)

Are there any useful "fan" utilities to run seperately?

marty

---

