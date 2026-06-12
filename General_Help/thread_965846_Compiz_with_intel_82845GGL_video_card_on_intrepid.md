---
title: "Compiz with intel 82845G/GL video card on intrepid"
date: 2008-10-31
forum: General Help
---

### Post by glennric on 2008-10-31
Does anyone know of a workaround to get compiz working with the intel driver?  I know there were several bugs filed about this during Intrepid's development, but the workarounds were to uninstall compiz.  Not a real workaround in my opinion.  I should mention that compiz did work on this computer in Hardy and before.  

I think it is really sad that this hasn't been fixed, particularly now that Intrepid has been released.

---

### Post by sea_monkey987 on 2008-11-08
+1.  bump. 

also, what changed that caused this chipset (correct term?) to break?

---

### Post by pluckypigeon on 2008-11-20
+2

bump!!!!!

:(:(:(

---

### Post by alwayshere on 2008-11-20
i think its just a in with the new and who cares about the old thing.

---

### Post by pluckypigeon on 2008-11-20
> **alwayshere said:**
> i think its just a in with the new and who cares about the old thing.

I completely agree.

Hardware we've been using for a couple of years is all of a sudden "buggy"

---

### Post by everettattebury on 2009-03-05
This fixed it for me, and I have compiz working again on my 82845G/GL:

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/comments/8](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/comments/8)

All of the bug reports in launchpad about this problem seem to blame it on the intel driver.  I think it is really caused by changes in the structure of the xorg configuration files.

---

### Post by glennric on 2009-03-18
This works.  Thanks everettattebury.

---

### Post by pluckypigeon on 2009-03-24
Has this been fixed in the new Kernel 2.6.29.29?

---

### Post by everettattebury on 2009-03-24
I don't think it's a kernel problem or a driver problem.  It's a problem with settings necessary for running compiz being lost during the upgrade from Hardy Heron to Intrepid Ibex, due to a change in the way x settings are stored.

I have no experience with a fresh install of Intrepid, I think there are other issues affecting this video card that complicate that.

---

### Post by glennric on 2009-03-29
I don't think this is an issue of settings not being saved, but an issue of settings not being properly detected by the xserver.  This issue happens on any installation intrepid, whether it is a fresh install or an upgrade from hardy.

---

### Post by Astinsan on 2009-04-07
This may not work with some of the reversions of the chipset. There has been reports of problems on some dell hardware using the chip. I can not find the actual post that referred to it though. I believe it was reversion 1 locks up and rev 0 doesn't. Just in case someone reads this post to try and fix it with no success.

---

### Post by everettattebury on 2009-05-25
The previous fix I linked to didn't work for me after installing Jaunty, but I found that the fix listed here works:

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

### Post by inaninck on 2009-10-25
> **everettattebury said:**
> This fixed it for me, and I have compiz working again on my 82845G/GL:

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/comments/8](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/comments/8)

All of the bug reports in launchpad about this problem seem to blame it on the intel driver.  I think it is really caused by changes in the structure of the xorg configuration files.


THANK you!!!!!!
What I wonder, how did you find this solution?

---

### Post by pluckypigeon on 2009-10-25
none of this stuff works for me, it don't matter anymore.

For a couple of years Linux and my intel845g have been incompatible. 

If it does ever work properly, it's going to be too old to be any good anyway.

I've been using Arch Linux with the intel legacy (2.3) driver which is the best thing for me, it doesn't seem as fast as it did with feisty or gutsy though.

---

