---
title: "Testing A Used Laptop's Hardware"
date: 2014-03-06
forum: Hardware
---

### Post by Adam's AI on 2014-03-06
I just bought a used laptop, and have 30 days to return it. I don't know much about hardware. Are there any programs/ways to test the hardware I should use? What do you check when you buy a used laptop (possibly with non-original parts)?

---

### Post by varunendra on 2014-03-06
> **Adam's AI said:**
> What do you check when you buy a used laptop (possibly with non-original parts)?
Hard Disk, Memory (RAM), Battery backup, keypad/touchpad for functionality, display quality and internal wireless card.

All of these can be tested with a Live DVD/USB of Ubuntu or any other Live distro.

[INDENT]To test the harddisk, use either the SMART feature of the BIOS (if it has it), or test the same with Linux tools like "smartctl" (part of "smartmontools" package). Choose a "Detailed" or "Extensive" test.

To test the Memory, boot from a Live DVD/USB > get to "Advanced Boot Menu" by pressing a key during splash screen > Choose "Memtest+" > Run it for at least 8 hours (24 hours is recommended) and see if any of the Passes fail.

To test the Battery, fully charge it, then use it up doing something that drains it at a constant rate, like watching a movie (for heavy task, expect 1-2 hrs backup on a used battery) or just doing some simple text editing on a simple text editor or Libre Office (for lightweight task, expect 2+ hrs).

To test the keypad, use/check all the keys and make sure they are working as expected. For touchpad, make sure it works smoothly and buttons (if any) are working as expected.

To test the screen, open a white image > expand it to full screen (F11 usually) > make sure there are no blind spots or vertical lines on the screen. Blind spots can usually be ignored, but vertical lines usually very quickly (within a week or two) spread to whole screen making it unusable.
Also, obviously check that brightness is good enough for you.

To test the wifi, just boot from the Live DVD/USB and check if it is detected and works. Some wifi adapters will be detected in Linux but may not work without some tweaks or a suitable driver. In that case, post a thread regarding the problem in "Networking & Wireless" section of the forums and we can quickly determine whether it is a hardware fault or a software one.[/INDENT]


There are also some CDs (like SystemRescueCD or HBCD) that are dedicated to test/troubleshoot hardware or software problems of a computer. They contain a bunch of software in ready-to-use state to do all kind of testing you need. [HBCD]("http://www.hirensbootcd.org/download/") (Hiren's Boot CD) is probably one of the best, but be careful with its tools, as it also contains some that can be potentially risky if used improperly.

---

