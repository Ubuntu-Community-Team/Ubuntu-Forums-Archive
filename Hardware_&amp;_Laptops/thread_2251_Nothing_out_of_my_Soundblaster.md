---
title: "Nothing out of my Soundblaster"
date: 2004-10-26
forum: Hardware &amp; Laptops
---

### Post by princemackenzie on 2004-10-26
Hey everyone-

I have a soundblaster ensoniq audioPCI ess1371 that wont work in ubuntu- i've tried everything.  It shows up under volume control, and i hear some static, but I can not make anything happen.  I've tried all the disable ACPI options at boot also but those just make it hang... and ideas? 8-[

---

### Post by HungSquirrel on 2004-10-26
I have that very card and had no problems under Ubuntu.  Did you upgrade from Debian to Ubuntu, or is this a clean Ubuntu install?

---

### Post by princemackenzie on 2004-10-26
Fresh install... if its any help- the tabs under volume control, some say "oss mixer" and others say "alsa mixer".  There are tabs for everything i can think of(sound out on my video card, for example), but it still doesnt work.

---

### Post by FLeiXiuS on 2004-10-26
sudo modprobe emu10k1

---

### Post by princemackenzie on 2004-10-26
Just tried what fleixius said- still nothing but some static, but it begins and ends whenever a sound is supposed to go off (like during a sound test).  Sorry to be such a pain :sad:...

---

### Post by HungSquirrel on 2004-10-26
If you see some OSS controls and some ALSA it may be that the OSS and ALSA drivers are both running.  This is not good because they conflict.  The Debian solution is to make sure the OSS modules aren't loaded, I believe by adding 'es1371' without the quotes to the end of /etc/hotplug/blacklist .  Debian/Ubuntu guru want to help me here?  I'm not entirely sure I'm accurate.

---

### Post by princemackenzie on 2004-10-27
Adding 'es1371' to the end of the blacklist doesnt work. 

There are indeed OSS and ALSA items under volume control: "eMicro28028[OSS mixer]" and "Ensoniq Audio PCI [ALSA Mixer]" and my video card sound chip (a brooktree bt878, which also comes up with one OSS mixer and other ALSA mixer). I know I dont have that eMicro device.  Muting certain selections inside the OSS mixer will start/stop the static.

Like HungSquirrel said, does anyone have some thoughts?

---

### Post by princemackenzie on 2004-10-27
Update: here are the results of my lsmod.

Module                  Size  Used by
es1371                 33472  0
emu10k1                71812  0
sound                  75308  1 emu10k1
ac97_codec             16908  2 es1371,emu10k1
proc_intf               3968  0
cpufreq_powersave       2048  0
cpufreq_userspace       5336  0
freq_table              4356  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
8139cp                 19072  0
8139too                23936  0
mii                     4864  2 8139cp,8139too
crc32                   4608  2 8139cp,8139too
bt878                  11184  0
snd_bt87x              13640  2
bttv                  143020  1 bt878
video_buf              20356  1 bttv
i2c_algo_bit            8968  1 bttv
v4l2_common             6400  1 bttv
btcx_risc               4744  1 bttv
i2c_core               22416  2 bttv,i2c_algo_bit
videodev                9856  1 bttv
snd_ens1371            23012  3
snd_rawmidi            23232  1 snd_ens1371
snd_seq_device          7944  1 snd_rawmidi
snd_pcm_oss            48168  0
snd_mixer_oss          16640  4 snd_pcm_oss
snd_pcm                85540  3 snd_bt87x,snd_ens1371,snd_pcm_oss
snd_page_alloc         11144  2 snd_bt87x,snd_pcm
snd_timer              23172  1 snd_pcm
snd_ac97_codec         59268  1 snd_ens1371
snd                    50660  13 snd_bt87x,snd_ens1371,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ac97_codec
soundcore               9824  8 es1371,emu10k1,sound,bttv,snd
gameport                4736  2 es1371,snd_ens1371
ohci1394               32004  0
pciehp                 83948  0
shpchp                 87276  0
pci_hotplug            30640  2 pciehp,shpchp
ehci_hcd               27780  0
usblp                  12032  0
ohci_hcd               19460  0
usbcore               104292  5 ehci_hcd,usblp,ohci_hcd
nvidia_agp              7580  1
agpgart                31784  2 nvidia_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
nls_cp437               6016  2
ntfs                   88660  2
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
nvidia               4821428  12
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
ide_cd                 38276  0
evdev                   9088  0
tsdev                   7168  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
reiserfs              207600  1
ide_generic             1664  0
ide_disk               16768  6
amd74xx                13340  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   25904  692
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

This is the only thing i can't get to work... Any guru's have some ideas?

---

### Post by princemackenzie on 2004-10-27
Problem solved.  Conflict with onboard sound from mobo- once disabled in BIOS, problem goes away.  Never a problem in windows, but no worries.  :roll:

Thanks for everyone's help.

---

### Post by muszek on 2005-09-04
worked for me as well (and it was important, this pc will play music in a cafe... and mobo sound is terrible).

thanks!

---

