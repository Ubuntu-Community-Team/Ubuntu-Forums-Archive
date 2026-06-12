---
title: "32 bit processor list"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by er76 on 2007-04-29
Can anyone give some names of 32 bit processors that are currently in production?

I want to build a 32 bit machine, but when I went looking at some cpus, the description did not say if the cpus where 32 bit or 64 bit.

---

### Post by lcg on 2007-04-29
> **er76 said:**
> Can anyone give some names of 32 bit processors that are currently in production?

I want to build a 32 bit machine, but when I went looking at some cpus, the description did not say if the cpus where 32 bit or 64 bit.
Every CPU currently produced in the PC world can execute 32bit code, though some of them are also capable of running 64bit code.

HTH,
Lars

---

### Post by zgornel on 2007-04-30
> **lcg said:**
> Every CPU currently produced in the PC world can execute 32bit code, though some of them are also capable of running 64bit code.

HTH,
Lars

Ehem, no.

---

### Post by lcg on 2007-05-01
> **zgornel said:**
> Ehem, no.

Oh yes.

You are, of course, free to contradict me, but you might want to be more specific. That way, I'd know at least which part of my posting you disagree with. We could then even discuss it ...

Regards,
Lars

---

### Post by zgornel on 2007-05-01
The Emotion Engine of the PS2 (128 bit) or the IBM Z9 series (64 bit). From what I know there are no 32 bit instructions for these processors.

---

### Post by lcg on 2007-05-01
> **zgornel said:**
> The Emotion Engine of the PS2 (128 bit) or the IBM Z9 series (64 bit). From what I know there are no 32 bit instructions for these processors.

I agree. There are, of course, CPUs without a 32 bit instruction set. However, I'd like to repeat what I said, the important part highlighted this time: "Every CPU currently produced **in the PC world** can execute 32 bit code [...]".
And since the OP asked about building a system and about 32 and 64 bit CPUs, I think it's a valid assumption that this means x86 vs. x86_64. And again, every CPU capable of executing the x86_64 instructions will happily execute 32bit x86 code as well. Because that is how the AMD64 instructions were designed from the beginning, to be only an extension to the 32 bit instructions from the days of the i386.

Regards,
Lars

---

### Post by er76 on 2007-05-01
I have two amd64 machines, but the 64 bit version of ubuntu is buggy.  

Thats why I want to build a 32 bit machine to install the 32 bit version of ubuntu.  

I have tried edgy version of 64 bit ubuntu, but the nvidia drivers do not work. 

Also I cant upgrade from dapper to fawn on a 64 bit machine, too many problems.

---

### Post by nanotube on 2007-05-01
> **er76 said:**
> I have two amd64 machines, but the 64 bit version of ubuntu is buggy.  

Thats why I want to build a 32 bit machine to install the 32 bit version of ubuntu.  

I have tried edgy version of 64 bit ubuntu, but the nvidia drivers do not work. 

Also I cant upgrade from dapper to fawn on a 64 bit machine, too many problems.

like the previous poster mentioned, you can run 32bit ubuntu on an amd64 machine. you dont /have/ to install 64bit ubuntu on it, you can just install the good old regular i386 32bit ubuntu. :)

---

### Post by er76 on 2007-05-02
Oh, sorry, I thought it meant using an emulator.

Thanks :)

---

