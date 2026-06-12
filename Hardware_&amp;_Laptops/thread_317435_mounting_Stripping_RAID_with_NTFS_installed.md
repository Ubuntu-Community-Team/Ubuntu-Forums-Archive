---
title: "mounting Stripping RAID with NTFS installed?"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by Capslock118 on 2006-12-12
Ok, I have searched and searched but no threads I have found seem to relate to my particular issue.

I have a RAID with windows installed, I dont want to wipe the raid for ubuntu to see it.

Can I mount the RAID in Ubuntu Edgy WITHOUT losing the NTFS partition (windows boot)?

---

### Post by psusi on 2006-12-12
Depends on what kind of raid it is.  Is it a windows software raid? 

If it is one of those cheap on board fake hardware raid controllers, see [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by Capslock118 on 2006-12-12
I am a little concerned because the link you gave me dealt with partitioning the raid and installing the OS, I am not concerned with that...rather, allowing ubuntu to see my raid and mount my current ntfs partition

---

### Post by psusi on 2006-12-13
Then skip the parts about installing.  

In fact, you should probably just wait a few days for the rc13 fix to get uploaded to the repositories, and then just install the dmraid package.  This will give you access to the raid array.

---

### Post by Capslock118 on 2006-12-13
what is rc13?

I dont know, I read the whole link but it still does not seem like I can do this.

I have NVIDIA as a RAID controller... my MB is an MSI k8N Neo2 Platinum with an Nforce3 Chipset, i hear linux supports this but it doesnt seem that way.....thoughts?

---

### Post by psusi on 2006-12-15
The version that shipped with Edgy was release candidate 11, or rc11.  It was broken.  rc13 works again, and is in Feisty, and currently waiting to be backported to edgy.  Once it is, all you have to do is install it and you will be able to access the raid.  The rest of the howto is really for installing to the raid, not just accessing it from an installation on another disk.

---

