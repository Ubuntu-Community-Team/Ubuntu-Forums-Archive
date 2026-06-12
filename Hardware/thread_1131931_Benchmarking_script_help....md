---
title: "Benchmarking script help..."
date: 2009-04-21
forum: Hardware
---

### Post by lawentzel on 2009-04-21
So I had an idea for creating a simple benchmarking tool, and needed some help.  I am assuming that this can be done with a script of some sort.

The idea I have is simple.  You pass a number to the batch script, and it will do two things with this.  First, it checks the time.  Then runs two loops.  Counting from 1 to your number, 1 to your number times.  This way the counting is exponential.  Then it will compare the time first time with the second time to give you a benchmark.

Second, it will then create a temporary file.  Check the time.  Then again, same sort of loop, read the content of that file, then write something to that file.  Finally after the loops are done, check the time and show you the difference.

This simple benchmark should show you the processor speed and hard drive reading and writing.  While the numbers are essentially meaningless...  if you run this same script on multiple systems using the same start number, you will then be able to compare performance.

The reason I got thinking on this, is I have two laptops.  One is a Pentium III the other a Celeron.  The Celeron has a faster MHz speed, then the Pentium III.  However everything I am looking at suggests the Pentium III should be a faster unit.  Just wanting to check.

Thanks in advance.

---

### Post by lawentzel on 2009-04-22
Anyone?

---

