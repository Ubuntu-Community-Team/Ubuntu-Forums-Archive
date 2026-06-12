---
title: "boots into grub even though CD is selected"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by dowbjts on 2007-01-27
I have a Dell L400 laptop with XP/ubuntu dual boot using grub.  

Originally, it had 6.06 running fine with XP.  I'm trying to do a clean install of 6.10. 

So...I downloaded the .iso (desktop i386) checked the hash5 (it is fine) and burned a 6.10 CD.

I hooked up the external CD and hit F12 to boot off the CD...but, no luck...the grub screen off the hard drive comes up.  I can't seem to get the 6.10 CD to boot.

I booted into XP and can see the CD just fine with the iso file in place...so I know the hardware is OK.

I hit F2 and looked at the bios settings, they look ok.  I even changed the boot sequence so the CD-ROM is first...before the internal drive.  Still no luck.

Any ideas on what to look at next?

---

### Post by xmastree on 2007-01-27
> **dowbjts said:**
> I booted into XP and can see the CD just fine with the iso file in place...so I know the hardware is OK.So, you can see the ISO on the CD?
That's your problem, you didn't burn it as an image.

See this:
[http://www.xmastree.34sp.com/ubuntu/burn](http://www.xmastree.34sp.com/ubuntu/burn)

---

### Post by dowbjts on 2007-01-27
I figured it was something stupid like that!  
Thanks for the prompt response!

---

