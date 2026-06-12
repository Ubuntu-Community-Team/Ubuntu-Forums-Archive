---
title: "[SOLVED] Conky execbar"
date: 2008-10-11
forum: General Help
---

### Post by Metaleks on 2008-10-11
I seem to be having trouble with the execbar variable in conky.

I have a simple python script for testing:
```
#!/usr/bin/python
print  50
```

And in my .conkyrc, I want to use this. Here is the relevant bit:
```
TEXT
Test: ${exec python test.py}% ${execbar python test.py}
```

This shows 50% and then a **full** white bar. Correct me if I'm wrong (and I know I have to be), but doesn't the conky manual say that execbar takes a value between 0 and 100 and outputs a bar representation? So shouldn't this display a bar that is **half** full? If not, what do I need to do to make it display properly?

---

### Post by Metaleks on 2008-10-17
Bump!

---

### Post by Metaleks on 2008-10-19
Solved!

It turns out that only numbers from 0 to 1 will give you the correct graphical representation. So, 0.50 would be 50%. Makes sense. So, it looks like the conky documentation is not only misleading, but just very wrong in general!

---

### Post by loomsen on 2008-10-19
I agree, it's not the best documentation... But, tbh, anything else for a percentage wouldn't be possible... Or how'd you think would conky draw 200 if you specified it?

Anyway, you're right, the doc page is not the best. This thread with like 500 pages or so is better :D

---

### Post by giovannif on 2012-10-13
I know this is an old post, but I am having some problems with the command execbar. I am actually trying a very simple instruction:

${execbar echo 0.5}

Why does it show me an empty bar?

PS. I am using ubuntu 10.04

Thanks
Giovanni

---

### Post by oldos2er on 2012-10-13
Please start a new thread: 

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

