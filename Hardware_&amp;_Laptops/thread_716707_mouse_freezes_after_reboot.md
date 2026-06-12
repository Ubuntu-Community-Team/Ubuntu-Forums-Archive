---
title: "mouse freezes after reboot"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by mehageg on 2008-03-06
Hi all!

I used to work fine with 7.10 and a ps/2 mouse as suddenly, after a reboot, the mouse froze in the middle of the screen.

- the freeze is during splash screen and during KDE/xfce sessions.
- when using the liveCD there's no problem with the mouse.
- when running [FONT="System"]sudo cat /dev/input/mice[/FONT] I see nothing, even when the mouse moves/clicks.
- here's the output of lspci:
```

Module                  Size  Used by
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
8139cp                 25088  0 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
8139too                27776  0 
mii                     6528  2 8139cp,8139too
floppy                 60004  0 
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
sata_via               12548  3 
via82cxxx              10372  0 [permanent]
ide_core              116804  2 ide_cd,via82cxxx
ata_generic             8452  0 
libata                125168  2 sata_via,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

10x

---

### Post by mehageg on 2008-03-13
I solved my problem and would like to share my findings.

somehow, the /etc/modules files was changed so that drivers were not loaded.
I booted from the liveCD, saved the modules list: ```
lsmod > mods_list
``` then booted again, and added mods to /etc/modules
```

sudo su
cat mods_list | awk '{print $1}' >> /etc/modules

```

---

