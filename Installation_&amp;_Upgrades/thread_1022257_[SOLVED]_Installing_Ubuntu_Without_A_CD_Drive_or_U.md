---
title: "[SOLVED] Installing Ubuntu Without A CD Drive or USB Key"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by f37u5g0d on 2008-12-26
Is there a way to install ubuntu without using a CD or USB jump drive?  I got a new acer aspire 1 for christmas and I want to dual boot ubuntu with the windows xp it came with on the 120GB hard drive it has.  What are my options?  The laptop is oriented towards its internet connections.  Is there a way to install ubuntu over the network?  I have other windows and ubuntu machines on a wireless (or wired) network in my house.

Any ideas are welcome!

---

### Post by cariboo on 2008-12-26
Have a look [here]("https://help.ubuntu.com/community/Installation"), for the many different ways you can install Ubuntu.

Jim

---

### Post by f37u5g0d on 2008-12-26
I am using WUBI and it's installer!  Thank you!

---

### Post by f37u5g0d on 2008-12-27
I installed ubuntu using wubi but I thought that I would be able to make a dedicated partition not just a virtual hard drive file on my NTFS partition.  The guide from the post above says that this is possible.  How do I do it?

---

### Post by Biznarie on 2008-12-27
I suggest you read up on Wubi, look here [http://en.wikipedia.org/wiki/Wubi_(installer)](http://en.wikipedia.org/wiki/Wubi_(installer))

---

### Post by f37u5g0d on 2008-12-30
I threw out the whole wubi install after struggling with grub configs.  For some reason grub didn't see my hard drive!  When at the grub cli typing root (hd and then the tab key yeilded nothing.  Anyway I used unetbootin to boot from an 8.10 image I downloaded.  This method was by far the best I think for a netbook install.

---

