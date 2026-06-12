---
title: "c655 wifi not working with 10.10"
date: 2010-11-21
forum: Hardware
---

### Post by deezy23 on 2010-11-21
Hey all, so I had this apparently all too common acpi/ubuntu issue that most noticeably impacted my wifi. Back in the 10.04 days (yesterday) I finally fixed it by finding the solution was to add the "acpi=off" option to the menu that appears when you press 'e' during the boot and change grub to include the line "acpi=ht". Suddenly, full internet access! At the end of the day I decided to do the upgrade to 10.10 and it did it's thing overnight. I woke up this morning and i had 10.10... without wifi. my "acpi=ht" change is still there, but everytime i try to add the "acpi=off" option it seems to magically disappear and I still dont have wifi capability. I recognize the fact that the new release has been out for a short period of time, and that this problem either may not have been encountered yet, i may be doing something completely idiotic, or there may not be a solution yet. However, any help would be greatly appreciated!

---

