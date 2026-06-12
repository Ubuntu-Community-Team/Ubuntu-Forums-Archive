---
title: "lenovo 3000 N200, ubuntu 9.04 cooling problems"
date: 2009-05-04
forum: Hardware
---

### Post by monkman on 2009-05-04
hi, after instralling ubuntu 9.04, i observed my notebook getting very hot, because the cooling is not running. the parallel vista is no problem, the cooling runs. in ubuntu it stands still.

some data about the notebook

lenovo 3000 N200 0769 BGG

any hints?

thx!

---

### Post by monkman on 2009-05-08
anybody?

---

### Post by mikene on 2009-07-22
Same as in Lenovo 3000 V200 with Ubuntu 9.04.
Output of acpi -c:

     Battery 0: Charging, 82%, 00:12:58 until charged
     Cooling 0: LCD 0 of 9
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 3

Does anybody have an idea ?

---

### Post by monkman on 2009-07-23
i went for suse on my notebook... runs fine... even the issues with low video perfomance are solved now...

---

### Post by mikene on 2009-07-24
But I love Ubuntu :(

---

### Post by monkman on 2009-07-24
me too ;)

try 64bit<->32bit, maybe it makes a difference...

---

### Post by Cayal on 2009-07-24
My 3000 N200 (0769 ALU) on 9.04 also has some cooling issues, but the fans seem to run fine. I do notice that placing it on a hard wood surface (or soft surface, of course) will make it overheat, and using it in the sun also makes it run a bit hot, although I don't boot into Vista enough to know if this is a problem with the laptop or Ubuntu specifically. My acpi -c:
     Battery 0: Unknown, 100%
     Cooling 0: LCD 0 of 7
     Cooling 1: Processor 0 of 7

---

### Post by monkman on 2009-07-30
i tried again, but nothing new. notebook shutdown because of overheating. at first cooling runs, later on it stops...

i wonder which notebook runs fully on linux? i remember dell selling some with ubuntu preinstalled...

---

### Post by monkman on 2009-10-23
9.10RC 32bit. running fine for hours now, finally :)

---

