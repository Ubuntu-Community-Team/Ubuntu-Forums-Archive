---
title: "Standby and Hibernate Working....Almost"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by wsmoser2004 on 2006-02-23
I have an HP laptop...and I am very impressed by the fact that Standby and Hibernate work pretty well right out of the box.  Hibernate (I guess it's technically called "suspend to disk") works flawlessly, but the laptop has a little bit of trouble coming back from Standby (suspend to RAM?).  As soon as it comes back, the little battery monitor shows that I have 0% battery charge remaining, and when I go into System Settings (this is KDE) to change settings for "Laptop Battery" it says that my system only has a partial ACPI installation.  

It seems like ACPI is not restarting when I come back from Standby mode (that's just a guess on my part).  Is there anything I can add to the resume.sh script that will restart ACPI (if this is in fact the problem)?  Or, any other ideas?  I do use standby frequently when carrying the laptop around, so fixing it would be great.  Thanks.

---

### Post by drfelip on 2006-03-30
I got the same message:

Your computer seems to have a partial ACPI installation. ACPI was probably enabled, but some of the sub-options were not - you need to enable at least 'AC Adaptor' and 'Control Method Battery' and then rebuild your kernel.

My problem is I can't shut down my laptop, after everything is stopped it hangs.

I'm very scared about playing with kernel, I just succeeded once (under Libranet, that had a very nice frontend so you just changed the option you needed and recompiled). Does anybody solved that message thru kernel rebuilding, or is it some kind of bug?

---

### Post by wsmoser2004 on 2006-04-04
Yes, that is exactly the error I get and that is the same problem I have when I go to shut down.  I've pretty much resigned myself to the fact that I probably won't get standby working, at least in Breezy (maybe I will in Dapper).  Unfortunately this means that when I need standby, I just use XP.  #-o  

I don't think rebuilding the kernel will help in this case (I could be wrong about that however).  I think in order to fix this we would need a newer kernel.

---

### Post by drfelip on 2006-04-06
I noticed the error message is just under 2.6.12-10-386 kernel, not under 2.6.12.9-386 one (I get both options from GRUB menu), but the behavior is exactly the same: after everything is off, a "Power down" message on the screen and computer locking.

---

### Post by Mr Fat Bat on 2006-05-10
I'm getting the same thing.... it's not a real hassle but it would be great to be able to use the advanced power features!

The weird this is that I had it working previously and then for some reason it stopped working.  I was using gnome at the time and did not know about this "partial acpi" thing until I started tinkering around in KDE.  

Any help would be appreciated!

---

### Post by b-artje on 2006-05-15
I also got this problem with ubuntu dapper drake. Just to let u know!

---

### Post by albox on 2006-05-23
up !
Is there somebody having more information now ?

---

