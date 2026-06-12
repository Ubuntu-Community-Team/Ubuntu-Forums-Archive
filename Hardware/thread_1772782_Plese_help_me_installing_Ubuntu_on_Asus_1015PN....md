---
title: "Plese help me installing Ubuntu on Asus 1015PN..."
date: 2011-06-01
forum: Hardware
---

### Post by Markino76 on 2011-06-01
Hi guys, I'm trying to install Ubuntu 11.04 on my Asus 1015PN but after a lot of fresh installations I still can't get all working fine. :(

I found some guide but I think the scenario is changed because now there are some updates that make some stuffs works out of the box, new nvidia drivers ecc... I'd really appreciate a new guide from scratch.

My problem is that even if it seems to works fine after installation... I've got some problems with wifi card (the fastweb hub somethins stuck and I can't get connected to the internet. MyFastpage is ok but very very slow) and my most important problem is that I can't get xbmc to play 1080p video: it seems that vdpau doesn't works fine even if I installed the last version of nvidia driver fro nvidia web site.

I'm going to describe the way I install and hope someone can help me to understand where I'm wrong:
- Boot from usb and install Ubuntu 11.04 (standard 32bit or have I to install amd64?)
- Uncomment from source.list (apt) the 2 backports repository (multiverse) and 2 canonical reporitory and then sudo apt-get update
- updates all the system via Update manager
- install Broadcom , nvidia driver and nvidia 3d experimental via 3rd part drivers
- reboot
- install last nvidia driver downlaoded from nvidia web site running sudo sh <nvidiadriver>.run after performing sudo /etc/init.d/gdm stop
- reboot
- add xbmc ppa and changing natty to maverick in the repositoy (sudo apt-get update)
- install xbmc via apt-get install xbmc

Do I miss something? Why now I can't see 1080p video smooth?


I've got the xbmc.log file reporting something wrong about vdpau and libcrystalhd (?):
...
ERROR: Unable to load libcrystalhd.so.3, reason: libcrystalhd.so.3: cannot open shared object file: No such file or directory
...
NOTICE: vdp_device = 0xffffffff vdp_st = 0x00000001
ERROR: (VDPAU) unable to init VDPAU - vdp_st = 0x1.  Falling back.
NOTICE: CDVDVideoCodecFFmpeg::Open() Failed to get VDPAU device
NOTICE:  (VDPAU) Close
....
WARNING: Decode - avcodec_decode_video didn't consume the full packet. size: 58873, consumed: 0
...



S.O.S!!! :(((

---

