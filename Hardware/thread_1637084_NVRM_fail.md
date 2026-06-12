---
title: "NVRM fail"
date: 2010-12-04
forum: Hardware
---

### Post by h.mehdi on 2010-12-04
Hi,

I have following error in my messages file right after Ubuntu 10.10 startup on my Dell Studio XPS 1340

```
Dec  4 09:23:24 mehdi-laptop kernel: [   12.562185] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=600
Dec  4 09:23:24 mehdi-laptop kernel: [   12.564693] EXT4-fs (sda5): re-mounted. Opts: commit=600
Dec  4 09:23:25 mehdi-laptop kernel: [   14.040098] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
Dec  4 09:23:26 mehdi-laptop kernel: [   15.060151] hda-intel: Codec #1 probe error; disabling it...
Dec  4 09:23:29 mehdi-laptop kernel: [   18.240167] input: HDA NVidia Mic at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input10
Dec  4 09:23:29 mehdi-laptop kernel: [   18.240333] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
Dec  4 09:23:29 mehdi-laptop kernel: [   18.240389] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input12
Dec  4 09:23:29 mehdi-laptop kernel: [   18.332784] ppdev: user-space parallel port driver
Dec  4 09:23:31 mehdi-laptop kernel: [   20.346535] NVRM: failed to copy vbios to system memory.
Dec  4 09:23:31 mehdi-laptop kernel: [   20.348029] NVRM: RmInitAdapter failed! (0x30:0xffffffff:819)
Dec  4 09:23:31 mehdi-laptop kernel: [   20.348034] NVRM: rm_init_adapter(0) failed
Dec  4 09:23:34 mehdi-laptop kernel: [   22.906241] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=600
Dec  4 09:23:34 mehdi-laptop kernel: [   22.908547] EXT4-fs (sda5): re-mounted. Opts: commit=600

```

---

### Post by h.mehdi on 2010-12-06
bump :|

---

### Post by gamemaniac7 on 2010-12-06
Are your graphic cards 9400M G (onboard) and G210M?

---

### Post by h.mehdi on 2010-12-06
Thanks for reply. Yes, It's 9400M
this is my lspci

```
$ lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)
```

---

### Post by h.mehdi on 2010-12-07
I upgraded to 2.6.36 maverick kernel and still have same issue...

---

### Post by h.mehdi on 2010-12-20
Any ideas on this?

---

