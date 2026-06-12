---
title: "Restricted ATI Drivers Freeze"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by oo-boon-too on 2007-04-22
When I decided to install the restricted drivers from the "Install restricted drivers" option in System>Restricted Drivers, my computer freezes after a set amount of time after Ubuntu Boots.
I am on 7.04 i386 Fresh CD Install
Using ATI RADEON X1300PRO (Sapphire)

On a side note, I also installed Wine as this was installing, I'm not sure if that made it mess up or not. I'm afraid to try again, hopefully avoiding the necessity to Install again (Ubuntu that is).

Any help is greatly appreciated.

-Me

---

### Post by Inspire1997 on 2007-04-22
I have the exact same issue. I have a x1600 and this occured after I selected the "restricted driver" 

Can anyone tell us how to undo this? Everything worked great before.. :(

---

### Post by Invius on 2007-04-23
I gave up and merged my partitions, ati is just a crap card to run linux with, and sadly, xp is proving 100% more stable, i have a radeon x300 and even without the restricted drivers I still lock up constantly it's just not worth the trouble anymore, for me atleast.

---

### Post by oo-boon-too on 2007-04-23
I have a 250.1GB Linux HDD because Linux works with my large HDD better than windows, as it only can see 137.4 GB of it. That, and it makes scraping noises. In linux it works fine, nad has 250.1 GB. The VId card is recognized, but full support is obviously not there. If it was any worse, I might go to Windows until i got a GFX card that was more Ubuntu- Friendly. With that said, what cards have highest support? nVidia? Any specific model? I just spent a S-Load of money on my current one, so i wont change anytime soo, but if i were to get one in the future what would be a good suggestion?

---

### Post by Invius on 2007-04-23
> **oo-boon-too said:**
> I have a 250.1GB Linux HDD because Linux works with my large HDD better than windows, as it only can see 137.4 GB of it. That, and it makes scraping noises. In linux it works fine, nad has 250.1 GB. The VId card is recognized, but full support is obviously not there. If it was any worse, I might go to Windows until i got a GFX card that was more Ubuntu- Friendly. With that said, what cards have highest support? nVidia? Any specific model? I just spent a S-Load of money on my current one, so i wont change anytime soo, but if i were to get one in the future what would be a good suggestion?

I am assumping you don't have to hold the power button on your machine every 20 minutes like I do, anyways, I believe nvidia is the best, their drivers are not 'restricted' so I am assuming the source is public, either that, or people took the time to write alternative drivers, either way, the fact that 'smartgart' exists tells you ati is crap.

I could stop the freezes altogether if I disabled beryl/compiz and what not, but the whole point of running linux was the effects offered by beryl and to replace vista as it just ran too slow with only 512 ram.

As for the future? I would say nvidia, ati has proven unstable too many times in too many operating systems, and the only beef I have with nvidia is their initial lack of support for vista while ati was ready for vista when it shipped. and if you ask me, I'd rather wait for stable drivers than be given crap drivers for crap hardware.

The only reason XP is more stable with ATI is because of smartgart, it takes 5 minutes to load everytime you startup xp, and checks for crap that will cause lockups and disables those functions, as for linux, there is no smartgart, nothing is disabled, linux would probably flip if software demanded that much control over hardware as smartgart requires and so it locks up. If you don't believe me, lookup a definition for smartgart.

---

### Post by CWayne on 2007-10-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+s...20/+bug/109482ain](https://bugs.launchpad.net/ubuntu/+s...20/+bug/109482ain)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Fiesty 7.04 on my Toshiba A75 originally installed and performed well but I had a few freezeups and lost complete control, having to reboot. This recently got worse, occuring more often, sometimes every 2 to 5 minutes. I spent frustrating hours trying to find info. I finally, through google, ended up at the solution. If you're having this problen, go here and read the threads.
I followed the instructions and the problem hasn't returned all day.
This is the launchpad bug fixing place.
copy & paste in your browser...

[https://bugs.launchpad.net/ubuntu/+s...20/+bug/109482ain](https://bugs.launchpad.net/ubuntu/+s...20/+bug/109482ain) 

It hasn't frozen again since then, several days ago.......whew!!!

Cliff

---

