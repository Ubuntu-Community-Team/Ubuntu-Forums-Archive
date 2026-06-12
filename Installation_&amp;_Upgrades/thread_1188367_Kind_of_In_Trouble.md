---
title: "Kind of In Trouble"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Justin511 on 2009-06-15
So today I was trying to make it so Ubuntu was the only OS on my EeePC 1000HA.  While stupidly messing with the partitions, I managed to delete everything.

When booting the tiny machine, I get the message:
> 
Reboot and Select Proper Boot device
or Insert Boot Media in selected Boot device and press a keySo now I don't know what to do, obviously I can't boot from a CD since there is no drive, and it won't work from the USB drive with the ISO on it.

Can anyone help me, because I really need it. :)

Thank you very much!

Justin

*You can also AIM me at justinmaz077.

---

### Post by Therion on 2009-06-15
> **Justin511 said:**
> ... it won't work from the USB drive with the ISO on it.
Why not?  Did you try using **Netbootin** to create the bootable USB thumb-drive?

---

### Post by Justin511 on 2009-06-15
No, don't know what that is. Can you give me a link?

And I didn't say it was impossible, just said it wasn't working for me.

---

### Post by Justin511 on 2009-06-15
So I tried doing a tut for booting off USB but it didn't work.

Can anyone help?

---

### Post by mhgsys on 2009-06-15
Is the usb boot device enabled in your bios settings?

---

### Post by H2SO_four on 2009-06-15
> **mhgsys said:**
> Is the usb boot device enabled in your bios settings?

+1 with boot from usb he could boot from thumb drive with installer, problem solved...  hopefully.

---

### Post by Therion on 2009-06-15
Have you tried these instructions?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Jekshadow on 2009-06-15
If you want to recover your files (and you haven't reinstalled ubuntu yet), use ubuntu-rescue-remix (google it) and then use gddrescue to create a drive image and then use photorec to get your files. Also try testdisk, it can sometimes recover partitions.

---

