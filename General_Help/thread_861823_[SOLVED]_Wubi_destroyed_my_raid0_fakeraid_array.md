---
title: "[SOLVED] Wubi destroyed my raid0 fakeraid array"
date: 2008-07-16
forum: General Help
---

### Post by dotted on 2008-07-16
So i wanted to install Ubuntu on my main computer, but it currently doesnt have any optical drive plugged in, nor did i have a usb pen available.

So i had only 1 option, which was to install Ubuntu using Wubi. My windows vista (x64) install is currently living on a RAID 0 array using a Intel ICH9R raid controller (fakeraid if im not toally off course). But due to limited space available i installed Ubuntu on another drive ehich is not part of any raid array.

Now, when Ubuntu was done installing, and rebooted the second time. The ICH9R Raid Bios said the Raid array failed and is now unbootable. Now why would Wubi/Ubuntu need to change anything related to my raid array at all? And why didnt Wubi warn me that fakeraid is a no go?

And also is there some way to recover the raid array?

Best regards
Dotted

PS. It seems my first cup of ubuntu, is gonna be my last :(

---

### Post by arufa on 2008-07-17
I had a similar situation last night, i'm running a Windows XP and I use ICH9R with RAID 0. After I boot into ubuntu installed by wubi, the Intel Matrix Raid BIOS says my first RAID 0 drive becomes "Non-RAID disk", and the raid cluster becomes "Fail". I found out that if I turn off the power (instead of restart). The RAID cluster becomes "Normal" again...

---

### Post by ago on 2008-07-17
As mentioned in several places (website, faq, guide), fake raid arrays are not supported, this is not a Wubi issue but Ubuntu's. They will be supported in 8.10

> **dotted said:**
> But due to limited space available i installed Ubuntu on another drive which is not part of any raid array. 
That is OK

> Now, when Ubuntu was done installing, and rebooted the second time. The ICH9R Raid Bios said the Raid array failed and is now unbootable. Now why would Wubi/Ubuntu need to change anything related to my raid array at all?
If you installed on a separate disk it doesn't mount the other partitions in write mode, the only write operations happen during the windows-side installation (boot.ini, registry, wubildr...) and are controlled by windows. 

> And also is there some way to recover the raid array?
I do not see how, but in the worse case the raid is out of sync, and each raid should have tools to bring it in sync again. The tools are probably specific to the raid though.

---

### Post by dotted on 2008-07-17
> **arufa said:**
> I had a similar situation last night, i'm running a Windows XP and I use ICH9R with RAID 0. After I boot into ubuntu installed by wubi, the Intel Matrix Raid BIOS says my first RAID 0 drive becomes "Non-RAID disk", and the raid cluster becomes "Fail". I found out that if I turn off the power (instead of restart). The RAID cluster becomes "Normal" again...
Whoa i never expected that :O

Thanks, it worked. Now i just got a missing BOOTMGR error, but atleast thats recoverable.

EDIT: What do you know,just  another reboot and now it is up and running like before, but with Ubuntu.

---

### Post by ArmoredCavalry on 2010-01-05
> **dotted said:**
> Whoa i never expected that :O

Thanks, it worked. Now i just got a missing BOOTMGR error, but atleast thats recoverable.

EDIT: What do you know,just  another reboot and now it is up and running like before, but with Ubuntu.

Ah, this is now my official favorite thread.

I actually had this happen before, and accidentally fixed it.

This thread made me remember what I had to do! :KS

---

