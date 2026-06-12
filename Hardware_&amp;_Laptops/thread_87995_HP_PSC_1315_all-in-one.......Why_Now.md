---
title: "HP PSC 1315 all-in-one.......Why Now ?"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by sarah_b on 2005-11-09
I have set this printer up in several Linux distros, including ubuntu 5.04 & 5.10, and I have never had any problems. Now I have a problem and can not figure out why.

The scanner still works fine but it does not send anything to the printer anymore. 
hplip & xsane are installed, the dll.config file is correct. I have tried removing the printer, turned the printer off and then on again, add another, and when I set it up as a 1310, which I have always done in the past, everything looks fine, nothing different than when it has worked before, but it is unable to send anything to the printer. 

I have not added or downloaded anything to my system either.
Can someone help me please with what could be causing this to happen.

All suggestions, comments and opinions are welcome,
sarah

---

### Post by Kyral on 2005-11-09
Hmm......might be a bug somewhere...

I'll have to check it out for myself (I have the same model ;P)

---

### Post by sarah_b on 2005-11-18
Problem solved.....

I removed and reinstalled hpijs, now the printer and scanner work perfect !

---

### Post by duckboy on 2006-02-17
I have this printer too and I just installed Ubuntu 5.10 on my computer so I am hoping that everything will go smooth :)

---

### Post by suziequzie on 2006-02-19
Well, I couldn't get the scanner to work until I read this topic. I had installed the HP driver, not the hpijs. After reading here, I removed it and used the hpijs and *boom*, kooka recognized my scanner. And it scans beautifully.

[QUOTE=duckboy]I have this printer too and I just installed Ubuntu 5.10 on my computer so I am hoping that everything will go smooth :)[/QUOTE]

---

### Post by Zeroangel on 2006-02-19
Hmm, I have had the same problem with the PSC 1315 (spent a few hours tinkering, reinstalling, etc). This is definitely a bug worth fixing.

---

### Post by duckboy on 2006-02-19
My 1315 automatically installed itself which is cool. I will check and see if the scanner works sometime soon. Just don't feel like doing it right now :)

---

### Post by jason.b.c on 2006-02-20
my 1315 all in one worked perfectly,  blew my freek'n mind at how simple it was to get it working !!!:) :D

---

### Post by pneaveill on 2006-09-13
> **jason.b.c said:**
> my 1315 all in one worked perfectly,  blew my freek'n mind at how simple it was to get it working !!!:) :D

  Is this thread still active? If so, I have a 1315 also and with the tweaks it scans and prints, but does not do the OCR (Optical Character Recognition) at all. I have tried reloading xsane and gocr, but I am stumped.

---

