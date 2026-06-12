---
title: "Laptop desktop not displayed on Panasonic TV"
date: 2015-07-09
forum: Hardware
---

### Post by Trogladyte on 2015-07-09
Hello all.

I am running 14.04 on a PB Easynote MZ36 with ATI Mobility Radeon Xpress 200. I want a second display using a Panasonic TXL 37e5B TV. I am using a VGA cable.

WhenI switch on the lappy, the purplr Ubuntu loading screen appears, alongwith my wallpaper in some basic resolution. The mouse pointer functions and the password login appears. But when I log in the display goes blank.

Any thoughts on what is happening? The TVclearly can see the laptop, and likes the basic settings. Changing the resolution on the laptop does not appear to help.   
[h=1][/h]

---

### Post by Trogladyte on 2015-07-10
Sorted

```
sudo xrandr --auto
```

---

