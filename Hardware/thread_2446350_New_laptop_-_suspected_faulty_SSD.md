---
title: "New laptop - suspected faulty SSD"
date: 2020-06-29
forum: Hardware
---

### Post by FrenchyFungus on 2020-06-29
I bought a [Novatech nSpire N1678]("https://www.novatech.co.uk/laptop/range/novatechnspiren1678.html") laptop recently, which I installed Ubuntu 20.04 on. Unfortunately, it crashes a couple of times per day - often enough that I started keeping track of them.

Some examples:

"Screen froze whilst opening Firefox. Keyboard not working. Mouse stopped moving after ~15s. Rebooted using Ctrl+Alt+Shift+[RIESUB]. On reboot, saw a purple box saying "No bootable device". Entering settings, and then using F10 to "save and exit" (but without changing any settings) allowed booting."

"Keyboard stopped working browsing Firefox. Closing lid and reopening fixed issue."

"Closed laptop lid, when reopened got a black screen with "input/output error" and "Ext4-FS" messages. Ctrl+Alt+F4 etc. all same. Rebooted with Ctrl+Alt+Shift+[RIESUB]. Booted normally."

A fresh install of Ubuntu didn't fix the problem. Am I right to suspect that the SSD drive is faulty?

Novatech have suggested that I install Windows and see if I have similar issues. I'd prefer not to buy a copy of Windows just to troubleshoot, so am wondering if there's anything else to try first.

Does anyone have any advice?

---

### Post by crip720 on 2020-06-29
Have read some posts about I5 cpu giving problems with Ubuntu(can google).  Don't need to buy Windows just to check hardware, they give a few months to try(also google for free Win 10 legal).  Will need woeusb or mkusb to make bootable windows USB from Ubuntu.  Should also disable internet when installing Win 10, less hassle.

---

### Post by FrenchyFungus on 2020-06-29
That's very helpful, thank you. I'll try some other Linux distros too.

---

### Post by Yellow Pasque on 2020-06-29
See if there are any BIOS updates available. (Normally, I would look for you, but Novatech's support site leaves a lot to be desired.)

---

### Post by oldfred on 2020-06-29
In addition to UEFI/BIOS updates, you need to check for SSD firmware updates either from Novatech or SSD vendor.

---

### Post by 2912pwil2 on 2020-06-30
This might help for checking the drive 
[https://ubuntuforums.org/showthread.php?t=2446027](https://ubuntuforums.org/showthread.php?t=2446027)

---

