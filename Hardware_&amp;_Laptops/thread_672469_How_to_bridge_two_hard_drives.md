---
title: "How to bridge two hard drives?"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by Kubotaz4 on 2008-01-19
I have two seperate hard drives, one with XP and the other with 6.06, both are internal.  I would like to run some type of VM software that allows me to use the XP hard drive while still in 6.06, without having to dual-boot to get my information off of the XP hard drive. Is this possible? and how?  Thanks.

---

### Post by Yellow Pasque on 2008-01-19
Why do you need a virtual environment to "get information" off of the drive. Can you not just mount it as a normal filesystem? You'll need the ntfs-3g package if you want to read/write to an NTFS drive, but I think you should be able to mount it read-only with Dapper.

---

### Post by smartboyathome on 2008-01-19
the NTFS-3G package is included with Gutsy, so that shouldn't be a problem.

---

### Post by Yellow Pasque on 2008-01-19
> **smartboyathome said:**
> the NTFS-3G package is included with Gutsy, so that shouldn't be a problem.
S/he said the OS in use is Dapper (6.06)

---

### Post by Kubotaz4 on 2008-01-20
Let me clarify my question.  I want to be able to access the information off of the hard drive that has XP on it while im in my 6.06 environment.  Exp: Dapper is main OS, and I open a window that allows me to view/use my XP hard drive and use the Windows XP aps in that window.  I hope I made that clear.  Just accessing the information is good, but being able to run my applications from Windows while still in Dapper would be optimal.

---

