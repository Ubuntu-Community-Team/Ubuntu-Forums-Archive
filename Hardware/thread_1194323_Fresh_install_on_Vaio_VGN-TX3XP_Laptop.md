---
title: "Fresh install on Vaio VGN-TX3XP Laptop"
date: 2009-06-22
forum: Hardware
---

### Post by kevinatkins on 2009-06-22
Hi,

I'm in the process of trying to 'sell' Ubuntu to a business client of mine.

He has a (very expensive 2 years ago!) Sony Vaio VGN-TX3XP laptop which originally had Windows XP installed. After XP fell over, I suggested we try Ubuntu, to which he agreed.

This machine is one of Sony's 'ultra-compact' offerings, originally purchased for the following benefits -

- Extremely compact and light (11" widescreen display);
- Very long runtime (7+ hours on one charge originally, down to about 5.5 hours under Windows now).

The general machine spec is -
- Intel Core Solo U1400 processor, 1.2GHz;
- 512MB RAM;
- Intel GMA 950 graphics, 128MB RAM;
- 80GB 4200RPM hard drive.

After installing Ubuntu successfully, the following issues were immediately apparent -

- The battery run-time was very poor - down to around 2.5 hours;
- Overall performance was generally poor, especially multi-tasking, with frequent interface freezes.

I really hope my client sticks with Ubuntu, but his initial impressions have sadly been less than positive, so it's important that I can show a real improvement, or he'll be asking for XP back!

I have now made the following tweaks, which appear to have improved matters somewhat -
- Set laptop-mode to enabled in /etc/default/acpi-support;
- Allowed laptop mode to control various aspects of on-battery performance in the /etc/laptop-mode/conf.d/* config files;
- Turned desktop effects off;
- Removed the tracker indexing daemon;
- Set mounts to 'noatime' in /etc/fstab.

Battery life seems better, although the Gnome power manager applet seems to insist on under-estimating the time remaining (showing 3 hours when powertop shows closer to 7? And empirical testing so far would indicate better than 4 hours runtime, which is acceptable.) The interface also seems snappier, if not quite as good as a fresh XP install.

Is there anything else I might have missed? I understand that 9.04 has some issues with graphics acceleration with the Intel graphics chipset - would these manifest in the sort of issues described?

Many thanks in advance for any comments!

Kevin.

---

