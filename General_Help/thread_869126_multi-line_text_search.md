---
title: "multi-line text search"
date: 2008-07-24
forum: General Help
---

### Post by drop669 on 2008-07-24
Hi.
I have a text file.
I would like to find all occurrences of A in text, but also one
condition should be met: some B should be present somewhere in 1-5
text lines after A occurred.
For example, I would like to find these patterns:

.... A ....
.. B ...

or

.... A ....
(3 some random text lines)
... B ...

But not this:
... A ...
(more than 5 text lines)
.. B ...

Can it be done by sed, awk or any other command-line tools?

---

### Post by bodhi.zazen on 2008-07-24
grep -A 5 | grep B

---

### Post by drop669 on 2008-07-24
> **bodhi.zazen said:**
> grep -A 5 | grep B

Is this some special grep?

cat file | grep -A 5
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.

---

### Post by bodhi.zazen on 2008-07-24
no, your syntax is off.

grep -A 5 A <file> | grep -B 5 B

-A is an option as is -B

This is confusing, so lets search <file> for <foo> and <bar>

```
grep -A 5 <foo> <file> | grep -B 5 <bar>
```no need to :

cat <file> | grep <foo>

just grep directly

```
grep <foo> <file>
```you can use the -n flag to number lines if you want.

grep -n <foo> <file>

Edit: I assumed from your brief post you were more familiar with grep, sorry, hope the clarification helps.

---

