---
title: "Can't adjust brightness on UNR9.10"
date: 2009-10-30
forum: Hardware
---

### Post by blwizard on 2009-10-30
Hi guys my netbook is Samsung N110, I've just installed UNR9.10 today and happily found a lot of new exciting features. However, the only thing is that I can't adjust brightness either through shortcut key or through the power management window. I could do it without any problem in 9.04. So what should I do to be able to change brightness? Thanks!

---

### Post by coffeecat on 2009-10-30
Right-click on panel and select "Add to Panel". Now highlight the Brightness Applet and click on "Add". Hopefully, you'll be able to adjust the brightness with that. But if you can't adjust the brightness through power management, it may be a driver issue - or a lack of driver for the way Samsung does it. I don't know. The Fn key combinations for screen brightness work OK on my EeePC but every manufacturer does it differently.

If the brightness applet fails, leave it a couple of weeks and try googling around. You can be sure that someone somewhere is doing some hacking/coding for this at this very moment.

---

### Post by blwizard on 2009-10-31
Thanks for your reply, but that applet doesn't help, the bar is stuck at the maximum position I can't move it. Anyone else out there having the same problem? Brightness adjusting worked flawlessly in UNR9.04 for me with either the Fn combo keys or the power management options. Any workaournd?

---

### Post by blwizard on 2009-11-03
Bump, no one knows how to solve this problem?

---

### Post by V15 on 2009-11-05
Hi

I also had this problem with my samsung n110.

It was solved quite easily by upgrading the bios to the most recent version on the [samsung website](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05012600&prd_mdl_cd=NP-N110-KA02UK&prd_mdl_name=NP-N110&prd_ia_sub_class_cd=P) (go to "firmware")

The only problem you may face is that I'm not sure how to do this process from linux - I was ok, since I dual boot koala and win7...hopefully you do too, otherwise you might need to pop xp back on, or get someone much more knowledgeable than me in the ways of linux to help.

V

---

### Post by lamadude on 2009-11-17
I have the same problem, in spite of having flashed my BIOS to the most recent version 07D0 I can't change the brightness not with the keys and not with the applet. 

I've tried setting the BIOS brightness setting to either auto or manual but neither one of those works.

I suppose I could downgrade to Jaunty, but apparantly it IS working for some people in Karmic, so it has to be possible somehow.

---

### Post by blwizard on 2009-12-03
> **V15 said:**
> Hi

I also had this problem with my samsung n110.

It was solved quite easily by upgrading the bios to the most recent version on the [samsung website](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05012600&prd_mdl_cd=NP-N110-KA02UK&prd_mdl_name=NP-N110&prd_ia_sub_class_cd=P) (go to "firmware")

The only problem you may face is that I'm not sure how to do this process from linux - I was ok, since I dual boot koala and win7...hopefully you do too, otherwise you might need to pop xp back on, or get someone much more knowledgeable than me in the ways of linux to help.

V

Thank you so much dude for that information. But I currently only have ubuntu installed on my netbook, and I don't really use windows... It would also cause a lot of hassle if I try to get a spare partition to put windows on. 

This is actually not quite a problem because it doesn't really affect my work but it just would be nice to be able to change the brightness to save battery life. Having had a kernel update last week didn't really solve the problem. I think I might just try compiling the kernel myself sometime. Thanks again!

---

### Post by robinPain on 2009-12-25
> **V15 said:**
> Hi

I also had this problem with my samsung n110.

It was solved quite easily by upgrading the bios to the most recent version on the [samsung website](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=05012600&prd_mdl_cd=NP-N110-KA02UK&prd_mdl_name=NP-N110&prd_ia_sub_class_cd=P) (go to "firmware")


V

Thanks!  worked a treat - now the brightness function keys work (I have two extra partitions, one running UNR, the other running the desktop 9.10).

Before this I had to set the BIOS brigthness from AUTO to MANUAL and then set brightness to max in Windows, then re-power up in either Ubuntu and both would then remain at max brightness on battery power (I could not find the original post that explained this but I think it also said that the brightness could be forced to max in grub where the up/down keys worked).

Prior to that I had extensively googled for a fix in vain.

---

