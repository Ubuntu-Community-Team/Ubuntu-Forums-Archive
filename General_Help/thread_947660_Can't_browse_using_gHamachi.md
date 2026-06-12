---
title: "Can't browse using gHamachi"
date: 2008-10-14
forum: General Help
---

### Post by rbradt on 2008-10-14
I've recently started using Xubuntu, and I'm trying to put gHamachi on it to do some file sharing between my other systems.

I managed to be able to ping the other systems on the Hamachi server; however, I can't browse my other Ubuntu systems from my Xubuntu laptop.

I've been reading around, and I guess Xubuntu has very different networking capabilities or something like that.  Does anyone have any suggestions on how to fix this problem?

Thanks for the help
-rb

---

### Post by felker2 on 2008-10-14
Have you set up SMB / Samba sharing? And have you shared a directory via SMB? On the same LAN, without hamachi, can you see the share(s)?

---

### Post by rbradt on 2008-10-14
I'm actually in the process of doing just that which I haven't done before.  Any special tips or suggestions?

---

### Post by rbradt on 2008-10-14
I just set up a SMB file share using pyNeighborhood, and I was able to view the shared folders.  Also, I mounted the same shared folders using the gHamachi IP address, and I was able to view those as well.

Does that mean there's something wrong with gHamachi or maybe it's not fully compatible with Xubuntu?

-rb

---

### Post by felker2 on 2008-10-15
There could be something wrong with SMB-shares/-broadcasts over gHamachi, but I think you should try a bit further and analyze what does and what doesn't work: Can you connect if know the name (\\system\share), can you connect if you know the IP address (\\1.2.3.4\share), etc.

BTW: You can use Nautilus to browse SMB-shares: Places -> Network.

---

