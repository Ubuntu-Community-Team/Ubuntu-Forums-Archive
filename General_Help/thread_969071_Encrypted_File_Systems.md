---
title: "Encrypted File Systems"
date: 2008-11-03
forum: General Help
---

### Post by JasonRivers on 2008-11-03
Hi all.

Currently I have some important information that is encrypted using PGP, but if I wish to make any changes, then I have to unencrypt it, make the changes, and re encrypt.

What i'm looking for, is a way to encrypt a USB stick, there seems to be alot of information on encrypted file systems, but most seem to have the kernel unencrypt it - I don't really want this, I want to be able to plug it into any system (that has the required keys) and unencrypt it - as I have 5 desktop machines and 3 laptops.

it would be really nice if I could do this using PGP too, but I understand if this is beyond the limitations of PGP.

does anyone have any ideas or good documentation on doing this? - remember this is not part of my actual system, just an encrypted device for me to put files into, and I wish to be able to use it on any machine without recompiling a kernel for it to happen.

Jason.

---

### Post by charlesbrooking on 2008-11-05
Have you looked at EncFS or TrueCrypt?

These will save you decrypting/editing/encrypting files individually with PGP: you can have an encrypted directory (looks like a blob or a directory containing files with random names and contents) and mount its entire contents as an unencrypted directory. This might not be as automatic as you want, though, because you have to manually do the mounting as far as I've seen.

I'm not expert, though; do some reading and get back to us. :)

---

### Post by hyper_ch on 2008-11-05
I'd say you should have a look at truecrypt

---

