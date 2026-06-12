---
title: "Hibernation questions"
date: 2009-06-09
forum: Hardware
---

### Post by ianmillington on 2009-06-09
Hi

Kubuntu 9.04 on dell inspiron 630m. 2 points please:

When resuming from hibernate, after the bios should the machine then go through to the grub screen, or should it simply wake up? It seems to come back to life properly, but I would assume the latter, whereas I get the former.

Also, when hibernating I get the following error message appearing on multiple occasions (possibly 50 times)

<number> "mmc0: controller never released inhibit bits"
<number> "mmc0: 0x2 reset never completed"
<number> "mmc0: 0X4 reset never completed"

This repeats on multiple occasions signifying numerous failed attempts and then it seems to give up. I believe mmc0 is all to do with the sd card reader that is on the machine. 

Can anyone tell me what is going on here and how it is fixed. To be honest this has been happening with kubuntu since I first installed dapper in 2006 and so if I can get a fix for it I'll be really pleased.

Thanks

Ian

---

### Post by go2dell on 2009-06-10
Your machine is resuming from hibernation exactly as it should.  When resuming it will begin a normal boot process until a hibernation image is found, then it will restore the hibernation image rather than proceeding with a full boot.

No idea about the error messages.  Do they appear when you suspend, or only when you hibernate?  I've found that on my laptop everything breaks if I suspend while logged in, but simply logging out and suspending from the KDM screen works fine.

---

### Post by ianmillington on 2009-06-10
Thanks for that.

Suspend is a complete mess. If I try to suspend from within kde then it "seems" to work, seemingly coming back OK. However, if I then try to shut down from that point then it's a screen load of error messages then freezing - I've given up on that. However, I'll try it from the login screen and see what that does.

Ian

---

