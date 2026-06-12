---
title: "testing if badRAM was successful"
date: 2012-10-05
forum: Hardware
---

### Post by PGScooter on 2012-10-05
I would like to use memtester as a way of testing whether badRAM is working (or rather, if *I* set badRAM correctly). If it's working, the memory shouldn't be accessible by memtester, right? I ran memtest86+ with the configure option of outputting badRAM addresses. After running for 10 hours it found 9 errors at GRUB_BADRAM="0xc507fd24,0xfffffffc". I then added the following to my /etc/default/grub:

GRUB_BADRAM="0xc507fd24,0xfffffffc"

Then I booted normally and ran memtester. memtester soon found errors "at offset 0x9eaa3d20". I then changed my badRAM to:
GRUB_BADRAM="0xc507fd24,0xfffffffc,0x9eaa3d20,0xffffffff"

and rebooted. memtester again found errors. I'm not sure what to think because memtester is finding many errors so quickly where with memtest86+ I left it running 10 hours and it only found 9 error.

Any advice?

Note that I'm on 64-bit.

Thanks a lot.

---

### Post by PGScooter on 2012-10-06
I was not running sudo update-grub (which was clearly documented in the comments in /etc/default/grub). Now the output of free confirms that "total" mem is reduced by 16 bytes. So I have confirmed that badRAM is indeed blocking some memory (presumably the memory I asked it to).

The question remains that I still receive errors from memtester. I don't know what to make of that. Should I trust a 10 hour run from memtest86+ to come up with all of the bad addresses? It doesn't seem believable that memtester could find errors within 10 minutes that memtest86+ doesn't find in 10 hours.

---

