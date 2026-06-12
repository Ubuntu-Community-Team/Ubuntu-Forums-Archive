---
title: "sound problems after 2.6.15-25-386 update"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by cthornhill on 2006-06-15
After doing the kernel update to 2.6.15-25-386 on my Toshiba laptop sound in several third party apps failed with the 'device in use' error. Specifically I could not get sound in VMWare sessions of XP, or in RealPlayer10. Presumably other apps had issues too, but VMWare was a killer for me, so I had to find a fix.

After a Google search I noticed the suggestion on a similar sounding error that I turn the ESD sound mixer off and try VMWare. I did , and it is back to working for now. RealPlayer works too. Of course this is the only system out of 4 others with this error. I also want the darn default sound mixer back. Things were fine in 2.6.15-23-386, so as far as I can tell this is a bug and should be fixed.

Personally I consider this regression and a good reason to be unsure about loading new kernel fixes no matter why they are sent out. Is this stuff getting tested? This is the sort of thing that makes me think BSD...

OK, I know I am being harsh, but I don't expect security updates to break the system. I own lots of MS systems, and I don't need more software that gets patched with broken patches! Take some more time and get it right!

Cecil

---

### Post by mscman on 2006-06-15
As far as I know, a kernel upgrade has not been a part of a security update since Dapper was released...  If it has been upgraded, I haven't recieved it yet (and I just ran a manual dist-upgrade).  I'm not sure where you received this upgrade from, but you may want to check your sources.list file.

---

### Post by Martian on 2006-06-15
I believe this is the kernel upgrade...

[http://www.ubuntuforums.org/showthread.php?t=197181](http://www.ubuntuforums.org/showthread.php?t=197181)

---

### Post by mscman on 2006-06-15
I take back what I said.  After doing a manual update && upgrade, I found that the kernel was upgraded.  Didn't mean to be critical, I was just confused!  :---) 

I am a little hesitant about performing the upgrade myself, as I am using a Toshiba laptop as well and would like to avoid breaking it (my desktop is for breakage, laptop is for important stuff...)

I'm not really sure what advice to give, since I don't know of any specific areas to start looking... if I experience any similar issues, I'll make sure to post back here.

---

### Post by cthornhill on 2006-06-15
No problem - I was surprised by the update as well. My wife gave me good talking to about loading a new kernel just because it was out (she is an ops person - I am a developer - draw your own conclusions...).

I understand the desire to fix stuff, but really...Now it is true that 3 of my 4 systems here at home did not have issues. Like you my laptop is for client day work, and I can't really do without it. On the other hand, the problem was not too bad to solve once I got a hint.

My post was more to warn others and tell them a possible fix than anything else. I found this work around on Google not on the forums. That was a little worrysome to me.

Iin general I would love to have a better error message too. the message that comes up is not too useful. Plus I do think a log of all changes to the system is needed in the update manager, as well as a rollback feature.

Yes I know I can set all that up. Still, I think it is time to see those sort of features as a baseline part of the OS in Ubuntu. I also feel there needs to be a central config manager tool available to organizations deploying Ubuntu. If this is going to be a LTS and Enterprise level tool it is time for all those features. Most of the code is available - it just needs to be put together and documented.

As for this bug/problem. If you plan on updating I could suggest you do an image back up and then at worst you can restore to that point.

Cecil

---

