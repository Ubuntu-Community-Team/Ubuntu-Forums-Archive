---
title: "intermittent black video from Logitech Webcam Pro 9000"
date: 2013-10-27
forum: Hardware
---

### Post by halfbeing on 2013-10-27
Hello.

Sometimes my webcam works fine, but sometimes it gives me black video in both Skype and Cheese. This obviously makes receiving Skype calls pretty hit-and-miss. When it does this I have found no solution but to reboot. My camera is a Logitech Webcam Pro 9000. Is there any way I can stop this happening?

---

### Post by dannyboy79 on 2013-10-27
you could find out which module it uses and when it's a black screen you could try to remove the module and then re-add it. what modules are currently running when the camera works?
```
lsmod
```

---

### Post by halfbeing on 2013-10-27
This is what lsmod gives me:

Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               320359  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13274  3 
joydev                 17332  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371941  10 bnep,rfcomm
arc4                   12608  2 
snd_hda_codec_conexant    56945  1 
snd_hda_intel          44075  3 
iwl3945                69075  0 
snd_hda_codec         188696  2 snd_hda_codec_conexant,snd_hda_intel
ip6t_REJECT            12910  1 
snd_usb_audio         149162  3 
snd_usbmidi_lib        25070  1 snd_usb_audio
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
xt_hl                  12521  6 
uvcvideo               80885  0 
snd_pcm               101983  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
ip6t_rt                13507  3 
videobuf2_vmalloc      13216  1 uvcvideo
iwlegacy              100487  1 iwl3945
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
nf_conntrack_ipv6      18938  9 
nf_defrag_ipv6         34616  1 nf_conntrack_ipv6
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ipt_REJECT             12541  1 
microcode              23518  0 
xt_LOG                 17718  8 
snd_seq_midi           13324  0 
xt_limit               12711  11 
mac80211              613561  2 iwl3945,iwlegacy
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                97626  0 
xt_tcpudp              12884  22 
pcmcia                 61727  0 
binfmt_misc            17468  1 
xt_addrtype            12635  4 
snd_rawmidi            30095  2 snd_usbmidi_lib,snd_seq_midi
nf_conntrack_ipv4      15012  9 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_conntrack           12760  18 
r852                   18301  0 
sm_common              16860  1 r852
serio_raw              13413  0 
thinkpad_acpi          80701  0 
nand                   64353  2 r852,sm_common
nand_ecc               13312  1 nand
nvram                  14362  1 thinkpad_acpi
r592                   18023  0 
nand_bch               13227  1 nand
yenta_socket           41019  0 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nand_ids                8627  1 nand
nf_nat_ftp             12741  0 
nf_nat                 26653  1 nf_nat_ftp
bch                    17397  1 nand_bch
lpc_ich                21080  0 
nf_conntrack_ftp       18608  1 nf_nat_ftp
mtd                    55348  2 nand,sm_common
nf_conntrack           91736  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
memstick               16760  1 r592
cfg80211              496195  3 iwl3945,iwlegacy,mac80211
pcmcia_rsrc            18407  1 yenta_socket
iptable_filter         12810  1 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ip_tables              27239  1 iptable_filter
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
pcmcia_core            23592  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  25 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
tpm_tis                19123  0 
soundcore              12680  1 snd
mac_hid                13205  0 
coretemp               13435  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
dm_crypt               22728  1 
sdhci_pci              18985  0 
firewire_ohci          40060  0 
sdhci                  42630  1 sdhci_pci
tg3                   162230  0 
firewire_core          64476  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
i915                  655899  4 
ptp                    18580  1 tg3
pps_core               19027  1 ptp
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
drm                   296739  5 i915,drm_kms_helper
video                  19318  1 i915

---

### Post by dannyboy79 on 2013-10-28
ok, it's a uvcvideo capable webcam and it looks like the modules loaded. is it a possibility that the picture settings of the webcam are just really dark? have you checked this out yet?
[http://phoxis.org/2012/02/24/fix-dark-video-in-skype-for-linux/](http://phoxis.org/2012/02/24/fix-dark-video-in-skype-for-linux/)

i have a logitch c260 and I use guvcview to capture facecam's and such and I never have a problem with skype. what version of skype are you using and where did you DL it from? can you please try out guvcview and see if you have a black screen there as well? and or try to issue 

```
cat /dev/video0 > webcam1.ts
```

do you see a light come on on the webcam letting you know it's recording? after a minute or so, click ctrl-c for it to stop recording. now try to play that file using whatever media player you have installed. it's a file called webcam1.ts and would be located within whatever working directory you were in when you ran the command line command. (most likely your home directory.)

good luck

---

### Post by halfbeing on 2013-10-28
Thanks for the pointers. I will have to wait for the problem to occur again before I can try using guvcview.

---

### Post by halfbeing on 2013-10-28
Thanks for the pointer. I shall have to wait until the problem occurs again before I can try guvcview. However the problem occurs not only in Skype but also in Cheese, so it doesn't look like a Skype problem as such.

---

### Post by dannyboy79 on 2013-10-28
i don't know what's causing it but if you want to solve it without having to restart your laptop you could try the following 2 commands

```
sudo rmmod uvcvideo
```

```
sudo modprobe uvcvideo
```

again, good luck. it almost sounds like the module doesn't get loaded IF you have a black screen in both cheese and skype, so when you see the black screen try to issue the lsmod command and look for the uvcvideo line and if it's no in lsmod than you simple have to sudo modprobe uvcvideo and you should be good then. let me know

---

### Post by halfbeing on 2013-10-29
The problem has just occurred again. I've tried the "sudo rmmod uvcvideo" route, but Skype continued to show a black picture. I've tried running guvcview and playing with the settings, but even though I get a good picture in guvcview, the picture in Skype remains black. I then tried opening Cheese and found that there too I had a black picture. So the problem is not limited to Skype, since it occurs also in Cheese, but it does not occur with all applications because it does not occur with guvcview.

---

### Post by dannyboy79 on 2013-11-01
if it works in guvcview than i am assuming maybe some permission access issue with those apps to the video device node. if you issue sudo rmmod uvcvideo than you have to reload the driver using sudo modprobe uvcvideo.

have you tried launcing cheese or skype from the terminal to see what messages are being displayed

it possible that some of this reading may aid you.
[https://bbs.archlinux.org/viewtopic.php?pid=1241639#p1241639](https://bbs.archlinux.org/viewtopic.php?pid=1241639#p1241639)
 let me know if i can help possibly with any question you have about the link

---

### Post by halfbeing on 2014-01-25
The latest state of play is that I found the problem occurred much less frequently once I switched from Unity to XFCE. At the same time the problem of waking from sleep with the network dead happened much less frequently as well, and I suspect therefore that the problems are connected.

I discovered on one of the rare occasions that the problem reoccurred that simply logging out and logging in again was enough to get Cheese and Skype working again.

However now the problem has taken a much darker turn. Video has stopped working in Skype and Cheese and nothing I do will bring it back. Not even rebooting.

---

