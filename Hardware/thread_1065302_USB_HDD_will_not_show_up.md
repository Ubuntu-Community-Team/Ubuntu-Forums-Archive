---
title: "USB HDD will not show up"
date: 2009-02-09
forum: Hardware
---

### Post by bellboa45 on 2009-02-09
When I plug my usb hdd into my computer the light on the usb drive comes on but the computer dose not react. I've tried using the "sudo fdisk -l" command but it only lists the main hard drive that the OS is installed on. The drive was used fine with the computer earlier in the day

---

### Post by taurus on 2009-02-09
What's the output of this command from a terminal (make sure the USB drive is still plugged in)?

```
dmesg | tail
```

---

### Post by sedawk on 2009-02-09
Turn on the computer, but do not connect the USB HDD.

Open a terminal and clear the message buffer with "sudo dmesg -c".

Now connect the drive, wait 10-15 seconds and the run
"dmesg" again. Post the new output lines here ...

---

