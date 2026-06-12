---
title: "Overheating Hard drive"
date: 2011-07-18
forum: Hardware
---

### Post by louisgonick on 2011-07-18
My laptop is about two years old. Some time ago I had problems with my processor overheating. I just put some compressed air through the air vents and now it gets warm (90F) but nowhere near the temp it used to get. Now I noticed my hard drive is starting to get pretty hot, When I am playing a game or editing video it gets super hot, maybe like 130F. It gets so hot that I cant touch it for more than like 5 seconds. Does anybody have any idea on how can I solve this?

---

### Post by Ginzell on 2011-07-26
Hello,
Did you ever solve this issue?  I have this problem also and I was reading about possible kernel causes.  
I'm still looking.. :)

---

### Post by louisgonick on 2011-07-26
> **Ginzell said:**
> Hello,
Did you ever solve this issue?  I have this problem also and I was reading about possible kernel causes.  
I'm still looking.. :)

I downloaded a windows program that tells me what are the readings of the temp. sensors in my machine. The temp when idle was 67C (152F) and when I'm using it it gets up to 96C(204.8F) I guess that this is pretty normal because different machines run at different temperatures. If its getting so hot that it starts melting itself then that is a reason to get worried, but apparently laptops are built to resist pretty high temperatures. In Ubuntu it must run a bit cooler because the os is less resource hungry.

Hope this helped

---

### Post by Ginzell on 2011-07-26
Thank you, I'm looking at some links about putting metal shims inside the laptop.  Maybe I'll go that route if it continues to be bad.

---

### Post by varunendra on 2011-08-06
Try **top** command to see if there's some process keeping the CPU unusually busy. Compiz has been reported by some users to be permanently using 3-8% of CPU on Natty even when the computer is idle.

Interestingly, I recently cleaned up an HP Pavilion dv4 2101TU in which the pre-installed Win7 made it so hot (while using firefox only) that windows itself used to almost come to a halt. While the same laptop, when booted into Ubuntu Studio 9.10 (I installed it as a dual boot the day lappy was bought), worked like a charm with all the compiz effects enabled and multiple tabs of firefox open. So I think there may be something wrong with the newer kernel as I've seen many posts now complaining about lower battery backup and overheating. However, in the laptop I mentioned, a compressed air cleaning solved the issue for Win7 also.

---

### Post by Ginzell on 2011-08-06
Hi Varun,
I tried blowing it out, but it didn't help.  I thought it might be a kernel thing too but I'm not sure.  It only gets hot when I'm doing several things at once.  I usually find it very hot when running VBox or if I'm downloading something that takes a while.  Or if I'm backing up/restoring something that's extensive. (ie iTunes, cloning)
I will try the top command and see if I can find anything going on. 

Thanks!

---

### Post by .... on 2011-08-07
96C?!! The max operating temp spec is 65C (70@most). I really hope you have a bad sensor (and/or a good backup of your data). Good luck with that...

---

### Post by Ravvij on 2011-09-26
> **louisgonick said:**
> My laptop is about two years old. Some time ago I had problems with my processor overheating. I just put some compressed air through the air vents and now it gets warm (90F) but nowhere near the temp it used to get. Now I noticed my hard drive is starting to get pretty hot, When I am playing a game or editing video it gets super hot, maybe like 130F. It gets so hot that I cant touch it for more than like 5 seconds. Does anybody have any idea on how can I solve this?

I have a similar problem using Ubuntu. When I first setup Linux on my pc it was great, but my HardDrive over heated a LOT.
How do I solve this problem?
I use programs like Photoshop, Blender, Maya, and several other programs that use a lot of processing and hard drive power.
Is there some programming I can use to tell Ubuntu to quit making my hard drive so d@#m hot?

---

### Post by louisgonick on 2011-09-26
I really appreciate all of the answers...

---

