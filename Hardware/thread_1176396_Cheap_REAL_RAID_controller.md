---
title: "Cheap *REAL* RAID controller?"
date: 2009-06-02
forum: Hardware
---

### Post by wiz561 on 2009-06-02
Hi!

I was wondering if somebody could recommend a reasonably priced REAL SATA RAID0 controller that will work with ubuntu out of the box.  It seems like there are a lot of controllers out there that say they do real hardware raid but don't.  I was hoping to spend somewhere around 100 bucks.


Thanks!

---

### Post by paulisdead on 2009-06-02
Honestly, unless I've got the budget for a 3ware or Areca RAID card, I just use Linux software RAID.  I don't much care for LSI or Adaptec, and like you said a lot of the lower end raid cards are really just sofware RAId.  This is the software RAID built into most distros, not the onboard motherboard RAID.

One huge benefit to Linux software RAID, is if your motherboard/disk controller dies, you can pop the drives out, and slap them into another Linux system, and the array is recognized.  If that happens with hardware RAID, you have to get another identical or similar controller just to get back your data.  Yes you should have backups, but it can save you a lot of time if you can just bring the array back up in another system.

I could go into the reasons why you shouldn't do RAID0, but I won't.  Just please search around for the reasons why not, if you plan on keeping any data you can't afford to lose on those drives.  It's definitely worth it to get 1 more drive and make it a RAID5.

---

