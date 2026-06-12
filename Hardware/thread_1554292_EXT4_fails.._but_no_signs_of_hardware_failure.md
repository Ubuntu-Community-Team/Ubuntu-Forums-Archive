---
title: "EXT4 fails.. but no signs of hardware failure"
date: 2010-08-16
forum: Hardware
---

### Post by sofamensch on 2010-08-16
I was just using a quite fresh installation of 10.04, when out of the sudden the console throws a lot of read errors.

I couldnt copy them, but i recall them to be something like
"Error reading Bitmap..."
"I/O error... reading sector **"

Its the second time this happened today. I already did a full smartctl-test, and it delivers me good smart attributes, and also the extended tests delivers 00% errors.

I managed to write down the sectors, and used badblocks to check that area, but this also tells me that the sectors are OK.

This is really annoying, because it completely KILLS the whole partition unrecoverable! 
I am using an Thinkpad T42 with a 30GB Hitachi (which is mounted upside down, very weird).

---

