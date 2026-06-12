---
title: "SMART says my hard drive is dying, why did I have to check this manually?"
date: 2016-05-28
forum: Hardware
---

### Post by darxus2 on 2016-05-28
This hard drive has been flaky (randomly failing fsck, losing files).  

"sudo smartctl -a /dev/sdc" says, among other things:


SMART overall-health self-assessment test result: PASSED

Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   199   193   051    Pre-fail  Always       -       329426
  3 Spin_Up_Time            0x0027   156   141   021    Pre-fail  Always       -       9191
  5 Reallocated_Sector_Ct   0x0033   157   157   140    Pre-fail  Always       -       344


The man page says:

'Each Attribute also has a Threshold value (whose range is 0 to 255) which is printed under the heading "THRESH".   If  the Normalized value is less than or equal to the Threshold value, then the Attribute is said to have failed.  If the Attribute is a pre-failure Attribute, then **disk failure is imminent**.'

And it's way over all three of those pre-fail thresholds.  

How should I have noticed this?  Is the lack of notification a bug, or did I miss something?

---

### Post by darxus2 on 2016-05-28
Looks like I mis-read the man page, specifically the part that says "If  the Normalized value is **less than** or equal to the Threshold value".

---

### Post by weatherman2 on 2016-05-29
If the RAW value of "Reallocated_Sector_Ct" truly is 344, then you've got a catastrophic problem or are about to have one.  That means 344 sectors on the surface failed and were replaced with spares by the drive firmware.  Once you run out of spares, the drive will be unable to replace new failed sectors and you will experience data loss, etc.

A few reallocated sectors is usually OK unless the number begins increasing regularly.  344 seems very bad to me.

What's the value of "Current Pending Sector Count" ?  That's another one to watch.  it should be zero; if not, then some sectors also can't be read already.

I would run the extended S.M.A.R.T. test immediately - use GSmartControl to do it with the Gui or figure out the options to smartctl to do it on the command line.

---

