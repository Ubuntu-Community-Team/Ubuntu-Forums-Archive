---
title: "VisionPlus (twinhan) PCI vid card"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by ubuntme on 2005-08-12
Hi,

I'm new to Ubuntu (and linux for that matter) and trying to get a Visionplus Twinhan card to work under ubuntu.
here is my dmesg:

matt@ubuntu:~$ dmesg |grep bttv
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 17, latency: 32, mmio: 0xe2003000
bttv0: detected: Twinhan VisionPlus DVB-T [card=113], PCI subsystem ID is 1822:0001
bttv0: using: Twinhan DST + clones [card=113,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
bttv0: using tuner=4
bttv0: add subdevice "dvb0"

and lspci:

0000:00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capt ure (rev 11)
0000:00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (r ev 11)

and finally lsmod:
matt@ubuntu:~$ lsmod
Module                  Size  Used by
vfat                   12928  1
fat                    37792  1 vfat
nls_cp437               5888  2
isofs                  33720  1
udf                    77060  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
nvidia               3923388  12
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
sd_mod                 16784  2
ipv6                  229504  11
via_rhine              19972  0
mii                     4736  1 via_rhine
usb_storage            64064  1
snd_via82xx            25248  2
snd_ac97_codec         64608  1 snd_via82xx
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
i2c_viapro              7436  0
usbhid                 29376  0
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
sata_via                8196  0
libata                 44548  1 sata_via
scsi_mod              119936  3 sd_mod,usb_storage,libata
rt2500                207076  1
snd_bt87x              12612  0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_via82xx,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  10 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  3 snd_via82xx,snd_bt87x,snd_pcm
tuner                  20388  0
bttv                  142928  0
video_buf              20484  1 bttv
firmware_class          9728  1 bttv
i2c_algo_bit            9224  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4744  1 bttv
i2c_core               21264  4 i2c_viapro,tuner,bttv,i2c_algo_bit
videodev                9728  1 bttv
pci_hotplug            30512  0
via_agp                 9216  1
agpgart                31784  2 nvidia,via_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_utf8                2176  2
ntfs                   97136  1
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  1
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               18176  5
ide_core              118988  5 usb_storage,ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  868
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

sorry about the length of that, not sure what is important and what is not.

But this is what happens when I run xawtv -hwscan

This is xawtv-3.94, running on Linux/i686 (2.6.10-5-386)
looking for available devices
port 105-105
    type : Xvideo, image scaler
    name : NV17 Video Overlay

port 106-106
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 107-138
    type : Xvideo, image scaler
    name : NV05 Video Blitter

port 139-139                            [ -xvport 139 ]
    type : Xvideo, video overlay
    name : NVIDIA Video Interface Port

so xawtv can't find my card.

I made a node called /dev/video0 an ran a script from the web that was supposed to set it up, but I don't think it worked and don't know how to check it etc...

Any ideas?  What do I need to do???

Thanks!

---

### Post by art2003 on 2005-08-14
I had the same problem and fixed it.
My card is actually a Satellite card although it was detected as Terrestrial.

1)
sudo gedit /etc/hotplug/blacklist
Add these lines:
snd_bt87x
bttv
dvb_bt8xx
bt878

2)
sudo gedit /etc/modules
add these lines:
bttv
dvb-bt8xx
dst
snd_bt87x

reboot, start a program like kaffeine and it should detect your Twinhan PCI satellite card.

---

### Post by ubuntme on 2005-08-16
Thanks,

My card is a terestrial card btw.

I tried your suggestions, xawtv -hwscan still finds no device.  Do I need to create a device under /dev?  my card seems to be in /dvb/adaptor

I installed Kaffeine as suggested, and it seems to detect the card:

QSettings::sync: filename is null/empty
kaffeine: Found DVB device.
Card 0 : opened ( DST DVB-T )
Card 1 :openFe :: No such file or directory
Card 2 :openFe :: No such file or directory
Card 3 :openFe :: No such file or directory
kaffeine: Window manager: not KWin - using save fullscreen mode
kaffeine: SystemTray: Create System Tray
kaffeine: Kaffeine:: Try to load service: kaffeine_part
Asked to stop
Live stopped
kaffeine: This is a KMediaPart...
kaffeine: KaffeinePart: Creating new KaffeinePart...
kaffeine: PlayList: add 1 items to playlist
kaffeine: Kaffeine: Set screensaver timeout to: 2 min

But I try to scan for channels, and it can't find any....

Any ideas?

---

### Post by ubuntme on 2005-08-16
Oh, here's what happens when I try to scan channels:

Using DVB card "DST DVB-T"
tuning DVB-T to 226500000 Hz
inv:2 bw:1 fecH:2 fecL:0 mod:3 tm:1 gi:2 hier:0
polling....
Getting frontend event
polling....
polling....
polling....
polling....
polling....
polling....
polling....
polling....
polling....
dvbsi : Cant tune DVB
Transponders : 1
dvbsi : The end :)

---

### Post by cloudr on 2005-08-17
Since I never had a DVB-T card any advice I can offer you is of limited use.

Have you tried tzap to scan?

does dmesg show it has configured a DVB-T card?
(mine does say something like DVB-S CARD detected)

also try lsmod | grep dvb to find out what modules get loaded.

---

### Post by ubuntme on 2005-08-17
This is the bit from dmesg:

bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 17, latency: 32, mmio: 0xe2003000
bttv0: detected: Twinhan VisionPlus DVB-T [card=113], PCI subsystem ID is 1822:0001
bttv0: using: Twinhan DST + clones [card=113,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00f100fe [init]
bttv0: using tuner=4
bttv0: add subdevice "dvb0"
bt878: AUDIO driver version 0.0.0 loaded
bt878: Bt878 AUDIO function found (0).
ACPI: PCI interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 17
bt878(0): Bt878 (rev 17) at 00:09.1, irq: 17, latency: 32, memory: 0xe2002000
DVB: registering new adapter (bttv0).
dst_check_ci: recognize DTTDIG
DST type : terrestrial
DST type flags :
DVB: registering frontend 0 (DST DVB-T)...


And from lsmod:

dvb_bt8xx              10116  0
dvb_core               74408  1 dvb_bt8xx
nxt6000                 6532  1 dvb_bt8xx
mt352                   5380  1 dvb_bt8xx
dst                    12040  1 dvb_bt8xx
bt878                  10552  2 dvb_bt8xx,dst
sp887x                  7172  1 dvb_bt8xx
bttv                  142928  2 dvb_bt8xx,bt878
firmware_class          9728  3 dvb_bt8xx,sp887x,bttv
i2c_core               21264  9 i2c_viapro,dvb_bt8xx,nxt6000,mt352,dst,sp887x,tuner,bttv,i2c_algo_bit

will have a play with tzap once i figure out what it is.
One question, how can I get a channels.conf file?

Thanks

---

### Post by art2003 on 2005-08-18
The output from dmesg looks right, I think your drivers are fine.
To get a channels.conf you can either scan for them yourself (which doesn't work for me except using kaffeine which generates a different format incompatible with vdr)

or you can use google to find a pre-generates list.

If you find a tool to convert channels from kaffeine to vdr let me know!

---

### Post by ubuntme on 2005-08-21
hmmm, 

I'm a little confused about the whole thing, If the drivers were working I would have thought that xawtv -hwscan would get something...

Also, I get nothing when I scan channels using Kaffiene... (see verbose output above)

I had no luck getting a channels.conf from google.  Is there a way I can get the channels from windows using the twinhan software?

Ta

---

### Post by art2003 on 2005-08-22
xawtv -hwscan doesn't get anything for me either yet I have a working instalation. Based on your dmesg output I believe your drivers are up and running.
Question, do you have /dev/dvb/adapter0 created?

about channels.conf check
/usr/src/linuxtv.cvs/dvb-apps/util/szap/channels-conf/dvb-t/

you should have some default channels.conf there

Let me know if it helps

---

### Post by ubuntme on 2005-08-24
update,

I do have /dev/dvb/adaptor... etc :)

And I managed to get a channels.conf for my area. :)

I can now get mplayer and xine working.  Though I have to use the command line for mplayer, for xine I can't figure out how to change channels... :(

Whats next??

Thanks!!

---

### Post by art2003 on 2005-08-25
Oh you are through the difficult bits now!
Two ways to change channels:
Either keep the terminal window from where you run vdr in focus or
install xine-lib and xine-ui with VDR keys built in support.

You  need a version of xine-lib that has been patched for VDR.
Install them with:
dpkg -i libxine-dev_1.0.1-2_i386.deb
and
dpkg -i libxine1_1.0.1-2_i386.deb

You need a rather new version of xine
Install as usual with dpkg -i xine-ui_0.99.3-1_i386.deb

Get the 3 above mentioned files from my other posting:
[http://www.ubuntuforums.org/showthread.php?t=57597&highlight=vdr+twinhan](http://www.ubuntuforums.org/showthread.php?t=57597&highlight=vdr+twinhan)

Now when you run vdr as a daemon if you wish and then get xine to connect to vdr,
you can right-click, settings, keymap edit and towards the end you will have all keys  for VDR (which you will have to define)

Let me know if you get stuck.

---

