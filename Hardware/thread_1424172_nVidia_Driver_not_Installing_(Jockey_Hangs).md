---
title: "nVidia Driver not Installing (Jockey Hangs)"
date: 2010-03-07
forum: Hardware
---

### Post by sarloth on 2010-03-07
I have installed Ubuntu plenty of times on this machine and never had problems getting Jockey to install the video drivers. However with 9.10 it appears to hang when trying to install the nVidia driver (version 173).

My graphics card is a nVidia GeForce FX 5200.

lshw -c display:

```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5
       resources: memory:fd000000-fdffffff memory:e8000000-efffffff(prefetchable) memory:fe9e0000-fe9fffff(prefetchable)
```

The first time I ran jockey the bar stopped moving about half-way through for several minutes. I noticed afterwards that many of the nVidia drivers were installed but the card is still unclaimed and I still show no proprietary drivers in use.

After re-booting and running it again it is stuck at about a quarter of the way through the progress bar.

Unfortunately jockey doesn't have a terminal information display to tell me what it is/was doing when it gets/got stuck.

I am wondering if there is a way to manually undo anything it did before so that it can try again, or to manually undo its changes and then do them again manually, any advice?

Thanks in advance for any help.

---

### Post by xcross on 2010-06-02
I have the identical problem. Did you ever solve this?

---

### Post by dino99 on 2010-06-02
1) goto synaptic:

- remove/purge (right click) all the nvidia packages installed

- add this ppa into synaptic repo:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

2) remove xorg.conf: sudo rm -f /etc/X11/xorg.conf

3) update, upgrade 

4) into synaptic install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

5) reboot

6 ) check into "system admin hardware driver" that nvidia-current is activated

---

