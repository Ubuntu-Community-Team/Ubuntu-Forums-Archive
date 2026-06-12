---
title: "What's wrong with having xorg.conf file?"
date: 2013-07-12
forum: Hardware
---

### Post by jp734 on 2013-07-12
I've seen a lot of posts that encourages people to not create and use the file and I just want to understand why. I personally have lubuntu 13.04, crunchbang Waldorf and LinuxMint 15 triple boot, triple screen using two cards and I was ONLY able to get my setup working by creating my xorg.conf file. And I never had any problem so far except for Mint's cinnamon crashing when enabling  xinerama (triple screen works though and haven't doing much research on it). Other than that lubuntu and crunchbang are perfectly working.

---

### Post by Cheesemill on 2013-07-13
It's recommended not to use one because nowadays everything ***should*** be automatically detected.

In the rare cases where this doesn't happen (as in your situation) then having an xorg.conf file is the only fix.

There is nothing wrong with having an xorg.conf it's just that the X developers are trying to improve the auto-detection so that it is never needed.

---

### Post by jp734 on 2013-07-13
Ahh...gotcha. Thanks for the info. I guess it's going to be a while before we completely forget about xorg.conf file. As of now, people are still having issues with their monitors not getting the max resolution *(issues with EDID, Horizontal and Vertical refresh rates)*. And I wonder how they are going to determine if a person is using a multi-monitor setup like myself. Well, they are smart individuals and am sure they'll figure it out. For now, as long as xorg.conf gets prioritized if it's present, we'll be able to configure our monitors the way we want it while they are working on it.

---

