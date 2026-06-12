---
title: "Disabling dell bios fan control, and making i8k work"
date: 2021-10-05
forum: Hardware
---

### Post by validust on 2021-10-05
When I thought that I had found a way to make i8k work on my Dell Latitude E7470, I posted here how I had done it. The reason for that was that in some of the many posts I had read, there was the puzzled observation that it seemed as if the native fan control overrode i8k. 
Not long after I had submitted the post... the native fan control overrode i8k. 
Somewhere I had come across a caveat, that the more recent Dell machines did just that. Don´t know that Latitude E7470 is recent. Anyway, I found a way to disable the Dell bios fan control:
Write as a boot option "bios-control.disable=1" - No quotation marks. I used Grub Customizer to edit the menu entry/boot sequence.

---

