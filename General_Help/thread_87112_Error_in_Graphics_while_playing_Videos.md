---
title: "Error in Graphics while playing Videos?"
date: 2005-11-07
forum: General Help
---

### Post by Svip on 2005-11-07
So Friday last week, I got my laptop and installed Ubuntu on it, meaning that it doesn't dual boot, it only runs on Linux.

Until now, I have been very pleased, it found my wireless unit, and actually it worked! I have heard stories about Linux not being able to configure with the wireless cards.

However, I'm still having a problem with playing videos, I know I wasn't looking for a laptop with a huge graphic card, but I assumed that it could at least play videos to where you can sit back and enjoy it.

But no, when I play videos using MPlayer ( which I can for some reason only use being root ), it goes to full screen ( note: Normal resolution is 1024x768 ), and the colours is limited to black, dark green and pink, it's horrible to look at, I wish that I could install some drivers so my videos at least would live up to being able to at least look at.

I am not entirely sure what the graphic card is, as the manual was wrong ( the manual was about a desktop by the same company ( what a bunch of retards ) ), and according to the website, it's just onboard with up to 128mb ( which should work for videos at least! ).

I will appreciate any help. :)

*I apologies for my English, I'm not native at English.*

**Update:**
A friend told me to do ```
 $ dmesg | grep vga 
```
So I did, and here's the output:
```
[4294668.494000] vga16fb: initializing
[4294668.494000] vga16fb: mapped to 0xc00a0000
```

**Update2:**
Okay, here just goes some video/vga related information grep vga couldn't get:
```
[4294668.078000] Boot video device is 0000:00:02.0
[4294823.380000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[4294668.616000] fb0: VGA16 VGA frame buffer device
```

**Update3:**
I think "oops" would be in order;
```
$ lspci | grep -i vga
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 04)
```

---

