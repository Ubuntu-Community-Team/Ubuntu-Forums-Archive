---
title: "No Audio on Headphone Jack on Sylvania G"
date: 2008-08-12
forum: Hardware
---

### Post by aastaneh on 2008-08-12
I recently purchased a Sylvania G Netbook (which is pretty much a rebranded cloudbook)

Installed Xubuntu on it, works nicely, except one detail.

Sound works through the laptop speakers, however when I plug in my headphones I don't hear a thing. I've googled this problem however I haven't seen anything with this type of hardware before.

Here's some hardware information that may be useful:

root@ronin:~# lspci | grep Audio
02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

root@ronin:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

root@ronin:~# lsmod
Module                  Size  Used by
via                    43648  2 
drm                    82452  3 via
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ipv6                  267780  8 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0 
joydev                 13120  0 
af_packet              23812  2 
snd_hda_intel         344728  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_seq_dummy           4868  0 
evdev                  13056  6 
snd_seq_oss            35584  0 
serio_raw               7940  0 
snd_seq_midi            9376  0 
rtl8187                36096  0 
mac80211              165652  1 rtl8187
snd_rawmidi            25760  1 snd_seq_midi
uvcvideo               58116  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
psmouse                40336  0 
cfg80211               15112  1 mac80211
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
eeprom_93cx6            3200  1 rtl8187
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
video                  19856  0 
output                  4736  1 video
pcspkr                  4224  0 
battery                14212  0 
ac                      6916  0 
button                  9232  0 
i2c_viapro              9876  0 
i2c_core               24832  1 i2c_viapro
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
via_agp                11136  1 
agpgart                34760  2 drm,via_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
usb_storage            73664  0 
libusual               19108  1 usb_storage
sd_mod                 30720  3 
8139cp                 24704  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
pata_acpi               8320  0 
pata_via               13316  2 
ata_generic             8324  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
libata                159344  3 pata_acpi,pata_via,ata_generic
usbcore               146028  7 rtl8187,uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
scsi_mod              151436  4 sg,usb_storage,sd_mod,libata
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1

Any help would be appreciated.

---

### Post by aastaneh on 2008-08-13
Solution Procedure-

1. Download the alsa-drivers source:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)

2. Follow the patching and installation instructions from here: 
[http://ubuntuforums.org/showthread.php?t=556217](http://ubuntuforums.org/showthread.php?t=556217)

3. Reboot, and use alsamixer to unmute the "Headphones" control and set its volume.

4. Enjoy the now-working headphone jack.

I would hope that the alsa-project developers commit some changes upstream, or I will have to maintain a driver install from source (which is silly for a package-based distribution lauded for it's ease of use).

---

### Post by guest128 on 2008-11-18
Sorry to revive an old thread, but I wanted to know if you're talking about the regular Sylvania G, and not the Sylvania G Meso. I just ordered the former with the purpose of using it as a brain for a robot. I've already done the robot thing with Ubuntu, so I was thinking about wiping the HD and throwing Ubuntu on there, but I wanted to make sure that wireless and sound are functional. But any info about the Sylvania G and Ubuntu seems to be talking about the Meso.

I suppose anyone who has installed Ubuntu (or some flavor of it) on the non-Meso Sylvania G would be able to answer my question.

Also, if I wipe gOS off of the HD, will it be hard to setup again if I have to? I've heard something to the effect that the restore disk for the netbook has gOS, but Windows drivers instead of linux drivers. this is a concern.

Thanks for your time
-guest128

---

### Post by caitlynmaire on 2008-12-25
I have the original g.  If I were you I'd plan on doing some significant work on the g before being able to use it for much of anything.  The hardware is brilliant.  The gOS configuration is horrible and leaves you with a crippled machine.

Here are the issues and fixes:

1.  It ships with gOS 2.92, a beta with issues.  It can be upgraded to gOS 3.0 using an iso on the Sylvania site.  You need an external (usb) CD drive to install it. 

2.  gOS 2.92 comes with a Realtek wireless driver that is the absolute pits.  It has very limited range and drops connections.  gOS 3.0 does fix this or else you can blacklist the driver and install one that actually works.  The gOS 3.0 solution is, in fact, ndiswrapper and a Windows driver.  There is another Linux native driver that works but I need to do some more searching to find it again :(

3.  The processor is a 1.2GHz Via C7-M ULV which supports frequency scaling.  In gOS 2.92 or 3.0 you have an old 2.6.24.x kernel that doesn't have this support.  If you don't install a kernel patch the system comes up underclocked to 600MHz (yes, half speed) and is slow and can't be changed.  Once patched powernowd does work well. 

4.  gOS 2.92 or 3.0 ships with an older proprietary Via Chrome video driver with broken 3D acceleration.  Upgrading to the newest open source Via Chrome driver fixes the problem.  3D works well with the new driver.

5.  gOS makes their system idiot proof by hiding the terminal and any tools needed to install or upgrade software.  You need to edit the .desktop files in /usr/share/applications to reenable Synaptic and gnome-terminal or else create launchers for them.  Doing all the Hardy updates doesn't break anything AFAIK.

6.  Some apps are poorly configured and open in windows that are too large for the screen resolution. 

If you fix all those things then you do have a brilliant little machine.  I love mine.  I just don't recommend it for anyone who isn't computer savvy.

HTH

---

### Post by willreed on 2008-12-28
I want to thank all of you that started and posted to this thread. I've been searching the forum waiting for someone that 

has one of these to make a list such as the above. 

I purchased my little g netbook in July and I've been relatively content with it. I've burned gOS 3 to a cd. However I've 

been using it without installing it on my little g book because of some of the problems mentioned above.

What I need to ask is this.

Is it possible to apply all these patches/fixes then recompile the kernal and burn a new ISO? The reason I ask is that I'm 

not up on how an ISO file structure is compressed and even if I had a chance at replacing the kernal that's offered with 

the ISO download with one with the list of fixes you've mentioned above. 

I've installed Linux on dozens of machines since 1998 but in the last few years I've been spoiled by using (nearly hands off) Linux installs. 

I would be thankful for any help on this.

I want to add that this is the g netbook pre Meso

---

### Post by intrepid7 on 2009-04-27
I updated my gnetbook to gOS 3.0 , everything is pretty smooth but I have been trying to fix the freq scaling issue.  I follow the directions here:[http://www.a110wiki.de/wiki/CPU](http://www.a110wiki.de/wiki/CPU)

$ wget [http://www.a110wiki.de/wiki/images/6/65/Cpufreq-2.6.25_backport.tar.bz2](http://www.a110wiki.de/wiki/images/6/65/Cpufreq-2.6.25_backport.tar.bz2)
$ tar xfvj Cpufreq-2.6.25_backport.tar.bz2
$ cd cpufreq
$ make

However, when I try to make the module I get a slew of returned errors, ie:
mpdion@gnetbook:~/cpufreq$ make
make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24.3'
/usr/src/linux-headers-2.6.24.3/arch/x86/Makefile:15: /usr/src/linux-headers-2.6.24.3/arch/x86/Makefile_32: No such file or directory
  CC [M]  /home/mpdion/cpufreq/e_powersaver.o
In file included from include/linux/kernel.h:11,
                 from /home/mpdion/cpufreq/e_powersaver.c:9:
include/linux/linkage.h:4:25: error: asm/linkage.h: No such file or directory
In file included from include/linux/posix_types.h:47,
                 from include/linux/types.h:11,
                 from include/linux/kernel.h:13,
.
.
.
and so on.  I have installed the build-essentials package. Has anyone had this problem, any fixes? Thanks

---

### Post by sixteenkats on 2009-08-12
[deleted by author]

---

### Post by zerker2000 on 2009-11-27
I have the same problem, though I installed #! instead of pOS 3 since I couldn't find an external cd drive. I am currently looking for a solution.

---

