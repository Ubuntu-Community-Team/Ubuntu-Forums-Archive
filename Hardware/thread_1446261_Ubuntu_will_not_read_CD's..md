---
title: "Ubuntu will not read CD's."
date: 2010-04-03
forum: Hardware
---

### Post by Piro24 on 2010-04-03
Hello.

I've been having a weird problem, that I just noticed. Ubuntu will not read any CDs. I've tried multiple ones, some of which are practically brand new, so I'm 100% sure it's not bad disks.

The weird thing, mounting and reading DVD's isn't a problem. Most of the stuff I've found only was related to DVD problems, but none to exclusively CDs. Relevant output below.

```

patrick@patrick-laptop:~$ mount /dev/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

patrick@patrick-laptop:~$ dmesg | tail
[1196611.542124] end_request: I/O error, dev sr0, sector 2496
[1196611.542244] UDF-fs: No anchor found
[1196611.542249] UDF-fs: No partition found (1)
[1196611.582902] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[1196611.582917] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[1196611.582928] ILI
[1196611.582933] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[1196611.582948] end_request: I/O error, dev sr0, sector 64
[1196611.583087] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[1196617.100096] usb 1-2: reset high speed USB device using ehci_hcd and address 26


```

Any suggestions?

Edit: Just before anyone suggests this, adding -o loop only gets rid of the first error mount gives (The one about it being a block device.) But otherwise it doesn't help.

---

