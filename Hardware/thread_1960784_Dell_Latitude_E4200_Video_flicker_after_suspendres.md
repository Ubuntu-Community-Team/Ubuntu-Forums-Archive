---
title: "Dell Latitude E4200 Video flicker after suspend/resume"
date: 2012-04-18
forum: Hardware
---

### Post by Bubbel on 2012-04-18
Hi there,

For anyone with similar problems:

It's the BIOS. I recently updated my Ubuntu installation to Precise and at the same time I thought it was a smart move to check for a BIOS upgrade. Which there was. Upgraded to A22 and the problem started to manifest itself:
When the laptop woke up from suspend, the screen was constantly flickering. At first I suspected Ubuntu, but when I got to a console screen (Ctrl+Alt+F1), the problem was still there.

Downgradig the BIOS to A21 did not solve the problem, but another downgrade to A20 did!

Additional information:
lspci output
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

Hope it helps someone.

Greetz, 8-[

---

