---
title: "Samsung HM160HC + Load_Cycle_Count"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by 444 on 2008-02-16
So I got this drive recently, and I wanted to mention a few things I found out about it.

I am using laptop_mode (which isn't enabled by default). It does an "hdparm -B 255 /dev/sda" when I go on AC power. This worked fine on my old drive. When I installed this new one, however, my Load_Cycle_Count starting skyrocketing even when on AC (400 within a couple hours). Apparently this Samsung does not recognize the 255 value. Changing it to 254 caused the Load_Cycle_Count to go back to normal.

Another issue, running "smartctl -a" on it causes it to hang for about a minute :confused: . Running "smartctl -A" works fine.

Other than that, it's pretty nice. Quiet and fast.

---

