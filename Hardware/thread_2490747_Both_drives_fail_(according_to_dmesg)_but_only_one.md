---
title: "Both drives fail (according to dmesg) but only one is faulty."
date: 2023-09-14
forum: Hardware
---

### Post by sunstormrider on 2023-09-14
[COLOR=#232629][FONT=-apple-system]**I have a couple of standard SATA drives connected to an Ubuntu box via a Yottermaster 5-bay JBOD array. Recently, while both drives were mounted fine at boot, inside 2 minutes they [B]*both*** showed IO errors.
[/B][/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]**[B]Thinking it's unlikely (except power surge etc (which I've not had)) for both drives to fail at the same time, I suspected the Yottermaster and / or the cable. Having tested the same drives in another Yottermaster and with a different cable, same results: *both* drives failed after about 2 minutes. So it must be the drives.**[/B][/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][B][B][B]
Again - I didn't think both drives could fail at the same time but that's what dmesg was showing me: errors on /dev/sdm and /dev/sdl. So I booted with just one of them in the array. For 24 hours now - no errors whatsoever. Then did the same with the other drive. The second drive reported errors immediately. So it must be that when both drives were installed, the bad drive was somehow affecting the dmesg output and showing [/B][/B][/B]**[B][B][B]both**[/B][/B][/B]**[B][B] drives failing. I've never seen this behaviour before.**[/B][/B][/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][B][B][B][B]
Is there anything I could have done to avoid this? As there were only 2 drives in the 5-bay array (i.e. 3 empty bays) - it was comparatively easy to identify this - but had all 5 bays been full - and only one disk was bad - it would have been much more time consuming to identify the bad drive.[/B][/B][/B][/B][/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]**[B][B][B]Thanks R**[/B][/B][/B][/FONT][/COLOR]

---

### Post by TheFu on 2023-09-15
I'd suspect Yottermaster as the issue. 

Get a $30 USB dock and see if the same issue happens.  Use smartctl/smartmontools to see what the drive internal testing claims. Need to perform standard troubleshooting techniques.
[LIST=1]
[*]Simplify
[*]Test
[*]Repeat until the only possible component is clear
[/LIST]

Drives can fail around the same. It is just bad luck.  Not all drives are compatible with all arrays.  Are the drives on the official approved list for those arrays?

I can see where more testing and simplification would clarify which parts are actually the cause.

[LIST]
[*]Swap the drives around inside the array? Could be 1 port is bad.
[*]Test each drive separately without the array involved at all?
[*]Test using completely different disk controllers?  SATA, USB, eSATA, SAS, Infiniband?
[*]Swap the internal cables in the array, if there are any?  I've seen this issue myself. My newer arrays don't have internal cables to avoid that issue. That is both good and bad, since the cables are a another point of failure, but failures with the direct attached port in the back of an array for each disk can become loose too. One of my older arrays has a loose back-port. The fix was to never put the drive with the loose connection into that array again.
[*]
[/LIST]
Isolate each component until the failed part is clear.

---

