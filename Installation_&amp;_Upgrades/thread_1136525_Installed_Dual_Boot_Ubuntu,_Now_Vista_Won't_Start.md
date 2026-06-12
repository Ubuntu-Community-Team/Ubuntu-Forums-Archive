---
title: "Installed Dual Boot Ubuntu, Now Vista Won't Start"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by LibertyRebellion on 2009-04-25
Hello,

Complete newb to the Ubuntu community from Windows world. Anyways, I installed Ubuntu on my PC with XP in a dual boot format. Everything works great.

I installed it on my laptop with Vista, Ubuntu works, but Vista won't start up and I go directly to the Startup Repair when trying to load Vista.

Can anyone assist in guiding me through how to get Vista to work w/o having to use my recovery disk. I don't mind using recovery, but it's just a giant pain in the ****!


Thanks in advance!
LR

---

### Post by hashan17 on 2009-04-25
Hey you can install vista DVD and boot from it. Then try repairing the bootloader (There's an option in the DVD)

It worked for me...

---

### Post by LibertyRebellion on 2009-04-25
> **hashan17 said:**
> Hey you can install vista DVD and boot from it. Then try repairing the bootloader (There's an option in the DVD)

It worked for me...



Awesome, thanks for the suggestion! I will give it a whirl!

---

### Post by LibertyRebellion on 2009-04-25
Okay, well I popped in my recovery CD and it's from Toshiba. It's going to restore my PC to factory defaults.

Is there some other way around this? I really don't want to lose the pics of me and my gf, software, and settings.

I'm computer and CLI savvy, if anyone can point me in the right direction I would much appreciate it!

---

### Post by LibertyRebellion on 2009-04-26
anyone have any other suggestions?

---

### Post by Mark Phelps on 2009-04-27
> **LibertyRebellion said:**
> Okay, well I popped in my recovery CD and it's from Toshiba. It's going to restore my PC to factory defaults.

Is there some other way around this? I really don't want to lose the pics of me and my gf, software, and settings.

I'm computer and CLI savvy, if anyone can point me in the right direction I would much appreciate it!

Well ... that's exactly what recovery CDs are supposed to do.

You can download (via torrent) a Vista repair CD from the NeoSoft forums, burn that to a CD, and boot from that to do Startup Repair.  

Other than that, you will need to borrow a Vista DVD from someone else -- they all have the same repair options so it doesn't matter which version it is.

---

### Post by LibertyRebellion on 2009-04-28
Thanks for the suggestions all. I ended up fixing it by changing the entry in menu.lst from hd(0,1) to hd(0,0)

---

### Post by jamesrico on 2009-04-28
Where did you find the menu list? hd 0,1 hd 0,0.? I have a Vista machine, that I installed a dual boot with 9.04 When windows start I cannot logon I get a message that says lost ini file? Any  ideas.

Thanks in advance
James

---

