---
title: "Do I have 64bit compatible hardware?"
date: 2009-09-02
forum: Hardware
---

### Post by GroogFish on 2009-09-02
How can I figure this out? I did a google search and I found a bunch of solutions for windows users but I can't find this in Ubuntu's sysinfo. How do I figure this out?

---

### Post by Rhubarb on 2009-09-02
What CPU have you got in there?
How old is your computer?

Is it a core2duo / i7 / Opteron / Athlon64?

Running this may help us work out what CPU you've got, so we can work out if it's 32 or 64bit:

```
cat /proc/cpuinfo
```

---

### Post by running_rabbit07 on 2009-09-02
If you are running Windows you can use [CPUID]("http://www.cpuid.com/cpuz.php").

---

### Post by GroogFish on 2009-09-02
I've got a Pentium 4 _Integrated_ Processor. So the computer recognizes it as 2 processors. So it's a Pentium 4 but that might make a difference.

---

### Post by gordintoronto on 2009-09-02
> **GroogFish said:**
> I've got a Pentium 4 _Integrated_ Processor. So the computer recognizes it as 2 processors. So it's a Pentium 4 but that might make a difference.

Please, run

cat /proc/cpuinfo

and tell us what it says on the line which begins "Model name".  That way, it is possible to answer your question.

---

### Post by theozzlives on 2009-09-02
An easy way is to throw in a 64 bit CD and try to install, it'll tell you if it don't work.

---

### Post by GroogFish on 2009-09-03
> **gordintoronto said:**
> Please, run

cat /proc/cpuinfo

and tell us what it says on the line which begins "Model name".  That way, it is possible to answer your question.

model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz

---

### Post by howefield on 2009-09-03
> **GroogFish said:**
> model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz

That is a 32 bit cpu.

..if it is this one [http://ark.intel.com/Product.aspx?id=27497](http://ark.intel.com/Product.aspx?id=27497)

---

### Post by Rhubarb on 2009-09-03
> **GroogFish said:**
> model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz

I'd make an educated guess that it'd be a 32bit only CPU.
I'd assume the 2 processors that your operating system sees is actually just the 1 CPU core with hyperthreading.

There's no harm in trying out a 64bit Ubuntu live CD too see if it works - if you can spare the download.

---

### Post by howefield on 2009-09-03
> **Rhubarb said:**
> There's no harm in trying out a 54bit Ubuntu live CD too see if it works - if you can spare the download.

Don't think it will be the downloading that would be the problem, maybe the finding... ;)

---

### Post by GroogFish on 2009-09-03
Why, is the 64bit live cd hard to find?

---

### Post by howefield on 2009-09-03
> **GroogFish said:**
> Why, is the 64bit live cd hard to find?

nope, but the 54 bit is...

twas a joke, hence the smiley.

---

### Post by Yellow Pasque on 2009-09-03
```
cat /proc/cpuinfo | grep lm
```
If this returns nothing, you won't be running 64-bit ;)
Note: lm = long mode.

---

