---
title: "Not detecting USB hard drives"
date: 2011-03-27
forum: Hardware
---

### Post by silentwol on 2011-03-27
I've just tried plugging in two USB 2 flash drives. I'm running the latest mythbuntu.

Here's dmesg:
usb 1-6: new high speed USB device using ehci_hcd and address 14

That's literally all it gives. It doesn't detect any partitions (fdisk lists nothing), so it seems something is fundamentally wrong. Both drives work in windows - they are completely standard flash drives.

Any ideas?

Thanks!

---

### Post by dandnsmith on 2011-03-28
So, is that Windows on the same machine which is failing to recognise them under mythubuntu?
If so, can you check with another distro (via liveCD), just to rule out another sector of possible areas?

You may need to post details of the USB sticks and the machine hardware if tests pin it down to distro/release. Also, someone else may have had the same problem.

---

