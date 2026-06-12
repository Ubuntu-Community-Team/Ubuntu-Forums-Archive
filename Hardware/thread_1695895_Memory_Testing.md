---
title: "Memory Testing"
date: 2011-02-26
forum: Hardware
---

### Post by Infernoyance on 2011-02-26
Hello linux users, I was wondering if there were any gurus out there that had any suggestions for stress testing memory on a linux server environment.

We already have memtest86+, mprime, and memtester running, but still no avail to finding any problems for faulty memory.

Here are some of parts we are trying to test to see if they are stable enough on the servers.

4GB PC10600 1333MHz ECC REG Hynix
8GB PC10600 1333MHz ECC REG Hynix 
16GB PC10600 1333MHz ECC REG Hynix 

I would really appreciate if anyone could refer me to a program preferable that runs on the terminal/CLI.

:) Thanks!

---

### Post by ajgreeny on 2011-02-26
I'm not sure I follow your question.

What is wrong with Memtest86+?   If left overnight to run it should find any problems in any of your memory sticks, but it does need a long run-time, not just an hour or two.

Sorry if I've misunderstood, but give us more info and you may get a better answer from somebody else.

---

### Post by Infernoyance on 2011-02-27
Yes we have been already using memtest86+ and it works great, but the problem is that it runs in assembly, which is below the operating system. What I specifically need is a program that runs on top of the Linux OS that stresses memory, not just a general stress testing program for server use. Hopefully this clears things up.

The memory that is being used will be exclusively used for Linux machines only, so I need something that will test the memory inside a Linux execution environment.

Memtest86+ hasn't been catching our bad memory modules lately, and  that is why I have been looking for Linux program that can stress test memory.

---

