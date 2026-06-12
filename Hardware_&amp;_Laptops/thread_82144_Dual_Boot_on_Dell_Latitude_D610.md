---
title: "Dual Boot on Dell Latitude D610"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by jumpingin on 2005-10-26
Hello --
I'm a real newbie, and I'd like to end up with both Linux and Win XP Pro on my Dell Latitude D610. Right now it's just got Windows. Do I need to partition the HD before the Ubuntu install? If so, any advice on doing that? Anything else I should know, or places to look, before I really jump in?
Thanks, from someone starting at zero.
Loren

---

### Post by camj on 2005-10-26
You will need to resize the existing partition (Which you can do with Breezy). 

When you install Ubuntu, it will install a boot loader so you can select which OS you want to boot into when you start your laptop..

Best way to learn is to get down and dirty

---

### Post by 996 on 2005-10-26
**Don't worry. Ubuntu will take care of it.**

I started at zero too. But used (in Windows) Partition Magic to resize my existing partitions so I had about 5 gig of free space. Then I inserted the Ubuntu install cd and installed Ubuntu on that free partition... Grub made a fine bootmenu so I now can choose at startup which OS I want to use. This happened "automagically'

---

### Post by jumpingin on 2005-10-28
Thanks, you two. System's up, and everything seems to be working smoothly. And you're right -- it was incredibly easy (once I got the computer to boot from the CD drive...)

---

