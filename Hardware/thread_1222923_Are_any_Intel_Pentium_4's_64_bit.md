---
title: "Are any Intel Pentium 4's 64 bit?"
date: 2009-07-25
forum: Hardware
---

### Post by raymondvillain on 2009-07-25
Is there a feature in Ubuntu Jaunty that will ferret out the details of the processor?

Running Jaunty (32 bit) live CD, want to install Ubuntu Server 9.04.

System Monitor (system tab) says there are 2 processors, Pentium 4, each 2.40 GHz.

How do I find out if this system will handle the 64 bit Server version of Ubuntu?

---

### Post by mayagrafix on 2009-07-25
Figure out exactly what model of Pentium u have - in windows an application such as CPUID will give u this info - then go to intel page and see if said Pentium is 64-bit enabled. If so, you can address 4 gigs and up of RAM with a 64-bit ready OS. You're next question should be: Is Ubuntu 9 "Jaunty" 64-bit ready?

For instance I have a Dell 530 with a Pentium Conroe-L E2160 running Windows Vista 32 bit. After upgrading the RAM to 4 gigs and the OS to Windows Seven 64 bit version, I will be able to use all of the RAM. When I  boot to Jaunty, only 3.2 gigs show up. 

Hope this answers ur question :P

---

### Post by raymondvillain on 2009-07-25
Well, I do not know the answer.  But I did find out that my processor is NOT capable of running a 64 bit O. S.

I used a boot CD, UBCD4WIN, and went to "My Computer">properties>advanced>environment variables>PROCESSOR_ARCHITECTURE which states mine is an X86.

So I'll have to run the 32 bit version of Ubuntu server.

Thanks, folks.

Going to mark this SOLVED.

---

### Post by snargfish on 2009-07-25
Some Pentium IV's are 64 bit capable. But to be honest, your better off with 32 bit anyway.

---

