---
title: "Have tried several methods to eject/dismount external hdd to no avail"
date: 2011-02-24
forum: Hardware
---

### Post by Univ3rse on 2011-02-24
Ok, before anyone becomes frustrated w/me, I have scoured the web and forums for a solution and all seem to be similar but have had the same end result. I am running **Ubuntu Maverick**. Whenever I **attempt to** **remove my external hdd** it is removed from my desktop, but **still accessible** from the places menu or computer. This is a known bug, but again none of the solutions appear to be working for me. Here are the solutions I have tried and the results:

**Solution 1.** Selecting **"safely remove drive"** from drop down menu on desktop or from computer returns this **message:**
[B]Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5)
SYNCHRONIZE CACHE: OK
STOP UNIT: FAILED: No such file or directory[/B]

**Solution 2.** using command line: **"sudo eject /dev/sdc"** returns this message with in the terminal: "**eject: unable to find or open device for: `/dev/sdc'"**

**Solution 3.** using command line: **"sudo eject /dev/sdb"** results in **nothing**, so I'm assuming this is improper syntax for my version of ubuntu.

Any help w/this would be greatly appreciated. I am a linux noob, so I do realize that perhaps I misunderstood the previous solutions and need to add something specific to my command lines. **Thank you for your time.**

---

### Post by Univ3rse on 2011-02-28
bump.

---

