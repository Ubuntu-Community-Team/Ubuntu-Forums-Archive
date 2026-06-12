---
title: "Computer powers itself up after shut down"
date: 2014-02-02
forum: Hardware
---

### Post by mamboknave on 2014-02-02
The problem is as described in the post title.

Board: ASrock H87M pro4, with the latest BIOS; Ubuntu is 12.04.

1) I do shut the computer down from the menu OR with the command line "poweroff" OR "shutdown -P now"
2) It totally shuts down, all fans, all leds, the screen.
3) It stays off for a few secs, fooling me.
4) Then it restarts, powering itself back on.

The only way to impede the restart is to switch off the power supply on the back of the case at 3).
Doing so, it still *tries* to do 4). You hear the fans starting, but the little charge remaining in the the power unit gets discharged in a moment and it stops there. It's off.

This problem started around mid Jan, when I updated the Linux Kernel.

Cannot say if that's due to the Linux Kernel, as I updated again to the newest release and the problem persists.

I could not find similar issues in the forum.

Looking fwd for some hint/help.

P.S. I checked also the wake-on-LAN in the BIOS > Advanced > ACPI Config. There, "Wake from Onboard LAN" is disabled.

---

### Post by jp734 on 2014-02-02
I bought a used mobo that I was told was working fine, but when I got it the SATA connections doesn't work. Also, it does what you described, turns back on by itself. I updated the BIOS and never had the problems again. Happy using SATA conns with my hard drive right now.

---

