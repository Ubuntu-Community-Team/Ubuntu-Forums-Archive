---
title: "kernal panic on install ... never happened before"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by mkyb14 on 2005-10-17
Ok after pulling some hardware and then not getting it to boot up because of a kernal panic the first time i thought it best to reinstall with the hardware completly in it now.

Hence the new problem.  when using the regular 5.10 cd (which i have 3 downloaded versions) and try to install i get a kernal panic when it's trying to load the inital kernal for the install screen.  

"[4294671.018000] <0>kernal panic- not syncing: Attempting to kill init!"
"[4294671.019000]

never had this problem before but this even happens when i use knoppix live cd.  

no one in the irc channel could help or had an idea of why this is happening.  if anyone could lend some advice that would be great seeing as my business's website is down till this is resolved!

thanks again.

---

### Post by ewz on 2005-10-17
I Had this problem with knoppix, do you get the boot screen?
I found that if I put mem=XXXM (xxx is the amount of ram you have)
it worked I think its got somthing to do with the motherboard not giving the right ram count. Dont give your full ram though take about 10 meg off
hope this helps
:D

---

