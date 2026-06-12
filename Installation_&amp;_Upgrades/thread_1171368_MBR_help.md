---
title: "MBR help"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by artisan on 2009-05-27
It looks like I have wiped by MBR.

Neither of my hard drives will boot (both Ubuntu.
How do I go about restoring them?

Any help would be appreciated.

Thank you.

---

### Post by Rodamar on 2009-05-27
I, myself, was able to re-install grub simply by downloading and then burning onto CD the latest karmic koala daily build then booting with that CD.  One of the options offered by that build is to repair a damaged system.  After going through a menu steered dialog I was able to choose that grub be re-installed (in my case into the mbr on hd0).    I got an error message to the effect that a serious error prevented the re-installation of grub into the mbr when I entered &quot;hd0&quot; without the quotation marks as being the disk to which to write grub.  It worked when I instead entered exactly the &quot;(hd0)&quot; without the quotes that the menu steered dialog had suggested I enter.    Now grub functions normally again at my PC.  8)

---

### Post by artisan on 2009-05-27
Thanks. I am downloading it right now and shall give it a try.

Thanks.

---

### Post by artisan on 2009-05-27
Ah! I am using a live cd and cannot use my cd drive...

---

### Post by artisan on 2009-05-27
Fixed. Thanks for your help.
I did a google search and found a way round the issue.
Now I cannot find the link to the article I used so, I cannot post how I repaired it :(

---

