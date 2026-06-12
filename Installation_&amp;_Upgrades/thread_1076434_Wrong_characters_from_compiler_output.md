---
title: "Wrong characters from compiler output"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by BillRebey on 2009-02-21
I couldn't find a forum that seemed like the right fit for this question, please correct me if this post should be elsewhere...

I have two Ubuntu boxes that I'm compiling on (with g++ via SSH from a WinNT/Cygwin box).  

The compiler output produces garbled characters instead of punctuation.  For  instance:

   invalid conversion from â€˜void* (*)()â€™ to â€˜void*â€™

(The actual garbled characters appear different in my xterm and in my editor than they do above on this Web page, but their position is the same).

Anyone have any idea what's going on here?

---

### Post by BillRebey on 2009-09-15
In case it helps anyone else, I've found the solution to this problem.  Unset the LANG environment variable and the characters will come out correctly.  In csh:

unsetenv LANG

---

### Post by in4tunio on 2010-05-26
> **BillRebey said:**
> In case it helps anyone else, I've found the solution to this problem.  Unset the LANG environment variable and the characters will come out correctly.  In csh:

unsetenv LANG

Thanks, this worked for me. On bash, I did 'export LANG=""'.

---

