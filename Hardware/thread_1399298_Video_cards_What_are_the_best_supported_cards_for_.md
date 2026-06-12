---
title: "Video cards: What are the best supported cards for linux."
date: 2010-02-05
forum: Hardware
---

### Post by Kir_B on 2010-02-05
Hey all. I'm getting ready to take the plunge and buy my very first video card and would really appreciate some guidance. I'm running a dell inspiron 531s, which has dual amd64 4000+ processors and an underpowered 250 watt power supply, which will be upgraded to a 400 watt. It's a slimline case so i'll have to buy a low profile card. I would love to hear any thoughts on a good card, and which of the manufacturers are linux friendly and which ones are not.

Thanks a lot everyone. Kir_b\\:D/

---

### Post by llawwehttam on 2010-02-05
Go for nVidia, DO NOT go ATI.

Here is a list of supported nvidia cards.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

### Post by Simian Man on 2010-02-05
> **llawwehttam said:**
> Go for nVidia

Yes.

---

### Post by Kir_B on 2010-02-05
Thanks a lot folks.
                           Peace. Kir_b

---

### Post by Melcar on 2010-02-05
What do you plan on doing with that machine?  Normally any entry level card from either nvidia or ATI will work (hd4670/gt240 type cards would be nice).  If you plan to use that machine to play some HD content though, your best bet is nvidia.  You could also go with an older ATI card and just use the open source drivers; if you can get a midrange second hand 1K card (something like a x1600) for cheap that would probably be your best bet.

---

### Post by cascade9 on 2010-02-06
+1 to nVidia. For a slimline case, a 8400GS/9400GT or GT210/GT220 would be what I would be looking for. 

> **Kir_B said:**
> Hey all. I'm getting ready to take the plunge and buy my very first video card and would really appreciate some guidance. I'm running a dell inspiron 531s, which has dual amd64 4000+ processors and an underpowered 250 watt power supply, which will be upgraded to a 400 watt. It's a slimline case so i'll have to buy a low profile card. I would love to hear any thoughts on a good card, and which of the manufacturers are linux friendly and which ones are not.

To be technical, you actualy have a single AMD 4000+, its a dual core CPU. finding a 400watt slimline power supply might be a real pain, good luck there. 

Just in case you dont know- the different manufacturers just buy chips from different suppliers and make the cards. There is only a few companies making GPUs for video cars- nVidia and Ati are the biggest, with VIA, Matrox and SIS being, at best bit players. 
 
The manufacturers dont actually make the chips, so in theory if the only difference between (for example) 1 nVidia Geforce 8400GS and a different manufacturers 8400GS would be the layout, and the memory chips.  However, it doesnt really work like that because there are a lot of parts on video cards, and companies will change things from the 'reference' designs (reference cards are made by nVidia and Ati for 'proof of concept' and to show the manufacturers how to build the card). 

So most techies have brands they will never buy unless they have to (XFX for me) and prefered brands (DFI and Gigabyte are my current ones)

---

### Post by Kir_B on 2010-02-07
> **llawwehttam said:**
> Go for nVidia, DO NOT go ATI.

Here is a list of supported nvidia cards.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

Thanks for the link. Just curious, does anyone know how this list works? For example, the entries that don't specify which of the ubuntu's ie: 9.10 etc. Are they supported for all the Ubuntu's? Also if the card is suppurted for 8.10, is that card also supported for 9.04 and 9.10 also? I appreciate and look forward to a response.:confused:

I thought it might be worth adding, that I'm running Ubuntu Karmic Koala.

                                                      Thanks a lot folks. Kir_b

---

### Post by Kir_B on 2010-02-07
> **Melcar said:**
> What do you plan on doing with that machine?  Normally any entry level card from either nvidia or ATI will work (hd4670/gt240 type cards would be nice).  If you plan to use that machine to play some HD content though, your best bet is nvidia.  You could also go with an older ATI card and just use the open source drivers; if you can get a midrange second hand 1K card (something like a x1600) for cheap that would probably be your best bet.

Thanks for the input. I would like to do some gaming { I've been looking forward to playing "[UFO:AI ]("http://ufoai.sourceforge.net/")" for a long time } I'd also like to have the ability to hook to a friends HDTV for both gaming and video purpose. One of the other things I'd like to be able to do, is use google earth without having the fear that my computer is going to have a massive stroke or explode.:oops:

So, I guess I really don't need anything too crazy, just a half decent low profile card.

                               Thanks again. Kir_b

---

### Post by aviedw on 2010-02-07
> **llawwehttam said:**
> Go for nVidia, DO NOT go ATI.


I agree as well. Not to put ATI down, but Nvidia seems to have much better driver support.

---

### Post by Kir_B on 2010-05-26
Thanks to all of you for your help. :P

I know it's taken me a while to express my thanks, but I've been helping my cousin with his uncooperative video card, which really, really doesn't want to work with Ubuntu.

Anyhow, I thought I'd finally take the time to fill in the blanks, in the hopes that I might be able to help someone else, that may have a similar situation.

The situation is as follows:
I'm running a Dell 531s, which is a slimline case with a 4000+ dual core cpu with a 250 watt power supply (If I should include other pertinent details, please feel free to suggest).

I ran into** ****[COLOR=#cc33cc][The Truth About Graphics Power Requirements V2]("http://archive.atomicmpc.com.au/forums.asp?s=2&c=7&t=9354")[/COLOR]**[COLOR=#000000],[/COLOR]**[COLOR=#cc33cc] [/COLOR]**[COLOR=#cc33cc][COLOR=Black]which provided me with the power requirements for a tonne of cards. The other very helpful resource, was the [/COLOR][/COLOR]**[eXtreme Power Supply Calculator]("http://www.extreme.outervision.com/psucalculatorlite.jsp")**[COLOR=#cc33cc], [COLOR=Black]which really told me what kind of spare wattage my power supply (250 watt) had left for my video card. These were essential resources in my decision to not upgrade my power supply (very, very helpful), which looked to be a bit of a pain in the brain to find one that would fit _inside the case_. 

In the end, I decided on an _nvidia geforce 9600 gt_ (made by Galaxy). I've been running it for about a month and a half now and can say that it was exactly the upgrade that I was looking for, and I'm quite pleased with it. [/COLOR][/COLOR][COLOR=#cc33cc][COLOR=Black]Google earth runs  great now, along with every game I've tried to date. I no longer use windoze, so I'm only playing games from the open source community (thanks to all contributers), which suits me quite fine, as I really don't require anything on the bleeding edge.[/COLOR][/COLOR]
[COLOR=#cc33cc][COLOR=Black] 
It was very simple to install, considering that I'm very new to the inside of the PC. Nothing complicated, and with the exception of a new exhaust fan, nothing else needed to be purchased. In the end, it cost me less than a hundred dollars (Canadian dollars) and I highly recommend such an upgrade for those having problems running graphically demanding applications, such as video games and as it turns out, google earth. Even though I didn't think of google earth as an application that would require an upgrade such as this, it was exactly what was needed.

The proprietary hardware drivers installed without incident (I'm not running the "nouveu" open source drivers), which was very nice indeed, as I've read a lot of horror stories and am watching my cousin struggle with his video cards set of problems (an even older computer).

Also worth adding: I installed a higher capacity exhaust fan [A Rosewill 38 cfm (cubic feet per minute)], as I was told that this card runs quite hot. This seems to have solved the heat issue, but it is quite loud.

Also, there was one more link that helped me, and may be helpful to others in a similar situation trying to upgrade their slimline PC. It's [/COLOR][/COLOR][**The highly rated HP Pavilion Slimline PC thread**]("http://hardforum.com/showthread.php?t=1224011"). There is a tonne of info in there. :shock:

I'd like to thank all of you helpful folks out there. I couldn't have done it without you all. Thanks, yet again.

I hope that this is helpful for someone else and if you have any questions, don't hesitate to ask and I'll do my best to answer/help you out.

Good day to all. \\:D/ Kirby ):P
[COLOR=#cc33cc][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by oleink on 2010-05-26
I'd say at the rate ati is going them but not till next year... So yeah I'll say nvidia

---

### Post by cascade9 on 2010-05-26
> **Kir_B said:**
> I know it's taken me a while to express my thanks, but I've been helping my cousin with his uncooperative video card, which really, really doesn't want to work with Ubuntu.


I ran into **[COLOR=#cc33cc][The Truth About Graphics Power Requirements V2]("http://mark.zoomcities.com/images/gfx/GFXpowerchartbyidle.png"), [/COLOR]**[COLOR=#cc33cc][COLOR=Black]which provided me with the power requirements for a tonne of cards. The other very helpful resource, was the [/COLOR][/COLOR]**[eXtreme Power Supply Calculator Signature]("http://www.extreme.outervision.com/psucalculatorlite.jsp")**[COLOR=#cc33cc], [COLOR=Black]which really told me what kind of spare wattage my power supply (250 watt) had left for my video card. These were essential resources in my decision to not upgrade my power supply (very, very helpful), which looked to be a bit of a pain in the brain to find one that would fit _inside the case_. 
[/COLOR][/COLOR]

Does your cousin have a thread here? ;) 

BTW, those 'power supply calculators' tend to overestimate the amount of power used by systems, for various reasons. 

I'm glad that your new card is working out so well ;)

---

### Post by Kir_B on 2010-05-26
> **cascade9 said:**
> Does your cousin have a thread here? ;) 

BTW, those 'power supply calculators' tend to overestimate the amount of power used by systems, for various reasons. 

I'm glad that your new card is working out so well ;)

Thanks **cascade9. **

Concerning the 'power supply calculators'. I was kind of betting that they were over estimating, as I wasn't quite positive exactly how much wiggle room I had left. Definitely comforting to know, thanks.

As to my cousin's thread; He thinks that "forum" means _for him_, so **_I_**, have a thread _forum_ called "[Can't boot to our desktop. Assistance needed]("http://ubuntuforums.org/showthread.php?t=1426234")". #-o

That thread is fairly old, and doesn't reflect our current situation, as we have managed to install a driver, but still can't get past the "(initramfs)" prompt. I'm not quite sure if we're missing something, or we're just plain fighting a losing battle. It sure would be nice to find a magic checklist of things to try [-o<, just so we knew when to give up on this one and give it to some poor sole that's resigned to using windoze.

Maybe some suggestions from all of you wise folks might help out, as he's been taking a break from it for a while now. Then again, maybe it's time to start a new thread? Any suggestions, would of course, be very much appreciated.

Peace everyone. Kirby

---

