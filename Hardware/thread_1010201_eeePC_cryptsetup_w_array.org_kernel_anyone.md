---
title: "eeePC: cryptsetup w/ array.org kernel anyone ?"
date: 2008-12-13
forum: Hardware
---

### Post by aurelieng on 2008-12-13
Hi all,

I'm trying to set up an encrypted home partition on a eeePC 1000H, using Adam's kernel from array.org. I didn't manage to create a LUKS filesystem, and I am not even able to decrypt a LUKS partition I have on my USB key. It stops with the following error message :

```

root@localhost:~# cryptsetup luksOpen /dev/sdb3 key
Enter LUKS passphrase:
Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/sdb3 contains at least 514 sectors.

```

It seems that there is no LUKS support in this kernel. Shouldn't it be added ASAP, since these machines are very likely to get lost ? :-)

Cheers,

Aurélien.

---

### Post by aurelieng on 2008-12-15
OK, I just had to load the dm-crypt module before running cryptsetup.

---

