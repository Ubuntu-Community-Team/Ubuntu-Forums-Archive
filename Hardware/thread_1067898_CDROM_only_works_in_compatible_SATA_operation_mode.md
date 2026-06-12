---
title: "CDROM only works in compatible SATA operation mode"
date: 2009-02-12
forum: Hardware
---

### Post by jou770d on 2009-02-12
Sometimes my laptop's cdrom  decide to work: it opens, reads the inserted disk but, when I try to eject the disk from nautilus I get an error saying that there's no media. Eject button does absolutely nothing. I can only eject using the little pin hole or what ever it's called, doing that restores functionality to the eject button, but if I insert a disk it doesn't get recognized.
But most of the time it wouldn't even open the first time around.

After some googling I found a *_workaround_*: if I changed SATA operation mode in the bios from enhanced to compatible the cdrom works on Intrepid. However I can't consider this a solution as I'm dual booting and Windows won't work if I changed that mode. Reinstalling windows is not a possibility at the time. (I should also mention that the cdrom works without problems on Windows so it's not a hardware issue).

The device is an Asus M51Va-as024c, if it matters.

Thanks in advance!

---

### Post by jou770d on 2009-02-13
sudo bump

---

### Post by jou770d on 2009-02-13
One more bump...

---

### Post by jou770d on 2009-02-23
I'm not sure why this is happening but I know now what's making it happen.
I've switched from 32 Ubuntu to 64, when I did that I made grub default bootloader (previously I kept Vista's) and that solved the issue.
However if I was using windows and wanted to switch to Ubuntu, restarting while make the cdrom useless. A shutdown is necessary for it to work uunder Ubuntu...
I hope this helps someone else.

---

