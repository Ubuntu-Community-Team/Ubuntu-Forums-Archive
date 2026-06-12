---
title: "Help interpreting SmartCTL results. Did I buy a bum drive?"
date: 2012-08-01
forum: Hardware
---

### Post by buddhaflow on 2012-08-01
Hi, I bought a 'no brand' hard drive off eBay sold as new never used. It's a 10K RPM 150GB.

I have been experiencing a rash of random segfaults and other bad behavior on my new ubuntu 12.04 box (C2D, 4GB, HP dc7800, etc.)

I ran smartctl on it to test it. The results can be seen here:

[http://pastebin.com/RgkjpQEw](http://pastebin.com/RgkjpQEw)

2 things stuck out at me.

1) ID#9, the disk total life. It should be around 60 hours. It reports at 16755 hours. I tried changing it to report this number as minutes and seconds (with -v9,minutes option), but neither gave correct results (279hours and 4 hours respectively, neither of which is correct.) What is going on? Has the disk really been used for years? Is there any other explanation? Do you think the disk was indeed 'new never used' as marketed, or have I been had?

2) The line "ATA Error Count: 50638" certainly gives me pause. Is there any reasonable explanation for that? 50,000 kind of seems like a lot of errors, almost as many as I have made in my whole life!

Basically, should I return it to the eBayer as a defective/misrepresented part, or is there some innocent explanation and maybe the drive is still sound?

Trying to decide whether I should install again on this disk or just throw in the towel and wait weeks for a new hard drive to come before finally getting to enjoy my shiny new (to me) computer. Thank you for reading!

---

### Post by ahallubuntu on 2012-08-01
Sure looks like a used drive to me.  In fact, there are a lot of errors reported.  For example, the Reallocated Event Count is 383 (should be 0) - that means there were 383 attempts to replace failed sectors.  487 are shown as Reallocated Sectors (replaced).

Send it back if you can.  Attach a copy of that report if the seller has any question!  You should win that dispute easily.

---

