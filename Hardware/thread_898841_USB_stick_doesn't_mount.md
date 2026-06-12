---
title: "USB stick doesn't mount"
date: 2008-08-23
forum: Hardware
---

### Post by jynyl on 2008-08-23
Running Kubuntu 8.04, various USB memory sticks auto mount fine, but not one labeled LG xtick.  This xtick mounts fine under Windows XP and OS X.

How can I mount this memory stick under Linux?  Is there a driver I need to install?  Or some configuration that needs to be adjusted?

How can I troubleshoot this?

TIA

Peter

---

### Post by raul_ on 2008-08-23
To troubleshoot:

insert the pen and then, in a terminal, type 

```

dmesg | tail

```

---

### Post by jynyl on 2008-08-23
```
$ dmesg | tail
[586510.973191] sd 9:0:0:0: [sdc] Write Protect is off
[586510.973194] sd 9:0:0:0: [sdc] Mode Sense: 03 00 00 00
[586510.973197] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[586510.973200]  sdc: sdc1
[586510.978248] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[586510.978292] sd 9:0:0:0: Attached scsi generic sg3 type 0
[586823.206560] kjournald starting.  Commit interval 5 seconds
[586823.206751] EXT3 FS on sdb2, internal journal
[586823.206757] EXT3-fs: mounted filesystem with ordered data mode.
[586857.960201] usb 5-7: USB disconnect, address 6
```
I have been plugging in a few mem sticks, so without timestamps in dmesg, it isn't clear to me what lines relate to the xtick.

---

### Post by jynyl on 2008-08-23
Actually, after trying another mem stick, it appears dmesg adds lines similar to the above when a different mem stick is plugged in, but dmesg adds no lines when the xtick mem stick is plugged in.

---

### Post by jynyl on 2008-08-23
Now I'm confused.  When plugged into a different USB port (there are 2 on the front of this box), the xtick mounts ok.  It hasn't mounted before, and I have tried several times (a while ago), on 2 different Linux boxes.  The dmesg following mount of the xtick follows.

```
$ dmesg | tail
[661872.521622] sd 11:0:0:0: [sdc] Write Protect is off
[661872.521627] sd 11:0:0:0: [sdc] Mode Sense: 43 00 00 00
[661872.521629] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[661872.524328] sd 11:0:0:0: [sdc] 1966080 512-byte hardware sectors (1007 MB)
[661872.525076] sd 11:0:0:0: [sdc] Write Protect is off
[661872.525080] sd 11:0:0:0: [sdc] Mode Sense: 43 00 00 00
[661872.525083] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[661872.525086]  sdc: sdc1
[661872.525895] sd 11:0:0:0: [sdc] Attached SCSI removable disk
[661872.525939] sd 11:0:0:0: Attached scsi generic sg3 type 0
```

---

