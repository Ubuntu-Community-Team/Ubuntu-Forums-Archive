---
title: "Wanting to have Ubuntu/XP Dual boot one one disk, and data on the other."
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by Cam42 on 2009-05-30
I have two HDDs in my computer, and I want the primary (80GB) to be used for WinXP/Ubuntu +apps, with the secondary (90GB) to be used for Data.
How do I configure both operating systems to use the second drive as the default place to store data? (as in windows have the "My Documents" be on the second drive, and in Ubuntu the Documents, Music, Videos etc also)?

---

### Post by badaveil on 2009-05-30
On the same configuration as yours but I didn't dual boot my pc, why don't you pull off the power from your secondary h/d like what I did to mine, install the O/S and when it works well, plug in the power back. It works for me. Just a humble suggestion.

---

### Post by Cam42 on 2009-05-31
bump.

---

### Post by Mark Phelps on 2009-06-01
> **Cam42 said:**
> How do I configure both operating systems to use the second drive as the default place to store data? (as in windows have the "My Documents" be on the second drive, and in Ubuntu the Documents, Music, Videos etc also)?
You're not going to be able to do exactly what you want -- Linux is not Windows.  While you can create a shared data drive (NTFS format would probably be the best), your "default" location for files related to your account in Ubuntu would be under the $Home directory, which (AFAIK) needs to be on Linux-compatible formatted filesystem.

So, you can have the other files (e.g., music, video, data) on the shared drive but I don't believe you can (or should) have $Home created there.

---

