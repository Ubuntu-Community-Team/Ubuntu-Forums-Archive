---
title: "Dell Studio 15 - Sleep not working"
date: 2009-11-21
forum: Hardware
---

### Post by Abadon125 on 2009-11-21
I have a (relatively) new Dell Studio 15 (1555 more specifically).
I recently did a clean install of Ubuntu 9.10 x64 on my laptop next to a Windows partition and I have been trying out all the different features.  

One of the things that I have noticed is that I can shut down and start up super fast, Hibernate works but is very slow, and Sleep just doesnt work at all.  The computer will enter sleep mode almost instantly.  It then will not come out of sleep at all.  It simply turns on and sits there indefinitely with a black screen.

Does anyone know the cause of this or things to try to fix it?  Thanks!

---

### Post by AndThenWhat on 2009-12-29
Same problem. I have a Dell Studio 15 also. I think the issue is a kernel problem and hopefully will be fixed in the next kernel.

---

### Post by conorsulli on 2010-01-02
Interesting, I own a studio 17, and I am not suffering from this. What graphics card do you own? Mine is  intel gm965

try- lspci -in your terminal if your not sure.

---

### Post by apurbapaul0 on 2010-01-11
I have dell studio 1555 with windows 7 and ubuntu 9.10 installed side by side. I have the same problem and I have tried code lspci -in it gives Segmentation fault. 
any suggestion.

---

### Post by conorsulli on 2010-01-12
> **apurbapaul0 said:**
> I have dell studio 1555 with windows 7 and ubuntu 9.10 installed side by side. I have the same problem and I have tried code lspci -in it gives Segmentation fault. 
any suggestion.

Try

 lspci | grep VGA

sorry about my last post because I meant try lspci  "in your terminal" ... the grep VGA will filter your card type from the rest of your text from the lspci command

---

