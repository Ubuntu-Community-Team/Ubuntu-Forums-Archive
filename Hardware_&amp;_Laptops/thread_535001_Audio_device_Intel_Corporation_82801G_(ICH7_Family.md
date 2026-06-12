---
title: "Audio device: Intel Corporation 82801G (ICH7 Family) not working!"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by PeterWalgreens on 2007-08-25
This post briefly covers it, but gives no help for total linux noobs like me.

[http://ubuntuforums.org/showthread.php?t=461794](http://ubuntuforums.org/showthread.php?t=461794)


Help! Please!

---

### Post by Chii on 2007-09-25
I had the same problem with that device, and what it required in order for me to get it to work was a modified DSDT file.  

If you want to test this out, try booting your linux install with the line acpi=off.  The guide for this is at [http://www.transcendent.us/jay/?page_id=46](http://www.transcendent.us/jay/?page_id=46) . If booting with acpi off does work for you it could possibly mean that you have a blacklisted bios.  So as a result you will need to find a modified DSDT file and apply it to your bios, and from that point on sound should work.

Hope this helps!

---

### Post by AnimateDeath on 2007-09-26
Go here:  [http://ubuntuforums.org/showthread.php?t=559695](http://ubuntuforums.org/showthread.php?t=559695)   This is what I did to get mine working, and it works everytime. :)

---

