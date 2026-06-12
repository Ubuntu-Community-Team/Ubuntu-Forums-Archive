---
title: "dark boot screen on Intrepid"
date: 2009-06-01
forum: Hardware
---

### Post by bigblackcar on 2009-06-01
Hi, I've got an Asus V1JP with ATI Mobility Radeon X1700.
Since I've upgraded to Intrepid, the boot screen is very dark and barely readable. The keys combination to make the screen lighter/darker won't work.

I can get the screen to 100% with the brightness applet after boot, but it is a pain to enter the password in the dark. 

If I enter BIOS and dim the brightness with the key combination before GRUB kicks in, the problem is solved. It seems that Ubuntu maps system brightness incorrectly: if BIOS brightness is 100% Ubuntu maps it to 20% or something, if it's lower it's mapped correctly.

Is there any way to solve this?

Thanks.

---

