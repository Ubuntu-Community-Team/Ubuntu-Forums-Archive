---
title: "Burning cd/dvd's don't work"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Osamabingandhi on 2006-10-29
When i start to burn a cd or dvd it starts out fine and everything seems fine but it just burns for a second or two and then quits. I can play the dvd and the file is there but just a small portion of it. How do i make the burning program to burn everything?

I have a nec 3520b burner and it works fine in windows. I have burned with all programs in ubuntu and none work. I have understood all programs use the same program to burn, any linux ubuntu program that use another program to burn? I have managed to burn dvd's with dvddecryptor through wine. Anyone has any ideas?

---

### Post by Osamabingandhi on 2006-10-30
Fixed it with "sudo hdparm -d0 /dev/cdrom", i had to turn my DMA off...

---

