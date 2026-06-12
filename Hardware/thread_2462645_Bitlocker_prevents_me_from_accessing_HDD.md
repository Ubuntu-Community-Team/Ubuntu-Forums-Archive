---
title: "Bitlocker prevents me from accessing HDD"
date: 2021-05-24
forum: Hardware
---

### Post by willis02 on 2021-05-24
I am having a dual boot on my system. On my HDD I have a partition  for win10 and one for Ubuntu 20.04.2. This works fine so far. Beside I  have a HD to store data.

I can open the HD in win10, but not in linux. Tells me that the file system of the HD is bitlocker2 and win10 says that it is NTFS (bitlocker encrypted). 

The problem is that I never activated bitlocker in Windows or Ubuntu. It is also not possible to disable it, because it was never activated.

I simply don't need to use bitlocker and would be happy to get rid of that trouble.

How can I access my HD when using Linux? What will I have to do? And is win10 or ubuntu? 

Thank you for your attention!

---

### Post by TheFu on 2021-05-24
This is a Microsoft issue, not linux.  Ubuntu doesn't use bitlocker without lots of effort. The native encryption for Linux is called dm-crypt/LUKS. No way would any Linux install encrypt NTFS without extraordinary manual effort by you.

I vaguely recall there was a way to have read-only access to bitlocker files, provided you know the passphrase and install the correct packages into Ubuntu.

---

