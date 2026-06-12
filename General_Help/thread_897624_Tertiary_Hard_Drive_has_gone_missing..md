---
title: "Tertiary Hard Drive has gone missing."
date: 2008-08-22
forum: General Help
---

### Post by Alex Carroll on 2008-08-22
Earlier today I booted up, moved ~30GB of data from my 40GB secondary hard drive to my 500GB tertiary hard drive. I dragged the information window to an empty desktop and let it move for about an hour, forgetting all about it. I eventually got bored of surfing and shut the computer down.

I'm fairly sure that the task had finished by the time I shut down, but I'm not sure what else can explain my problem:

Booting up for the second time today, I have discovered that my 500GB drive will not mount. Trying "sudo mount -a" gives the following message:

```
alex@alex-desktop:~$ sudo mount -a
[sudo] password for alex:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

A sizeable amount of data, in the region of 180GB, is quite important to me, and I'd rather not lose it. Thus a reformat is *currently* out of the question. If it turns out to be a more serious problem, I will reconsider.

EDIT: Output of dmesg | tail

```
alex@alex-desktop:~$ dmesg | tail
[   58.934942] wlan0: authenticated
[   58.934945] wlan0: associate with AP 00:1d:7e:bb:d4:84
[   58.938170] wlan0: authentication frame received from 00:1d:7e:bb:d4:84, but not in authenticate state - ignored
[   58.942581] wlan0: authentication frame received from 00:1d:7e:bb:d4:84, but not in authenticate state - ignored
[   58.943658] wlan0: RX AssocResp from 00:1d:7e:bb:d4:84 (capab=0x431 status=0 aid=3)
[   58.943662] wlan0: associated
[   58.944492] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   66.867402] wlan0: no IPv6 routers present
[  138.011106] EXT2-fs error (device sdc1): ext2_check_descriptors: Block bitmap for group 768 not in group (block 267665280)!
[  138.011112] EXT2-fs: group descriptors corrupted!

```

---

### Post by Alex Carroll on 2008-08-22
'fsck' is currently running, after about an hour of holding the 'y' key, it's finished a secondary check and is asking me to clone blocks with multiple claims. I'm not sure what this means, but I've chosen 'yes' on every prompt so far, since it's naming files that I want to keep.

---

### Post by Alex Carroll on 2008-08-22
Well, fsck fixed it. Thanks for listening guys :P

---

