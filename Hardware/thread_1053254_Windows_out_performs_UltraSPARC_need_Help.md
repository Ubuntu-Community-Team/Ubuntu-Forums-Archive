---
title: "Windows out performs UltraSPARC need Help"
date: 2009-01-28
forum: Hardware
---

### Post by colmac@gmail.com on 2009-01-28
We just installed ruby on a
Sun T1000, 6 core UltraSPARC T1 cpu, 4G memory , Solaris 10

Right now Windows is out performing an Ultra SPARC by 25 seconds! Does
anyone know why this would be the case. I have downloaded ruby and
compiled it on the hardware, i have tried the binaries from sunfreeware
and the results are the same. Actually, the results from my compile were
a second or two worse than the binaries from SUN!


This is the program ran for the bench mark. I called it t.rb

require 'benchmark'

array = (1..1000000).map { rand }

Benchmark.bmbm do |x|
x.report("sort!") { array.dup.sort! } #this sorts the array.
x.report("sort") { array.dup.sort } #this makes a copy of the
array and sorts it.
end


###########################################

Solaris v10
# ruby t.rb
Rehearsal -----------------------------------------
sort! 29.450000 0.020000 29.470000 ( 29.458899)
sort 29.760000 0.010000 29.770000 ( 29.772163)
------------------------------- total: 59.240000 sec

user system total real
sort! 29.060000 0.010000 29.070000 ( 29.064410)
sort 29.070000 0.000000 29.070000 ( 29.076217)
#

Windows

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\cmackenzie>ruby t.rb
Rehearsal -----------------------------------------
sort! 4.735000 0.000000 4.735000 ( 4.813000)
sort 4.359000 0.000000 4.359000 ( 4.390000)
-------------------------------- total: 9.094000 sec
user system total real
sort! 4.313000 0.000000 4.313000 ( 4.375000)
sort 4.297000 0.015000 4.312000 ( 4.422000)

C:\Documents and Settings\cmackenzie>

Ubuntu Linux

colmac@sideshowbob: ruby t.rb
Rehearsal -----------------------------------------
sort! 3.310000 0.010000 3.320000 ( 3.317860)
sort 3.250000 0.020000 3.270000 ( 3.270037)
-------------------------------- total: 6.5890000 sec

user system total real
sort! 3.280000 0.030000 3.10000 ( 3.318575)
sort 3.250000 0.020000 3.270000 ( 3.269284)
colmac@sideshowbob:
Edit/Delete Message

---

### Post by cariboo on 2009-01-28
Unless you are running all three OSs on the same computer, your results don't mean a thing. If you are running Windows and Ubuntu in a vm, it looks like you have a misconfiguration of some sort.

Jim

---

### Post by electrogeist on 2009-01-28
Yeah I'd love to know how you are running XP on an UltraSparc!

Anyhow it looks lke Ubuntu was the winner... was that running on the UltraSparc?

---

### Post by colmac@gmail.com on 2009-01-29
the hardware is a T1000 UltraSPARC, 
Ubuntu is E4500@2.2GHz
Dell laptop D630
anyway I already know the problem. It is the RISC technology is just too old.

---

### Post by colmac@gmail.com on 2009-01-29
read the post: Sun T1000, 6 core UltraSPARC T1 cpu, 4G memory , Solaris 10

---

### Post by cariboo on 2009-01-29
Your comparisons don't work, because you are using 3 different computers, a better test would be to run windows and Linux in a vm on the untrasparc computer and then run the tests again.

Jim

---

### Post by colmac@gmail.com on 2009-01-29
> **cariboo907 said:**
> Your comparisons don't work, because you are using 3 different computers, a better test would be to run windows and Linux in a vm on the untrasparc computer and then run the tests again.

Jim
dude i dont care about the other boxes. the question was WHY is it running so poor on the sun box. The answer is RISC is dead technology. anyway it gives me cannon fodder to get Linux in house on blade box of some kind

---

