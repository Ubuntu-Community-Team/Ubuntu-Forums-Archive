---
title: "Is there a way to make Hardy Hibernate?"
date: 2008-07-15
forum: General Help
---

### Post by rolandixor on 2008-07-15
Can't seem to find the answer?

---

### Post by Hooya on 2008-07-15
Works on my laptop with no extra work (run /etc/acpi/hibernate.sh) but it never works on my desktop...  No idea why.

There aren't many answers to this question around either... seems to be everyone that has a problem never gets it fixed.

Edit:  actually, just tried that script on my desktop and it worked just fine.  Maybe an update fixed it at some point.

Sleep (suspend) still doesn't work though.

In a terminal:
```
sudo sh /etc/acpi/hibernate.sh
```

---

### Post by bodhi.zazen on 2008-07-15
Hardy hibernates just fine for me too.

Perhaps if you described your problem a little better it might be easier to offer you advice.

One thought, you know you need a large swap to hibernate ?

Typically we advise swap = RAM X2, max 1 Gb

But to hibernate you need swap at least = RAM

So if you have 2 Gb RAM you need a 2 Gb swap ...

Then turn your computer on, it appears to "boot", select the same kernel you hibernated from ... allow it to boot ... you will get a log in menu ... enter password, viola

---

### Post by rolandixor on 2008-07-15
it tells me I don't have enough memory to hibernate, but I have about 4 GBs of swap, and 1GB of RAM.

is that a problem?

---

### Post by bodhi.zazen on 2008-07-15
What is the output of :

```
free
```

---

### Post by Erlander on 2008-07-16
To get hibernate to work on my 2 pc's I had to alter the Power management setting in bios.

Rob

---

### Post by rolandixor on 2008-07-16
I found a solution.
I'll post the link to the topic soon enough.
got some updates to apply :)

can I have cookie for my hard work?

---

### Post by scholzilla on 2008-07-16
check our majorix hack on this post:

[http://ubuntuforums.org/showthread.php?p=3151492#post3151492]("http://ubuntuforums.org/showthread.php?p=3151492#post3151492")

it worked like a charm for me on both feisty and hardy (32bit).

m

---

