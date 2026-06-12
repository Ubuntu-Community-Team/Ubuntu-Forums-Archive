---
title: "Ubuntu install freezes (so does XP?)"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by tnunamak on 2008-12-18
I've got a computer I'm trying to get working for my family that has been sitting around for a while by putting ubuntu on it. There is some sort of problem, however. First, I tried using two different HDDs that had XP installed. The computer reboots every time it gets to the XP loading screen, and when I tried doing an XP chkdsk it froze.

The ubuntu installer freezes after the initial loading bar stops bouncing back and forth. I checked the installation CD and it's good, I've even used it on other computers before. This seems like some sort of hardware problem, does anyone have an idea as to what it could be?

---

### Post by lovelyvik293 on 2008-12-18
You can use the alternative cd.

---

### Post by jenkinbr on 2008-12-18
> **tnunamak said:**
> I've got a computer I'm trying to get working for my family that has been sitting around for a while by putting ubuntu on it. There is some sort of problem, however. First, I tried using two different HDDs that had XP installed. The computer reboots every time it gets to the XP loading screen, and when I tried doing an XP chkdsk it froze.

The ubuntu installer freezes after the initial loading bar stops bouncing back and forth. I checked the installation CD and it's good, I've even used it on other computers before. This seems like some sort of hardware problem, does anyone have an idea as to what it could be?
Your problem seems to match a problem I had on another computer of mine. Insert the live CD and when you get to the menu, go down to the memtest86+ option.  If you see a lot of red error messages, you have bad ram, and will need to isolate the bad stick by removeing each stick (or pair) one by one, and repeat the test, until you've Isolated the problem.

When I had this problem, it turned out to be a bad stick of ram.  Removing or replacing it solved the problem.

---

### Post by tnunamak on 2008-12-18
Thanks for the tip. It does look like this happens a lot to people with memory issues. I've performed the memory test though and both sticks check out, I've also tried removing one at a time. Another thing is that the live cd doesn't freeze when the hard drive is not connected, but it hangs on a black screen with a "_" at the top.

---

