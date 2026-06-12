---
title: "how much battery does your laptop consumes in suspend??"
date: 2008-05-18
forum: Hardware
---

### Post by cespinal on 2008-05-18
I just realized the batery consumption in suspend is actually quite low!. I left my pc in suspend and forgot to plug it for about 20 hours... when I came back the battery was on 70%... with that performance I would not even bother to use hibernate unless I have to carry the pc on its bag... 

comments??

---

### Post by sdennie on 2008-05-18
Those numbers seem fairly normal.  The only real reason I can see for using hibernate is if you are low on battery power and have no way to charge or if you are on battery and want to swap to a new battery.

I'm not sure what you mean by "with that performance I would not even bother to use hibernate unless I have to carry the pc on its bag...".  Are you referring to the fact that laptops get very hot in bags if they aren't turned off?  If so, suspend shouldn't have that problem as it only keeps a very minimal amount of the system powered up (specifically the RAM) and so generates essentially no heat.

---

### Post by cespinal on 2008-05-18
I though the did build up heat on suspend :$ :$ 

thanks!!

---

### Post by Wharf Rat on 2008-05-18
I am happy to you get such great life from your battery.  How do you do it?

On Suspend I may get 6 hours.  I tried Hibernate last week. About 10 hours later the battery was at 1%.

---

### Post by jocko on 2008-05-19
> **Wharf Rat said:**
> I am happy to you get such great life from your battery.  How do you do it?

On Suspend I may get 6 hours.  I tried Hibernate last week. About 10 hours later the battery was at 1%.

Are you sure it really hibernated? When it's hibernating it should be completely powered off, so it shouldn't consume any power. And on suspend the only power that is used is to keep the memory in ram, so it should not drain the battery much.

My laptop will drain the battery in about two hours when I run it on battery, but I can leave it in suspend mode at least three days (haven't really tried any longer, but I think it could stay longer than that). Unfortunately hibernate doesn't work for me.

---

### Post by cespinal on 2008-05-19
I really thought the GPU was still on when the laptop is on suspend so I was concerned about heat build-up. Hibernate wont work in my laptop but now I guess that it wont concern me anymore :lolflag:

BTW, the differency between ubuntu and vista in battery performance and even in heat build up it preety important. I had to use chillpads on my laptop while using vista and I now they does not seem soooo necesary.

---

### Post by Wharf Rat on 2008-05-19
Jocko,
I have an IBM T61.
When I close the lid, Press Fn-F4, or Select "Suspend" from the Ubuntu shutdown menu, it appears to go to sleep, i.e. the battery light is still on but the computer is essentially off. It seems to have  a minimum power drain and the battery will last almost all day at this rate.

Last week I tried using "Hibernate" from the shutdown menu.  I took it to work but did not use the machine.  At the end of the day I had about 1% battery left.  

Is there anything I can check?  Logs, etc.
Settings to change?

---

### Post by fuzzyworbles on 2009-03-28
can anybody quantify how much juice gets drunk while in standby so we can establish the norm?

for example: 

at 7:26, the battery was at 64%
at 20:34 is 44%
13 hours drains 20%
1.5% per hour under linux
(on an acer aspire one)

---

### Post by CraigBray on 2009-03-28
I've got an Acer Aspire 6920G and when i put it in sleep/suspend i get about 7 hours of battery, hibernate it lasts forever, as it should...and on regular battery i get 3 hours. The thing about laptop batteries, is that when you're using them, you have to take into account the hardware involved, the charge of the battery, the strength of the battery, and the size, in conjunction with which power mode do you have it on (in the Windows setting at least, didn't experiment a lot with Ubuntu, only tested the time, just got the sound working last night though WOO! OSS4)

---

### Post by sdennie on 2009-03-29
> **fuzzyworbles said:**
> can anybody quantify how much juice gets drunk while in standby so we can establish the norm?

for example: 

at 7:26, the battery was at 64%
at 20:34 is 44%
13 hours drains 20%
1.5% per hour under linux
(on an acer aspire one)

You can only quantify it for a particular machine.  It depends on your hardware and the size of your battery.  With a 9 cell battery on my Dell XPS M1330, I'd be very surprised if it died after being suspend for a week if it started on a full charge.  I haven't actually tested this theory because it's never been suspend for more than the 8 hours it takes me to sleep but, the amount of power it uses during those 8 hours is miniscule.

---

### Post by fuzzyworbles on 2009-03-29
Oh, yeah, I guess you're right. I refuse to believe that this can't in some way be quantifiable though. How do you suppose we could make such a measure more objective irrespective of particular hardware? Somehow measure amp or watt output or reserve? I'm really grabbing at straws here.

I recall when I had an IBM T30 there was an issue with suspend where some devices kept running and drawing power. Ever since I've been suspicious of my later laptops really really really being suspended. Maybe it's a personal issue.

---

### Post by sdennie on 2009-03-29
> **fuzzyworbles said:**
> Oh, yeah, I guess you're right. I refuse to believe that this can't in some way be quantifiable though. How do you suppose we could make such a measure more objective irrespective of particular hardware? Somehow measure amp or watt output or reserve? I'm really grabbing at straws here.

I recall when I had an IBM T30 there was an issue with suspend where some devices kept running and drawing power. Ever since I've been suspicious of my later laptops really really really being suspended. Maybe it's a personal issue.

It's not a personal issue.  Suspend is a BIOS call and linux does as much as it can to make that call go down and come up smoothly as possible before letting the BIOS functionality kick in.  What actually happens at the hardware level is impossible to say (unless you are very good at reading DSDT files).

Until very recently, machine vendors have cared very little about differentiating themselves for battery life in any manner.  The difference between 1 hour and 1.5 hours isn't something that makes for a bullet item.  The difference between 2 and 6 is.

So, as vendors begin to realize what is important to customers they won't just wholesale take a BIOS from someone that kind of vaguely does some almost useful stuff sometimes (I'm looking at you Toshiba (no, I'm glaring at you with very angry eyes)), they will optimize for the hardware they are selling.  Some vendors already do this.  Dell comes to mind.  I'd love to test how long my machine would stay suspended but, I know for a fact that it would stay that way for much, much, longer than I could bear to live without it.

Edit:
If someone were willing to put up a large enough bet, I'd place 2 weeks on my suspend uptime.  And I'd be willing to put a lot on it.

---

