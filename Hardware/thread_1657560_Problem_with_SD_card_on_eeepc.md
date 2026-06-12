---
title: "Problem with SD card on eeepc"
date: 2011-01-01
forum: Hardware
---

### Post by Garcimore on 2011-01-01
Hi,

I'm running Ubuntu 10.10 Netbook Remix on a eeepc 1002HA.

When i plug a SD card in the internal device, nothing happens. Nothing appears in /dev. Just my hard drive sda.

I searched a long time on the internet but i could not resolve this problem.

Here is dmesg :

[  677.288191] usb 4-1: new full speed USB device using uhci_hcd and address 83
[  677.352282] hub 4-0:1.0: unable to enumerate USB device on port 1
[  677.688254] hub 1-0:1.0: unable to enumerate USB device on port 5
[  678.400159] hub 1-0:1.0: unable to enumerate USB device on port 5
[  680.321113] hub 1-0:1.0: connect-debounce failed, port 5 disabled

Any idea ?

Thanks

---

### Post by Jechem on 2011-01-01
I've noticed this kind of problem before on my 701. Try putting the SD card in the slot and logout or reboot. Sometimes it recognizes it. I think it's a bug on the SD card reader with Ubuntu.

---

### Post by Garcimore on 2011-01-02
It does not work. The same messages appears during the boot process :

55.276247] hub 4-0:1.0: unable to enumerate USB device on port 1
[   55.532230] hub 1-0:1.0: unable to enumerate USB device on port 5
[   55.888234] hub 4-0:1.0: unable to enumerate USB device on port 1
[   56.432235] hub 1-0:1.0: unable to enumerate USB device on port 5
[   59.168133] hub 1-0:1.0: unable to enumerate USB device on port 5
[   59.636215] hub 1-0:1.0: unable to enumerate USB device on port 5
[   59.837109] hub 4-0:1.0: unable to enumerate USB device on port 1
[   60.465142] hub 1-0:1.0: unable to enumerate USB device on port 5
[   60.849132] hub 4-0:1.0: unable to enumerate USB device on port 1

---

### Post by fabricator4 on 2011-01-02
> **Garcimore said:**
> Hi,

I'm running Ubuntu 10.10 Netbook Remix on a eeepc 1002HA.

When i plug a SD card in the internal device, nothing happens. Nothing appears in /dev. Just my hard drive sda.


Have a look at "computer" in "Places" (ie Nautilus)  Do you see a device called "Single Flash Reader" ?  That is the internal device with no card installed.  With a card installed the volume label is appended to this.  If you don't see the device then there may be a problem with the device, or a driver.

You could also see if the drive is visible to the system another way:

```
sudo fdisk -l
```

If it's there but not mounted you can mount it manually. (then investigate why it's not mounting automatically)

Also (and maybe I should have put this first) try the obvious - see if the system works with other SD cards, preferably low tech known good ones.

As a last resort try the full version of 10.4 LTS Lucid Lynx - it's been rock solid wrt USB drives on my Eee-PC which is a 900SD. I gave up on the netbook version because it seemed to miss stuff that my 900SD really needed like some device drivers - can't remember which ones now but the 'puter didn't work well until I installed the full version.

Chris.

---

