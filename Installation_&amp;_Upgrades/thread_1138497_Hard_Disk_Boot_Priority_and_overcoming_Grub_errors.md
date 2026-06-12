---
title: "Hard Disk Boot Priority and overcoming Grub errors"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by yetanothersteve on 2009-04-26
I have now successfully performed a fresh install of 9.04 AMD64 Desktop, but ran into some Grub errors along the way. I was running 8.04 upgraded from 7.10.

I have two internal hard drives,
[LIST=1]
[*]Seagate 250GB SATA
[*]Maxtor 80GB ATA
[/LIST]

The Maxtor used to be the primary back when I was running 6.06LTS and it has had Grub, Lilo, and the Windows boot loader installed at various times. The Seagate has been the primary since 7.10 and has only ever had Grub installed. 

What I did not realize was that the Maxtor was first in the BIOS boot order and actually held the active Grub information in the MBR. After the install of 9.04 and the write of Grub to the Seagate, I booted to a Grub Error 2. I tried installing Grub to the Maxtor but that left me booting to a Grub prompt. I discovered that the BIOS has a Boot Priority Setting and that the Maxtor was first in the boot priority, which I did not want. 

[LIST]
[*]Advanced BIOS Features
[*]Boot Seq & Floppy Setup
[*]Hard Disk Boot Priority
[/LIST]

Screenshot:
[http://home.comcast.net/~coding/hddprioritybios.jpg]("http://home.comcast.net/~coding/hddprioritybios.jpg")

If I had set the Seagate to be first in the BIOS boot priority before the install, it would have alleviated a lot of confusion for me and a lot of reading the Grub manual trying to get 9.04 to boot.

All is well now and I am thoroughly enjoying Jaunty, just thought I would pass along my experience.

---

