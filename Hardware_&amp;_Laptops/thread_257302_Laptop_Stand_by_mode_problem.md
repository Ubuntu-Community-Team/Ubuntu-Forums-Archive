---
title: "Laptop Stand by mode problem"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by Sims on 2006-09-14
HI,

I have Ubuntu 6.06 and my laptop goes every 4 minutes in Stand by mode. I put in Power Management all to off(never), but it won't work. I tryed in Grub apm=off acpi=off, but won't work(i tryed the same in suse10.1 and i't worked) What can i do to turn that Stand by off? 

Tnx.

Sims

---

### Post by xyz on 2006-09-15
What's the brand?
I think problems may vary accordingly.

I had a good friendly laugh reading your post because most people have problems going into or waking from standby and yours does it all the time!!
LOL

---

### Post by Sims on 2006-09-15
Hi,

:) The Laptop is quite old (PIII 733 SisChipset). The Idea is to turn off all the Power managing deamons or something that put my Laptop in Stand by mode.

:confused: 

Sims

---

### Post by xyz on 2006-09-15
Hi-
By "Standby", I'm assuming you mean "Suspend"?? 
If this is in fact the case, this here suspended mine without a hitch:
[http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222)

---

### Post by Sims on 2006-09-15
Hi,

I don't know how to call it "Suspend" or "Standby". I only know my Laptop goes to "standby" or "Suspend" mode in 4 minutes and it not mathers that i work(move Mouse) on my Laptop or not. After that when I move the Mouse it goes ON again. I will Turn all Off. I don't need "standby" or "suspend" mode. I just wan't that my Laptop runs ...

Sims

---

### Post by Sims on 2006-09-15
Hi,

I loooked with ps-A and found apmd service and kapmd. I killed apmd with "sudo kill -9 xxxx(apmd service number)" and the laptop stil goes in standby mode. I also tried to kill kapmd(i don't know what that is) but it won't work.

I even turned off all power options in BIOS. 

sims

---

### Post by xyz on 2006-09-16
Hello sims-
How about reporting a bug?
You could explain the situation there and see what they come up with.
Googling doesn't seem to help.
Let me know...

---

### Post by MrWrong on 2008-01-02
I'm going to try and resurrect this thread as a newbie here I'm running slax and have the exact same problem.

I've gotta Dell Inspiron 7500 laptop with a PIII 450 that likes to go into suspend after 4 minutes of inactivity.  As previously was said I've tried disabling it in the bios.  I tried increasing/decreasing the time in bios with no effect, it still only sleeps at about 4 min.

Any help would be appreciated.

---

