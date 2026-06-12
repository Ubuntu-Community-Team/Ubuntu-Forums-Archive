---
title: "Tough Question"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by Jason_howard on 2007-07-18
My Friend has 80gb hard drive with about 15 gb used up for pic videos ect  he tried gparted to  put Ubuntu on it but it would not let him, what could be wrong

---

### Post by ubanchaos on 2007-07-18
first what ru running on and ru dual booting

---

### Post by jimrz on 2007-07-18
> **Jason_howard said:**
> My Friend has 80gb hard drive with about 15 gb used up for pic videos ect  he tried gparted to  put Ubuntu on it but it would not let him, what could be wrong

if the drive is a single partition or other wise has not enough unallocated space, he will need to use gparted or partition magic or whatever to first shink an existing partition in order to make room for the ubuntu install. a word of caution, BEFORE attempting to shrink the current partition be sure to defrag it at least 2 or 3 times AND backup any critcal data.

---

