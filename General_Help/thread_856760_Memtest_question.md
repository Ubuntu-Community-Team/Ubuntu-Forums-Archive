---
title: "Memtest question"
date: 2008-07-11
forum: General Help
---

### Post by jerome1232 on 2008-07-11
When you run memtest, do you just let it run for a few hours or does it actually stop and say everything is borked/ok eventually?

---

### Post by mc4man on 2008-07-11
It will run to completion, I don't remember how many passes the default mode is (1 ?), the time will depend on # of passes and how much memory is being tested. You can reconfigure the tests, ect. by entering c on the keyboard.
figure about 15 mins. per pass for 512mb of memory

---

### Post by mc4man on 2008-07-11
@jerome1232
sorry i was wrong - been a couple of years since I used it. Memtest will continue to run, normally let it complete 1 full pass of all tests. After that pass it will start a 2nd pass, then a third ect. 1 pass is usually good unless you see errors reported, in that case maybe a 2nd pass is advised.
Note: in the past I've seen where memtest can sometimes report an a small # of errors but the memory is good.

[http://www.memtest86.com/tech.html](http://www.memtest86.com/tech.html)   for reading

---

### Post by jerome1232 on 2008-07-11
Yeah kinda figured when I noticed it said pass 2, thanks for the info and link. Starting to get weird lock ups and my ram is about 4 -5  years old so I just felt the need to check it. (seems to be only under Ubuntu so must be a package I installed)

---

