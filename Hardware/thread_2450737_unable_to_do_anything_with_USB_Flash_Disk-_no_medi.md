---
title: "unable to do anything with USB Flash Disk- no medium found"
date: 2020-09-19
forum: Hardware
---

### Post by mdziczkowski on 2020-09-19
Hello. I have a following problem with my USB Flash Disk with I had found and wanted to check if I can re-use it:

[B][U]Information about the Flash drive:
[/U][/B]

[LIST]
[*]**product:** USB Flash Drive [5DC:A793] 
[*]**vendor:** Lexar [0x5DC] 
[*]**physical id:** 2 
[*]**bus info:** usb@1:4.2 
[*]**logical name:** scsi3 
[*]**version:** 11.00 
[*]**capabilities:** usb-2.00 scsi emulated scsi-host 
[*]**configuration:** driver=usb-storage maxpower=100mA speed=480Mbit/s 
[*]**idProduct**: 0xa793 
[/LIST]

As you see above, the USB drive is detected by the system (used commands: lshw, lsusb), but it isn't detected neither by gparted, nor fdisk. I'm not even able to mount it - I get the "no medium found" error.

Does anyone got a clue how I could fix it and get access to it's content?

---

### Post by oldfred on 2020-09-19
If you used it as an installer with the hybrid DVD/flash configuration, it has no partition(s). You normally have to zero out beginning of drive, so you  then can add normal partitions.

Reset USB flash that was dd'd to make it usable again, reuse
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266) & 
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)
[https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection](https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection)

---

### Post by Yellow Pasque on 2020-09-19
What does dmesg say after you plug in the drive?
```
dmesg | tail -n 20
```

---

