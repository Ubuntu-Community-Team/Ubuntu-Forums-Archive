---
title: "Laptop unable to boot"
date: 2022-09-28
forum: Hardware
---

### Post by guilhermebfn on 2022-09-28
Hello,

Yesterday, I changed the battery of my Lenovo Ideapad 310-15ISK laptop. In order to do so, I had to completely dismantle my laptop, which involved also removing the HDD. After reassembling it, the laptop said "Default boot missing or boot failed". I tried following the tutorial over at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and run Boot Repair from a live USB stick, but it didn't even give me the option of Recommended Repair, just the [BootInfo summary]("https://paste.ubuntu.com/p/KbcP6FyYc8/"). Is my HDD physically damaged, or is there something else I can do? Note that the HDD had dual boot (Windows 10 and Ubuntu 20.04).

---

### Post by ajgreeny on 2022-09-28
Try booting to a live system from the USB you probably used to install your laptop's OS and you will be able to investigate much better what is going on.

You may also like to try the *Boot-Repair* in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by tea for one on 2022-09-28
0 (zero) OS Detected (Line 19)
No partitions found (Lines 44 - 55)

As you had to remove the HDD, it may be pertinent to check that it has been re-connected correctly?

---

### Post by guilhermebfn on 2022-09-28
Here is the Boot Info: [https://paste.ubuntu.com/p/hy4Dp3TWKd/](https://paste.ubuntu.com/p/hy4Dp3TWKd/). About booting to a live system, I am already running Ubuntu 20.04 from the USB stick, as I had chosen to follow the second option in the Boot Repair guide (I am currently using it to write here).

Edit: I thought quick reply would quote the comment. This is the response to ajgreeny.

---

### Post by guilhermebfn on 2022-09-28
I have already tried to do that, so I figured it must have been something else. I can try it again, though.

Edit: I thought quick reply would quote the comment. This is the response to tea for one.

---

### Post by tea for one on 2022-09-29
Can you access your UEFI Settings and see if your HDD is visible?

---

### Post by guilhermebfn on 2022-09-29
> **tea for one said:**
> Can you access your UEFI Settings and see if your HDD is visible?

When I accessed the BIOS, on the Information tab it said "Hard Disk - Not Detected" :(. I have also tried again to take it off and put it on to see if it was just a poor contact.

---

### Post by tea for one on 2022-09-29
Can you reset all UEFI settings to default - may or may not trigger a response?
By any chance, do you have another drive to test?

---

