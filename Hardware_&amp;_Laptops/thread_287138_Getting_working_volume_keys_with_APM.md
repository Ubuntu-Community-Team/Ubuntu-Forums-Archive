---
title: "Getting working volume keys with APM"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by R3linquish3r on 2006-10-28
I am running Dapper on an old Dell Latitude C600. Because of issues with suspend not working with ACPI, I am using APM instead. Every "Fn" key works with APM except my volume keys.  I have done a fair amount of research on how to get this working. Most things I have read suggested a combo of Xbindkeys and Xmodmap, but my "Fn" key doesn't have a keycode in Xev's output so I can't use that. If anyone else knows of a way to get this working it would be much appreciated :)

---

### Post by meng on 2006-10-28
My Fn key (on a Dell Inspiron) doesn't have a keycode in xev, either, but my volume keys do work. Furthermore, xev documents different codes for fn+volkey vs. volkey-alone. Perhaps yours does too?

---

### Post by R3linquish3r on 2006-10-28
I just tried holding down the Fn key along with the button for Volume Up (Page Up) and I didn't get any output in Xev.

---

### Post by meng on 2006-10-28
That's a shame, I thought since we both had Dells that your keyboard would be similar to mine. Guess not.

---

### Post by R3linquish3r on 2006-10-28
Inspiron is alot newer so I'm not surprised they are different. My uncle has one its real nice.

---

### Post by R3linquish3r on 2006-10-28
Anyone else have any ideas?

---

