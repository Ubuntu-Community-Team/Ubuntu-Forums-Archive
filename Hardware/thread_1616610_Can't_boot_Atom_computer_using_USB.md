---
title: "Can't boot Atom computer using USB"
date: 2010-11-08
forum: Hardware
---

### Post by pepsifx357 on 2010-11-08
I bought this atom motherboard with the 330 processor and I can't get it to boot with a usb flash drive.  The options are there in the BIOS, but when it starts up it just says "BOOT ERROR."  I've tried a few different distros using the Startup Disk creator in Ubuntu, and still get the same thing.  This little computer doesn't have a cdrom drive so this is the only way to get an OS on it, apart from removing the hard drive and installing it in another computer.  Any thought would be appreciated.

Thanks

---

### Post by malangaman on 2010-11-08
USB Drives will develop bad spots. Have you tried with a different flash drive?
Are you sure the correct boot order has been selected in BIOS? On an ACER Aspire one  which has an atom cpu, you can press the f12 key to select USB as boot device after power up.

---

### Post by kerry_s on 2010-11-08
startup disk creator only works for ubuntu & most ubuntu based distros.

use unetbootin for other distro's.

---

### Post by pepsifx357 on 2010-11-09
I found the problem.  Under the BIOS settings there is a setting for the type of USB drive.  I had to choose "all fixed disks" for it to work.

By the way, startup disk creator works perfectly for Ubuntu and Linux Mint;  For now until they fix their Debian distro.  I imaging it would probably work for a lot of Ubuntu variants.

---

