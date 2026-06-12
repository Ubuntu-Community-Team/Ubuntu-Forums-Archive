---
title: "cryptsetup and encrypted partition NOT mounting"
date: 2011-09-20
forum: Hardware
---

### Post by liju.. on 2011-09-20
Hi,

I have successfully encrypted partition on external HDD using cryptsetup and guide from this address:

[http://ubuntu-tutorials.com/2007/08/...emovable-disk/](http://ubuntu-tutorials.com/2007/08/...emovable-disk/)

I can mount this partition on my 2 laptops, but cannot do this on eeePC 701 with XBMC (actually Ubuntu Karmic) installed. 

using 
```

$ sudo cryptsetup luksOpen /dev/sdc1 secure
```
I got:
```
Enter LUKS passphrase: 
Command failed: unknown hash spec in phdr
```

my lsmod shows:
```

$ lsmod
Module                  Size  Used by
aes_i586                8124  0 
aes_generic            27484  1 aes_i586
cryptd                  6496  0 
lirc_mceusb            15520  0 
lirc_dev               10804  1 lirc_mceusb
joydev                 10272  0 
dm_crypt               12928  0 
uvcvideo               59080  0 
psmouse                56500  0 
videodev               36736  1 uvcvideo
lp                      8964  0 
v4l1_compat            14496  2 uvcvideo,videodev
serio_raw               5280  0 
eeepc_laptop           13936  0 
parport                35340  1 lp
atl2                   25716  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  1 
drm                   159584  1 i915
i2c_algo_bit            5760  1 i915
usb_storage            52576  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

```
I though that maybe I am missing some modules, but cannot really find any that I may be missing.

The other thing is that after reboot I have to manually load aes and cryptd modules.. any ideas?

---

