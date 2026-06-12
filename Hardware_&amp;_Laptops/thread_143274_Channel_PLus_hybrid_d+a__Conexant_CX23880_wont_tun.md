---
title: "Channel PLus hybrid d+a  Conexant CX23880 wont tune"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by mediumcool on 2006-03-12
Hi there, I cant get this card working (Channel PLus hybrid d+a  Conexant CX23880)  with  Kdetv.

It wont tune channels, however there is probably more going wrong here.

lspci -

0000:01:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0000:01:09.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
0000:01:09.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
0000:01:09.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)

lsmod -

cx88_blackbird         21692  0
af_packet              24520  2
tuner                  44932  0
cx88_dvb               10660  0
cx8802                 12740  2 cx88_blackbird,cx88_dvb
mt352                   7236  1 cx88_dvb
or51132                10564  1 cx88_dvb
video_buf_dvb           6884  1 cx88_dvb
dvb_core               88392  1 video_buf_dvb
nxt200x                16036  1 cx88_dvb
lgdt330x                8636  1 cx88_dvb
cx22702                 6980  1 cx88_dvb
dvb_pll                11044  4 cx88_dvb,or51132,nxt200x,cx22702
cx8800                 34668  1 cx88_blackbird
cx88xx                 64384  4 cx88_blackbird,cx88_dvb,cx8802,cx8800
i2c_algo_bit            9800  1 cx88xx
psmouse                39972  0
video_buf              22724  6 cx88_blackbird,cx88_dvb,cx8802,video_buf_dvb,cx8800,cx88xx
ir_common               9892  1 cx88xx
serio_raw               7748  0
tveeprom               15312  1 cx88xx
v4l1_compat            15204  1 cx8800
v4l2_common             6080  1 cx8800
btcx_risc               5288  3 cx8802,cx8800,cx88xx
i2c_nforce2             7104  0
snd_intel8x0           35452  4
videodev               10144  3 cx88_blackbird,cx8800,cx88xx
nvidia               4090960  18
agpgart                36784  1 nvidia
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
i2c_core               22848  12 i2c_acpi_ec,tuner,cx88_dvb,mt352,or51132,nxt200x,lgdt330x,cx22702,cx88xx,i2c_algo_bit,tveeprom,i2c_nforce2
snd_ac97_codec         99520  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96644  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
snd_timer              26884  2 snd_pcm
snd                    59972  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  2 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
evdev                  10176  2
ext3                  148104  1
jbd                    65876  1 ext3
forcedeth              25572  0
ehci_hcd               33800  0
ohci_hcd               22724  0
usbcore               137700  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 35780  1
cdrom                  41408  2 sr_mod,ide_cd
ide_disk               19200  3
generic                 5124  0
amd74xx                15068  0 [permanent]
sata_nv                10020  0
libata                 64872  1 sata_nv
scsi_mod              145448  3 sr_mod,sbp2,libata
thermal                13768  0
processor              26344  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13768  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

when i try the channel wizard, it comes up blank.

i am new to tv cards, i am in australia and used composite 1 and pal-bg


any help/pointers greatly appreciated

---

### Post by mediumcool on 2006-03-13
Here is the output from kdetv when started from console:

ALSA lib control.c:817:(snd_ctl_open_noupdate) Invalid CTL
kdetvv4lsetup: using X11 display :0.0
WARNING: Your X-Server has no DGA support.
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=unknown
seteuid(root): Operation not permitted
kdetv: WARNING: v4ldev: kdetvv4lsetup had some trouble. Trying to continue anyway.
Creating vbi proxy client, rev.
$Id: proxy-client.c,v 1.9 2005/01/20 20:56:11 mschimek Exp $
proxy_msg: connect: error 2, No such file or directory
kdetv: WARNING: VBIDecoder: vbi_capture_proxy_new error: Connection via socket failed, server not running.
Try to open V4L2 0.20 VBI device, libzvbi interface rev.
  $Id: io-v4l2.c,v 1.31 2004/12/30 02:24:11 mschimek Exp $
Opened /dev/vbi0
Try to open V4L2 2.6 VBI device, libzvbi interface rev.
  $Id: io-v4l2k.c,v 1.34 2005/10/04 10:06:33 mschimek Exp $
Opened /dev/vbi0
/dev/vbi0 (UNKNOWN/GENERIC) is a v4l2 vbi device,
driver cx8800, version 0x00000005
Using streaming interface
Current scanning system is 525
Querying current vbi parameters... success
VBI capture parameters supported: format 59455247 [GREY], 28636363 Hz, 2048 bpl, offs 244, F1 9...25, F2 272...288, flags 00000000
VBI capture parameters granted: format 59455247 [GREY], 28636363 Hz, 2048 bpl, offs 244, F1 9...25, F2 272...288, flags 00000000
Nyquist check passed
Request decoding of services 0x60000c7f, strict level -1
Will capture services 0x00000060, added 0x60 commit:1
Requesting 16 streaming i/o buffers
Mapping 16 streaming i/o buffers
Successful opened /dev/vbi0 (UNKNOWN/GENERIC)
kdetv: WARNING: MainWindow::setupInfraRed(): Lirc not available
kdetv: WARNING: SaverControl: Error in DCOP communication. Unable to disable KDE Screensaver.
kdetv: WARNING: VolumeController::doSetVolume: AudioManager failed, trying SourceManager
kdetv: WARNING: VolumeController::doSetVolume: AudioManager failed, trying SourceManager

if anyone has any starting points fo me i would be most geatful as i dont mind looking stuff up myself and trying things, just have no idea where to start.

---

