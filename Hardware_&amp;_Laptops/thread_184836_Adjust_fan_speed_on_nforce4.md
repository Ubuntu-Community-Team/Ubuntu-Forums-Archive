---
title: "Adjust fan speed on nforce4"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by oled on 2006-05-30
Is it posible to adjust the cpu fan speed under different temperatures ?

Ex. 2 % under 30 degress, 10 % under 35 degress etc.

There was a util for it in windows, but I can't find anything for linux. I have frequecy scaling working. Both cores of my CPU runs at 1 ghz when doing nothing. 

My setup is AMD X2 3800, gigabyte nforce4sli mobo.

/Oled

---

### Post by jellyfisharepretty on 2006-06-12
[QUOTE=oled]Is it posible to adjust the cpu fan speed under different temperatures ?

Ex. 2 % under 30 degress, 10 % under 35 degress etc.

There was a util for it in windows, but I can't find anything for linux. I have frequecy scaling working. Both cores of my CPU runs at 1 ghz when doing nothing. 

My setup is AMD X2 3800, gigabyte nforce4sli mobo.

/Oled[/QUOTE]

I would like to know if anyone has found how to do this in linux as well.  Even a fixed setting independent of temperature would be great.

Oled: I have found that Ubuntu works well with AMD's Cool n' Quiet (if I am not mistaken).  See if you can activate it in your BIOS.  I prefer not to activate it because my CPU is overclocked.

Jellyfish

---

### Post by oled on 2006-06-13
Cool n' quiet is enabled. But my fan still runs at about 1200 rpms (you can still hear it). In windows I can use the util to turn it down to 500 rpm or turn it off, when the temperature is under 30 degress.

---

### Post by jellyfisharepretty on 2006-06-15
Actually you are right.  I just enabled cool and quiet.  The frequency scaling works perfectly --but the fan speed does *not* scale along with the frequency, it just always stays high. :confused: 

I am using Dapper now, but back when I was using Breezy I could have sworn my fan speed was slowing as well...

Jellyfish

---

