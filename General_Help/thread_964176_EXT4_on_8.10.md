---
title: "EXT4 on 8.10?"
date: 2008-10-30
forum: General Help
---

### Post by Djinndrache on 2008-10-30
Hi,

does Ubuntu 8.10 support EXT4 filesystem?

---

### Post by Gannon8 on 2008-10-30
Not that I have heard of, because Ext4 is still under development. You can probably compile the driver though.

---

### Post by Djinndrache on 2008-10-31
Thanks :)

---

### Post by vwvr9 on 2008-12-30
If you bump up the kernel to 2_6_28 it should work.

[http://kernelnewbies.org/Linux_2_6_28](http://kernelnewbies.org/Linux_2_6_28)

---

### Post by hyper_ch on 2008-12-30
8.10 uses the .27 kernel... I don't think that it will be updated to .28 in 8.10

---

### Post by cariboo on 2008-12-30
The latest kerenel in Jaunty is 2.6.28-4, but I wouldn't advise installing the alpha2 as it is really broken, the latest version of Xorg doesn't support the restricted drivers. If you convert to ext4, you will also need to use grub2 as grub doesn't support ext4. I would suggest waiting until Jaunty RC comes out.

Jim

---

