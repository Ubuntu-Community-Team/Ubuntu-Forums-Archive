---
title: "Tape Device Order (st*)"
date: 2017-04-18
forum: Hardware
---

### Post by tlex300 on 2017-04-18
Hello Guys,

I'm new here. Hope someone can assist. I'm currently having issues with the "tape drive ordering" under **/dev/tape/by-id/*. **Every time I reboot, the order of st# changes.

I would like it to stay as st0, st1, st2 etc. 

[B]Currently (after reboot):
[/B]**Order of WWID stays the same, only st# order changes.*

/dev/tape/by-id/
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a001 -> ../..**/st2**
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a001-nst -> ../../nst2
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a007 -> ../../**st6**
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a007-nst -> ../../nst6
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a00d -> ../../**st5**
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a00d-nst -> ../../nst5
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a013 -> ../../**st3**
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a013-nst -> ../../nst3
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a019 -> ../../**st0**
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a019-nst -> ../../nst0
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a01f -> ../../**st1**
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a01f-nst -> ../../nst1
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a049 -> ../../**st7**
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a049-nst -> ../../nst7
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a04f -> ../../**st4**
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a04f-nst -> ../../nst4


[B]Need Drive Order To Be This Way (and stay this way even after reboots):

[/B]
/dev/tape/by-id/
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a001 -> ../../st0
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a001-nst -> ../../nst0
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a007 -> ../../st1
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a007-nst -> ../../nst1
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a00d -> ../../st2
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a00d-nst -> ../../nst2
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a013 -> ../../st3
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a013-nst -> ../../nst3
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a019 -> ../../st4
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a019-nst -> ../../nst4
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a01f -> ../../st5
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a01f-nst -> ../../nst5
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a049 -> ../../st6
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a049-nst -> ../../nst6
lrwxrwxrwx 1 root root   9 Apr 18 20:35 scsi-3500308c00163a04f -> ../../st7
lrwxrwxrwx 1 root root  10 Apr 18 20:35 scsi-3500308c00163a04f-nst -> ../../nst7

Any assistance is appreciated. Thanks!

---

### Post by frostschutz on 2017-04-19
All device names are assigned in a first come, first serve... this affects stX, sdX, vdX, ... and that's why there are the /dev/{tape,disk,...}/by-{path,id,uuid,...}/ aliases to give them fixed names. If you need fixed names, just use these.

Sometimes you can affect the order by making drivers built-in, or forcing loading modules early/late, but there is no guarantee for it. Sometimes a device might have a hiccup causing it to be detected late and the order randomly switches.

In the end you still have to stick to one of the /dev/*/by-*/aliases or create your own alias with custom udev rule.

---

### Post by tlex300 on 2017-04-19
Thanks for the response frostschutz. I also tried using a udev rule for the tape drives - using WWID. But it doesn't seem to work. 

#Tape Drives
KERNEL=="st0", SUBSYSTEM=="scsi_tape", KERNELS=="0:0:1:0", ATTRS{wwid}=="naa.500308c00163a001", MODE="0660"
KERNEL=="st1", SUBSYSTEM=="scsi_tape", KERNELS=="0:0:2:0", ATTRS{wwid}=="naa.500308c00163a007", MODE="0660"
KERNEL=="st2", SUBSYSTEM=="scsi_tape", KERNELS=="0:0:3:0", ATTRS{wwid}=="naa.500308c00163a00d", MODE="0660"
KERNEL=="st3", SUBSYSTEM=="scsi_tape", KERNELS=="0:0:4:0", ATTRS{wwid}=="naa.500308c00163a013", MODE="0660"
KERNEL=="st4", SUBSYSTEM=="scsi_tape", KERNELS=="0:0:5:0", ATTRS{wwid}=="naa.500308c00163a019", MODE="0660"
KERNEL=="st5", SUBSYSTEM=="scsi_tape", KERNELS=="0:0:6:0", ATTRS{wwid}=="naa.500308c00163a01f", MODE="0660"
KERNEL=="st6", SUBSYSTEM=="scsi_tape", KERNELS=="0:0:7:0", ATTRS{wwid}=="naa.500308c00163a049", MODE="0660"
KERNEL=="st7", SUBSYSTEM=="scsi_tape", KERNELS=="0:0:8:0", ATTRS{wwid}=="naa.500308c00163a04f",  MODE="0660"

I'll keep digging....

---

