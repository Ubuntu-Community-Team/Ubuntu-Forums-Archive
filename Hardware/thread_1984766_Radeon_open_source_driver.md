---
title: "Radeon open source driver"
date: 2012-05-22
forum: Hardware
---

### Post by tedius on 2012-05-22
Since at least Ubuntu 11.04, and probably a few version before, I've always used the open source radeon driver for my ATI Radeon HD 3450 graphics card, with no problem.  

But after updating to Ubuntu 12.04 I would just get a screen with kernel boot messages.  After some investigation I found that it was because lightdm failed to start and this inturn faild due to xorg.  Xorg was complaining about fglrx not being installed which is correct and by installing this I can now start Xorg and use my desktop.  But why wont the open source radeon dirver work when I has done so for the last 2 release at least.

Any help would be apreciated.

---

### Post by Redblade20XX on 2012-05-22
I believe that since you upgraded your distribution some configuration files probably carried over and is probably clashing with another program. Remember each distribution change has several program changes. You can try and back trace the problem but for efficiency sake your better off fresh installing.

-Red

---

