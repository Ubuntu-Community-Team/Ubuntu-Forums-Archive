---
title: "searching for workaround for &quot;failed command: READ DMA&quot;"
date: 2011-12-08
forum: Hardware
---

### Post by thinking on 2011-12-08
hi,

i have a SSD OCZ-ONYX disk in my via artigo A1000 server which causes
the following dmesg error log
```

[  189.441055] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  189.462145] ata1.00: BMDMA stat 0x25
[  189.483181] ata1.00: failed command: READ DMA
[  189.504211] ata1.00: cmd c8/00:00:f0:42:ff/00:00:00:00:00/e0 tag 0 dma 131072 in
[  189.504219]          res 51/84:00:f0:42:ff/84:04:01:00:00/e0 Emask 0x10 (ATA bus error)
[  189.546980] ata1.00: status: { DRDY ERR }
[  189.568447] ata1.00: error: { ICRC ABRT }
[  189.589762] ata1: soft resetting link
[  189.768295] ata1.00: configured for UDMA/133
[  189.768329] ata1: EH complete

```

sometimes i also get "failed command: READ DMA EXT".

anyway - i'm trying to resolve this for quite a while now
(checking hardware problems as best as i can, doing ubuntu updates, using "options libata noacpi=1" in /etc/modprobe.d/options.conf)
but nothing seems to work

the problem i have is that the server seems to kind of freeze sooner or later
with freeze i mean that i can't connect via SSH - sometimes i get an error like using wrong key-pairs, sometimes the server isnt reachable at all
maybe it takes a few hours or event weeks to freeze
so the problems are pretty undeterministic which i think is related to above dmesg log and how much the server is used

since i can't solve this i dont want to try to solve the cause but just prevent kernel from logging this error in dmesg
so, my idea is that i want to prevent dmesg flooding

anyone knows how i can disable logging of such errors?
maybe just changing some kernel params which dont even lead to this error like disabling ata dma usage or such?

thanks for any help

edit:
from the kernel sources i noticed that the error comes from drivers/ata/libata-eh.c
and in the [kernel parameters list]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")
i found the option 'libata.dma'
via /etc/default/grub i modified the kernel params to
GRUB_CMDLINE_LINUX="libata.dma=0 libata.noacpi=1"
then 'sudo update-grub' and reboot
currently the error seems gone and everything is working properly

---

