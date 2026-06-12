---
title: "Adaptec 19160 driver on Ubuntu 20.04"
date: 2021-01-07
forum: Hardware
---

### Post by spacedcowboy2 on 2021-01-07
So I've got an old hard drive and tape unit that I actually want to get some stuff off - the problem is that although I can see it using lspci (it's the second one)...
 
```

[COLOR=#000000][FONT=Menlo]root@backup:/home# lspci | grep SCSI[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]01:00.0 Serial Attached [COLOR=#b42419]**SCSI**[/COLOR] controller: ATTO Technology, Inc. ExpressSAS 6Gb/s SAS/SATA HBA[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]07:02.0 [COLOR=#b42419]**SCSI**[/COLOR] storage controller: Adaptec Device 0001 (rev 02)[/FONT][/COLOR]

```

lsscsi isn't picking anything up... (that's just the SATA disk). There isn't currently anything connected to the ATTO SCSI connector but there will be soon...

```

[COLOR=#000000][FONT=Menlo]root@backup:/home# lsscsi[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]][1:0:0:0]    disk    ATA      ST2000DM001-9YN1 CC4C  /dev/sda [/FONT][/COLOR]

```

Looking online (it's been literally years since I used this disk), it seems there were some instructions for Suse Linux ...

> 
[COLOR=#333333]According to the SuSE hardware database (which has been known to make a few mistakes), if you have an aha-19160, you should use the aic7xxx module.[/COLOR]

[COLOR=#333333]This module works well, as I use it with a different card, aha2940a, and it works well. To set it up, look edit the /etc/modules.conf (sometimes /etc/conf.modules) and add the line[/COLOR]

[COLOR=#333333]alias scsi_hostadapter aic7xxx[/COLOR]

[COLOR=#333333]or change the scsi_hostadapter to aic7xxx[/COLOR]

[COLOR=#333333]then, as root, type depmod -a[/COLOR]
[COLOR=#333333]then, modprobe aic7xxx[/COLOR]


... but I'm not sure how that applies to Ubuntu - especially when (as you can see) there's another SCSI host-adapter in place on the machine already.

Very much appreciate any help on this :)

---

