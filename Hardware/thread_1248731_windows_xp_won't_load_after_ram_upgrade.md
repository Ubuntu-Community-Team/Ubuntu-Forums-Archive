---
title: "windows xp won't load after ram upgrade"
date: 2009-08-24
forum: Hardware
---

### Post by hockey97 on 2009-08-24
Hi, I tried both windows xp and ubuntu live cd.  none will boot after I did a ram upgrade to my old pc. I have a motherboard: biostar M7VKB. I upgraded from 256mb to 768mb. the max ram I can have for the system is 768mb.

Now bios sees the ram 768mb. I then try booting into windows I get the loading screen and at the end I get a black screen for 10 min then a blue screen with hex code errors displayed for 1 to 3 seconds. Then the computer reboots by itself.

Then I tried the ubuntu 9.07 whatever the latest version it is. I used the live cd. I poped it in and when it tried booting I got an booting error in spanish or some other lango then english. 

Any Ideas what I could do. I know the ram is the right type and all of them are 256mb a stick and I got 3 sticks.

They all run at 133megahertz ram. any ideas what could be wrong?

---

### Post by hockey97 on 2009-08-24
any ideas on what I could try?

---

### Post by PatrickVogeli on 2009-08-24
I'd say the ram is bad... even if it was new, it can happen.

---

### Post by Monkey.feets on 2009-08-24
Try putting back in the old ram and see if it boots, if it does the new ram is either bad or not compatible with your system

---

### Post by davec64 on 2009-08-24
To identify the bad ram, try putting in 1 stick and booting, then swap each stick to identify the bad one.
With luck you might get 512 working :)

---

### Post by bondmatt on 2009-08-24
For those that are not aware of this: you should be grounded when touching hardware. Discharges of static electricity can ruin sensitive components. I am always hesitant to purchase RAM not in an unopened package. For older computers I have found that local small retailers will usually install RAM they have sitting around for free and give a decent price. It might be a bit more than Amazon or Ebay but I think the assurance that seeing it works before you buy it is worth the small increase in price.

If it boots some RAM probably works. I bought a few old laptops from the local university (very cheap, surplus equipment) and two had no RAM in them (one Dell, one Toshiba) neither would even let me get into BIOS. I dont think either one would even display anything. One had dedicated video memory, although I doubt that can be used by the system.

Good luck,
- Matt Bondy

---

### Post by hockey97 on 2009-08-24
ok, when I put the old ram it works fine. 

When I put in 2 ram of 256mb it works fine. When I put in 3 sticks again. I now get 512mb not 768mb.

We notice that the ram pins were oxidised. So I cleaned them . 

I took a A+ certification computer repair class in highschool. I even build a new computer in class.

I know about how to put ram and about static eletricity. I am aware their is a eletrostatic band that you can wear around your wrist to ground you. I took the computer and put it in the bathroon table. The reason it was dark and we have mirrors in the bathroon and the room lights up really good. 

well my system works. Just that I now can't get 768mb to be shown. 

I am using 1 old 256mb ram and 2 new ones. the old one I put by itself and tested it and it worked.

then I added the ram one by one tested it. the second new ram got the radings to 512mb. Then when I add the third ram I got nothing added. Then I took out the third one and put in another new one. 

I have total 3 new 256mb ram. and 1 old 256ram and 1 128 old ram.

I tried the other new one and dosen't work. I then tried those that didn't work on my systems to my dads computer and it worked on his computer.

I don't think the ram is bad . It's something I never experienced and I upgraded rams for many systems for many people.

I even changed ram for laptops and those mini computers.

So putting new ram is not something new to me. I know exactly what computer tech know. the one that repair your pcs. I just won't not the latest technology stuff. Since I never worked or got certified cause they want 200 bucks to take a test where I will be making 8 to 11 bucks an hour if I am lucky to get a job in that area.

I will play around moving around the ram and see if I can get it to 768mb.

---

### Post by philcamlin on 2009-08-24
if its not showing up its probably now being recognised 

are you sure the sticks are compatible togather ?

---

### Post by oldfred on 2009-08-25
You can use a pencil eraser to clean the contacts, use some alcohol to remove any eraser stuff. 
I never tried it but Jerry Pournelle recommended stabilant 22 as a contact improver. It is expensive but he says it works.

---

### Post by dandnsmith on 2009-08-25
The fact that initially 768MB were recognised by the BIOS, and now they aren't suugests that there is more detective work to be done (I once had a system with this sort of behaviour).

You've tried the one-at-a-time (and it works), and 2 work, but there are a lot of possible combinations here. For the 3 together (supposing you just have 3 slots), there are 6 possible. If the sticks aren't identical (and from the same manufaturer), then the order can be critical.

Another thing I had problems with was using some single-sided and some double-sided sticks.

---

### Post by hockey97 on 2009-08-25
ya, my dad cleaned it for me. He worked at gm as a eletrician and knows many computer geeks and computer hardware engineers that he worked with. He told me the last old hardware engineer told him to use a rubber eraser and some dish soap to clean the contacts when oxidized. so my dad told me this. He notice the new generation of hardware engineers screamming when my dad told them to use a rubber eraser. My dad said it works better then alcohol. 

Well, So far I tried many ways to stick the ram in.  It's very weird. 

I have 3 slots and can only hold max 768mb of ram. 

now whats weird when I moved 3 new ram sticks around in 3 different slots I get 3 different resuelts. One would only detect 512mb. the other combination would not let the computer boot at all I will get the post beeps. Then the third would show 768mb but when I try to boot any os even ubuntu I get a booting error. In ubuntu it's in spanish or some other lango. In windows I get the blue screen of death. 

after 9 combinations since I have 3 new ram cards and 3 slots making it possible for 3 cars per slot. 
I then decided to use the old 256mb ram. I got very similar results. 

I also even check each ram if they work by placing them one at a time and testing them. They all got a 256mb reading in the bios. 

I notice if I get to 768mb of ram to be reconized by bios. The OS will freak out and spit out booting errors. I know for a fact that you can have more then 768mb for any current OS like ubuntu,windows etc.

I am pretty much stumped. :confused:

I currently made this post with the computer only using 512mb of ram.

---

### Post by dandnsmith on 2009-08-26
I agree with your dad about using eraser to clean contacts - alcohol is only really good for shifting grease.

For the rest, you may well have to stick with the 512MB - sometimes you can discover practical limitations on motherboards by googling for the model name/number: I know that at least one of the motherboards I've used has limits/problems not in any of the literature (sometimes it's how many of the slots you can load to the maximum, sometimes whether the RAM sticks have to be matched ...)

Good luck in your endeavours.

NB my current system runs Ubuntu with no hiccups on 2GB RAM - so, no limit there. However, at the lower end there can be a problem with installing using the graphics-based installer, and there may be a limit on how much will run or which desktop to use (here I've found distros like DSL to be of help)

---

### Post by hockey97 on 2009-08-28
I checked the motherboard manufacture  manual.It states max ram of   768mb. I played around with the ram. I tried different stuff. I noticed that any thing above 512mb of ram. It will cause a weird OS error for both windows xp and ubuntu.  

I even put a 128mb old ram back in to make 600 something mb.
t 
I know it's not the ram. Bios can easily detect the 768mb ram. It's just that  any OS won't accept the ram giving a nice error boot message.  Is their anything I should look at like the ram slot pins?

---

### Post by hockey97 on 2009-08-28
I fainlly got the 768mb ram working. Don't ask me how I got it to work.

well just in case anyone that has the same problem with old or new computers.

What I did I tried every combination. Then just now I just put in all new ram back in. I then had the lid open. When I turn on the pc. I then watched what bios would see. if it was the right numbers and the OS would spit out a boot error. I then pressed on each ram card kinda hard. At one point one ram I heard a click click. I really pressed hard on the ram cards. You should hear a click click. After that the 768mb ram would then work.

So my problem was that it that the ram was lose for some reason. Even thought those clips where their holding the ram in. I still put pressure. 

The thing is that it still stumps me to why this was the case. I thought if the ram was loose you shouldn't even read the full ram reading that you expect.

So if anyone has this problem and know they have the right ram by looking at their motherboards manufactors manuel. If you get an OS boot error but see bios seeing your ram fully. Then it could mean the ram was loose still. You can also try to clean the ram pins. If you see it more like orange/golden color pins. It means it's oxidized. What I did was to use dish soap and a eraser just like either on top of a pencil or if you have those big huge erasers use those. Go over the pins by scrubbing them. you should see a light orange to silver color.

Hope this helps anyone else. It took me a lousy 5 days to get here. I also just started college classes so didn't spend alot of time on it.

---

### Post by Phreak5758 on 2009-08-29
I wonder if it might not be the actual slot for the ram...  I had one go bad on an old frankenputer I had, and it would see the ram part of the time.

---

### Post by dandnsmith on 2009-08-29
In the days when 768MB was maximum you could use, the design of slot was designed to be secure when loaded - and you had to be prepared to press quite hard, until you heard that vital click.
I swear that, after some sessions unplugging and replugging RAM, I had grooves in my fingers for days.

---

