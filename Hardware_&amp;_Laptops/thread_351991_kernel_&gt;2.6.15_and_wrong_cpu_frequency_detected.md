---
title: "kernel &gt;2.6.15 and wrong cpu frequency detected"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by flapane on 2007-02-02
why does kernel newer than 2.6.15 detects my overclocked x2 3800+@2.56ghz as a 1800mhz cpu?

---

### Post by flapane on 2007-02-14
up

---

### Post by mikewhatever on 2007-02-14
Most probably, the CPU frequency is just scaled down to save power and reduce heat output. Both Intel and AMD do it these days. Run some heavy programs, even a DVD movie or something of the sort and check it the frequency changes.
Check this too for more info [http://ubuntuforums.org/showthread.php?t=346255](http://ubuntuforums.org/showthread.php?t=346255)

---

### Post by flapane on 2007-02-16
frequenct scaling works well, but scales from 1800 to 1000, that means that it uses the default FSB value (200mhz), while it detects the correct fsb (285mhz) with 2.6.15 and older ones

---

### Post by flapane on 2007-02-21
up

---

### Post by flapane on 2007-04-03
up

---

