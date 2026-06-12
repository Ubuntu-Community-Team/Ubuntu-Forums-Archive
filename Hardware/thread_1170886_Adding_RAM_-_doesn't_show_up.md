---
title: "Adding RAM - doesn't show up?"
date: 2009-05-26
forum: Hardware
---

### Post by scradock on 2009-05-26
I'm trying to rescue a Sony Vaio PCG-FRV31 laptop, about 5-6 years old. It needs more RAM (originally 2x256MB; supposed to take up to 2x512MB). I've bought two matching 512MB SO-DIMMS (Corsair, from Newegg), but the machine still reports only 447MB RAM (512-64video),just as it does with the original RAM. This is consistent between Ubuntu (System Monitor), memtest86+, and even Windows XP, except that Ubuntu reports a few MB less.

The "512MB" SO-DIMM is automatically detected as 512MB if I put it into another machine (HP Pavilion laptop), but the 1GB SO-DIMM from the HP machine registers as only 512MB in the Sony. It looks as if the Sony is only accessing half of the memory on each SO-DIMM bigger than 256MB - is that possible?

I've re-seated the SO-DIMMS several times, with no power or battery, so that re-booting has to have a clean start - still comes back as 447MB total.

So I have three types of SO-DIMM: 256MB registers as 256MB in the Sony;
512MB registers as 256MB in the Sony; 1GB registers as 512MB in the Sony. All register as expected from the labels in the HP.

Does anyone have any insights as to what may be going on? Is there an obscure setting in the Sony to allow it to use more than 512MB RAM? But it accepts (half of) a 1GB SO-DIMM plus (half of) a 512MB SO-DIMM?????

The Sony User's Manual sets out how to replace RAM - and suggests I check that the added RAM is correctly detected (in Windows). But it doesn't say what to do if it isn't detected.

One clue: the original (256MB) SO-DIMMS are PC2100S 266MHz; the new ones (512MB and 1GB) are PC2700S 333MHz, sold as backwards compatible with PC2100S.

Any help gratefully accepted!

---

### Post by jerrrys on 2009-05-26
hi scradock...

i don't own an FRV31, but i thought i try to google up an answer.  instead i came up with only questions.

1 i can't seem to confirm a 2700 is backwards compatible

2 a newegg memory search does not show a frv31, but they do sell 2100 ram. why not just use 2100?

---

### Post by scradock on 2009-05-27
Thanks - yes, I found Googling gave more questions than answers. One site did specifically offer PC2700S as a more recent backward-compatible replacement for PC2100S, but I didn't check with Newegg on that point. I guess I shall have to see if Newegg will trade them back - probably not, but I can try.

---

### Post by scradock on 2009-05-27
I checked the Crucial website - it was quite definite:

"PC2100 memory &#8212; which Crucial no longer carries - is DDR designed for use in systems with a 133MHz front-side bus (providing a 266 MT/s data transfer rate). The "2100" refers to the module's bandwidth (the maximum amount of data it can transfer each second), which is 2100MB/s, or 2.1GB/s. PC2100 is used primarily in AMD® Athlon® systems, Pentium® III systems, and Pentium IV systems. PC2100 has been replaced by PC2700, which is backward-compatible.

PC2700 memory &#8212; the slowest DDR memory speed that Crucial now carries - is DDR designed for use in systems with a 166MHz front-side bus (providing a 333 MT/s data transfer rate). The "2700" refers to the module's bandwidth (the maximum amount of data it can transfer each second), which is 2700MB/s, or 2.7GB/s. PC2700 is backward-compatible for PC1600 and PC2100." 

There seems to be no reason why the PC2700 memory should not all be seen from the above; and Newegg do not accept returns for a different product.......

Any more ideas, anyone?

---

