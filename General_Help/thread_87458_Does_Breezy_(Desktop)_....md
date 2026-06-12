---
title: "Does Breezy (Desktop) ..."
date: 2005-11-08
forum: General Help
---

### Post by Frasir on 2005-11-08
Hi,

Does Breezy (Desktop) support dual processor?

I realise that the SysMon does not show that there are two processors.

Do I need the Ubuntu-Server version?

Thanks!!!

---

### Post by 23meg on 2005-11-08
You should use an SMP kernel with dual processors. What processors do you have?

---

### Post by Pablo_Escobar on 2005-11-08
Yes it supports dual processors. You need to download via Synaptic or apt-get SMP version of kernel Your using.
Post back what kind of processor You're using and what (32 or 64 bit ) OS :)

---

### Post by codejunkie on 2005-11-08
[quote=Frasir]Hi,

Does Breezy (Desktop) support dual processor?

I realise that the SysMon does not show that there are two processors.

Do I need the Ubuntu-Server version?

Thanks!!![/quote] yes but to enable dual core, or multiple cpu support you need to install the smp kernel for your processor type. for example if your had dual pentium4 processors you would install the linux-686-smp package this will install the kernel and restricted modules for that kernel for amd systems use linux-k7-smp hope this helps.

---

### Post by Frasir on 2005-11-08
Wow, you guys or gals are fast. My ditching of Windows was a right choice.

I use a dual Intel P3 800MHz, 32bit. So ... which smp package should I download?

Thanks very much!

---

### Post by Pablo_Escobar on 2005-11-08
Then You should get the latest 686 SMP kernel available in the repos.

---

### Post by 23meg on 2005-11-08
You're welcome. You should prefer linux-686-smp.

---

### Post by Frasir on 2005-11-08
Thanks to all and specifically Pablo_Escobar & 23meg.

Let me work on it when I get home and revert.

PS. I'm enjoying every bit of the Ubuntu experience, too.:p

---

### Post by Frasir on 2005-11-08
Dear all,

I've download and installed. It works now!

:KS :KS :KS :KS

---

### Post by jatos on 2005-11-08
Also users with HT may notice a performance boost with SMP.

---

