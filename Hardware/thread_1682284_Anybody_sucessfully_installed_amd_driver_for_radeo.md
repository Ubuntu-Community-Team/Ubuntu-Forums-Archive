---
title: "Anybody sucessfully installed amd driver for radeon 6950? Any issues?"
date: 2011-02-05
forum: Hardware
---

### Post by jcer93705 on 2011-02-05
Hey guys I just got a sapphire AMD Radeon 6950 2gb. I had to suck it up and so I baught this instead of nvidia. Thats due to I went for a Amd processor and mobo that support dual crossfirex. Anyways anybody installed this bad boy with the current driver from ati which is 11.1 for linux?? I know ati linux support is just sucky after all most ati driver are very buggy. Thanks

---

### Post by skypuppy on 2011-04-05
I just installed one of these and now Ubuntu won't boot.  I booted in safe mode and it said the ati drivers that were "officially blessed" by Ubuntu are still running.  The mobo has a baby ati graphics chip on it already.
I don't know which setting to make on the mobo.  There are four options and the manual is extremely terse (to say the least) on the subject.  
Let me know how you make out.
My mobo is Asus M4A785T-M/CSM.

---

### Post by jcer93705 on 2011-04-05
> **skypuppy said:**
> I just installed one of these and now Ubuntu won't boot.  I booted in safe mode and it said the ati drivers that were "officially blessed" by Ubuntu are still running.  The mobo has a baby ati graphics chip on it already.
I don't know which setting to make on the mobo.  There are four options and the manual is extremely terse (to say the least) on the subject.  
Let me know how you make out.
My mobo is Asus M4A785T-M/CSM.

Same issue. What I did instead using additional drivers on
ubuntu 10.10. I installed the official driver from ati. They
have a new version that I haven't tried though. But yea just
make the ati driver executed and then cd to where it is located
then do a sudo ./atidriver.run should do it. I like this card
and since Amd bought Ati so we should see better quality from 
amd when it comes to driver. We all know these amd/ati graphic
kick ***. Driver is the issue. Anyways I have no issue but one
game that it wouldn't show in full screen, in fact it does but to big to see and that is alien arena.

---

### Post by jcer93705 on 2011-04-06
> **skypuppy said:**
> I just installed one of these and now Ubuntu won't boot.  I booted in safe mode and it said the ati drivers that were "officially blessed" by Ubuntu are still running.  The mobo has a baby ati graphics chip on it already.
I don't know which setting to make on the mobo.  There are four options and the manual is extremely terse (to say the least) on the subject.  
Let me know how you make out.
My mobo is Asus M4A785T-M/CSM.

Well I installed 11.3 and I selected generate distribution specific then you will soon see that it detected you're os mavrikk 10.10. Then after that I ran aticonfig --initial then did my first reboot. Easy what a piece of cake. Nexuiz run great!! I think it just got better. :D I love my amd radeon 6950 2gb vid card.

---

