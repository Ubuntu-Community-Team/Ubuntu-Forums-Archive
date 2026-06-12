---
title: "ERROR Linux NEWB in need of help.  CAN'T UPDATE or Install anything!!!"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by dyingscience on 2007-05-29
When I try to update I get the following error:

E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E:_cashe>open()Failed. Please Report.

What do I do someone help me.

---

### Post by dyingscience on 2007-05-29
When I try to use Terminal to run Dpkg --Configure -a

I get this:

dpkg: requested operation requires superuser privilege

---

### Post by jerrylamos on 2007-05-29
Ubuntu doesn't use "root" or superuser.  When doing administration type tasks, precede the command with "sudo"  which is short for "psuedo root administration".  Try this:

sudo dpkg --configure -a
it will ask you for your regular password

I haven't done that command, but sudo prefix is used in lots of places.  Suggest you try "The Official Ubuntu Book" from your bookseller or Amazon.

Cheers, Jerry

---

### Post by dyingscience on 2007-05-30
I had found that solution previous to your response. But I do however appreciate that someone would offer their advice. Once again, Thank you.

---

