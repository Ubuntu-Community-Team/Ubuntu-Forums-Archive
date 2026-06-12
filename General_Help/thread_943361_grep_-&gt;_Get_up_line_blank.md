---
title: "grep -&gt; Get up line blank"
date: 2008-10-10
forum: General Help
---

### Post by gaiterin on 2008-10-10
Hi!

If I have this file test.txt:
test1
test2

test3
test4
test5

test6
test7


If like get with grep this:
grep test3 test.txt

test3
test4
test5

Can I do it?
Thanks very much!

---

### Post by geirha on 2008-10-10
For that specific case, you can do ```
grep -A3 -B1 test3 test.txt
```
which will show the line test3 with one line before it (-B1) and three lines after it (-A3).

---

### Post by gaiterin on 2008-10-10
Thanks, but I like a block between blank lines :O If I'm searching "test1" get:
test1
test2

---

### Post by geirha on 2008-10-10
In that case I think awk would be a better tool. The following should write all the lines from a line matching test3 to the first line containing nothing:
```
awk /test3/,/^$/ test.txt
```

---

### Post by gaiterin on 2008-10-10
Great help!!! :D Thanks very much!

---

### Post by gaiterin on 2008-10-16
Hi! One question more, please :$
Can I get the complete block?

Example: If I have this file test.txt:
test1
test2

test3
test4
test5

test6
test7

If I'm searching est3 or st4 or test5..., get the complete block:
test3
test4
test5

Thanks very very much! :)

---

