---
title: "Is the hardware of a Dell Vostro 3500 or 3700 Ubuntu friendly?"
date: 2010-11-22
forum: Hardware
---

### Post by ^andrea^ on 2010-11-22
I'm looking for a new laptop to use with Ubuntu but I'm finding it not so easy and, above all, a bit frustrating because of the lack of info/support provided by the different vendors (even the big ones).

First of all I want to point out that I'm asking if this computer is compatible hardware-wise to Ubuntu/Linux, not an opinion about the specs since I can "pretty much" understand it. :-)

So, for example I found [this]("http://www1.euro.dell.com/uk/en/business/Dell-Laptops/vostro-3700/pd.aspx?refid=vostro-3700&s=bsd&cs=ukbsdt1&~ck=mn") "Dell Vostro 3700" sold on their site for 694€ (£569) with:
Intel Core I5 460M(2.53GHz) (I'd be very interested to get this new type of processors "I")
4GB RAM 1333MHz DDR3 (4GB expandable to 8 at some point in the future would be nice)
SATA 320GB 7200 RPM (whatever the size is fine)
17" WLED screen (this is not a problem either, even a 15" would be fine)
Graphic card: Nvidia Geforce GT 330M, 1GB dedicated (not bad at all)

Now, how do I make sure it's all going to work with Ubuntu?
Where should I look at?

I checked [http://www.linux-laptop.net/]("http://www.linux-laptop.net/") where, with a few tweaks, it seems to be working quite well..
Is there a better place where to look at?

I found also this article on PCworld quite interesting but obviously general: [http://www.pcworld.com/businesscenter/article/211113/how_to_choose_a_linux_laptop.html](http://www.pcworld.com/businesscenter/article/211113/how_to_choose_a_linux_laptop.html)

Please let me know what you think and/or in case you have other machines to advice.

Thanks in advance,
Andrea

---

### Post by epz on 2011-01-19
Bump, I'd like to have some informations about it too since apparently things are a lil confused here.

Dell Vostro 3700 is certified for ubuntu 10.10 , 10.04  [http://webapps.ubuntu.com/certification/hardware/201001-4961/](http://webapps.ubuntu.com/certification/hardware/201001-4961/)


Someone had (and googling this shows its widespread) problems with graphic card (i don't even get what the hell is going on there, double card o.o)
[http://ubuntuforums.org/showthread.php?t=1567861](http://ubuntuforums.org/showthread.php?t=1567861)

And i also found some wifi / sensors issues.

someone tho says it's great
[http://www.art.ubuntuforums.org/showthread.php?t=1591930&highlight=vostro+3700&page=3](http://www.art.ubuntuforums.org/showthread.php?t=1591930&highlight=vostro+3700&page=3)

I join the op post and add my questions

1. does it really work or the &quot;certified&quot; just means it turns on?

2. how would i fix graphics problem? apparently nvidia isn't supporting optimus on linux but..if someone says it works great he/she must have found a fix?

3. is there any 3700 owner that may give me some advice?

thanks in advance, i hope the OP will come back and check the post if we got an answer lol.   
 
 PS: i forgot to say, i may want to be playing on it, thats why i was concerned about graphics

---

### Post by cascade9 on 2011-01-19
> **epz said:**
> 1. does it really work or the &quot;certified&quot; just means it turns on?

2. how would i fix graphics problem? apparently nvidia isn't supporting optimus on linux but..if someone says it works great he/she must have found a fix?

1- No idea on the exact 'certification' process. IMO it should never have passed, see answer 2. 

2- nVidia isnt supporting optimus on linux. There is a BIOS setting in the 3700 "Hybrid Graphics- Disabled", which AFAIK turns of the nVidia GPU totally, so it only uses the intel video. Yes, it will work, but you arent getting what you paid for (laptops without nvidia optimus are cheaper).

---

### Post by epz on 2011-01-19
> **cascade9 said:**
> 1- No idea on the exact 'certification' process. IMO it should never have passed, see answer 2. 

2- nVidia isnt supporting optimus on linux. There is a BIOS setting in the 3700 "Hybrid Graphics- Disabled", which AFAIK turns of the nVidia GPU totally, so it only uses the intel video. Yes, it will work, but you arent getting what you paid for (laptops without nvidia optimus are cheaper).

hi cascade9, first of all thanks for your reply, now don't get me wrong but, are u speaking from experience on point 2 (as 3700 owner)? I am not I haven't bought yet the laptop but googling i see people can't turn the hybrid graphics off from bios, is this because they can't/don't want to find it on BIOS or you're just assuming there is such option? 

And if you're a 3700 owner or have any idea of what it may be, would the intel graphics be any good? (there is a version without nvidia, supposed to be cheaper too).

As stated above I may get gaming, probably go insane and even install windows 7 for that purpose, obviously I don't expect to play on a laptop at max resolution or so (and my max time would be 3 hrs a day when i'm really bored), I usually run at lowest-to-mid  graphic settings, and don't really even play that much, could you rate the integrated graphics by any chance? (epic off topic but ye, helping me to choose lol)

Thanks again.

---

### Post by mastablasta on 2011-01-19
HP G62 series and i think G72 also seem nice. though they have i3 they do come with SUSE Linux preinstalled. so Ubuntu should work as well.

---

### Post by cascade9 on 2011-01-19
> **epz said:**
> hi cascade9, first of all thanks for your reply, now don't get me wrong but, are u speaking from experience on point 2 (as 3700 owner)? I am not I haven't bought yet the laptop but googling i see people can't turn the hybrid graphics off from bios, is this because they can't/don't want to find it on BIOS or you're just assuming there is such option? 

And if you're a 3700 owner or have any idea of what it may be, would the intel graphics be any good? (there is a version without nvidia, supposed to be cheaper too).

As stated above I may get gaming, probably go insane and even install windows 7 for that purpose, obviously I don't expect to play on a laptop at max resolution or so (and my max time would be 3 hrs a day when i'm really bored), I usually run at lowest-to-mid  graphic settings, and don't really even play that much, could you rate the integrated graphics by any chance? (epic off topic but ye, helping me to choose lol)

Thanks again.

No, I'm not a 3700 owner. There was an option to disable the 'hybrid graphics' with at least one BIOS version (A08 from the forum posts I saw). I dont think that the option was there with earlier BIOSes, and for all I know dell removed it from the later BIOS version (A09) 

It was docutmented though, you can see here- 

[http://support.dell.com/support/edocs/systems/vos3700/en/SM/Bios.htm](http://support.dell.com/support/edocs/systems/vos3700/en/SM/Bios.htm)

I've never been fond of laptops for gaming. (forgive me for this, I know how it might look). Maybe a cheap nettop for portablility and a desktop for home/gaming? 

Intel graphics are generally very weak. If you want the laptop for gaming, at all, a ATI or nVidia GPU (without 'optimus' or 'switchable graphics') is much better than an intel video chip.

---

### Post by epz on 2011-01-19
> **cascade9 said:**
> There was an option to disable the 'hybrid graphics' with at least one BIOS version (A08 from the forum posts I saw). I dont think that the option was there with earlier BIOSes, and for all I know dell removed it from the later BIOS version (A09) 



they nerfed my only hope <.<, well it appears that I have no choice lol

> **cascade9 said:**
> 
I've never been fond of laptops for gaming. (forgive me for this, I know how it might look).


It looks right, I agree with you on that, I'm not going to use it for gaming, I'm just saying that it may happen that if i had a boring day and i can't use my desktop i may want to use the laptop, I have plans on a desktop too anyways.

(just to clear it, i'm not really a gamer but i think that everyone needs, sometimes to clean up their minds burning some brain on games)

> **cascade9 said:**
> 
It was docutmented though, you can see here- 

[http://support.dell.com/support/edocs/systems/vos3700/en/SM/Bios.htm](http://support.dell.com/support/edocs/systems/vos3700/en/SM/Bios.htm)



Yes i found that post too, and some people were claiming that such option was unavailable (apparently they upgraded to A09)

> **cascade9 said:**
> 
Intel graphics are generally very weak.

Here i'm totally ignorant, only pc I had with intel graphics has been used only to backup files from my main pc using cli (couldn't be bothered setting up a DE lol) so i have no idea at all of what they look, are you saying that you wouldn't suggest them?

---

### Post by epz on 2011-01-19
> **mastablasta said:**
> HP G62 series and i think G72 also seem nice. though they have i3 they do come with SUSE Linux preinstalled. so Ubuntu should work as well.

Just noticed this post (yep tired lol) HP was the second choice in case Dell failed. It appears i'll have to give a look, thanks for your hint.

---

### Post by epz on 2011-01-24
I know this is an epic off topic but, do you think intel gma HD (i3 330) would play nicely with kubuntu or ubuntu with compiz? (graphic effects and so on), aslong as it does that it covers almost everything i'd like to do, intel gma on a pentium processor (4 years old i don't remember the model sadly) didn't work well with kubuntu but compiz survived it starting from Lucid Lynx (apparently prior version had problems with that card).

---

### Post by TBABill on 2011-01-24
I have a Dell 1564 that has the Intel Core i3-330m and I do not have an additional graphics card. Mine uses the on-chip GPU and it works wonderfully with Compiz. Since I don't game I have seen no application where the graphics are weak in any way and they just work out of the box without additional configuration. I do know they won't work well in PCLinuxOS because the xorg version is too old (must be 2.11 or newer and theirs is 1.something), but Ubuntu, Mint and Debian all work well with it.

---

### Post by Sylslay on 2011-02-16
What about sound on Dell vostro 3700 and - skype?

After some time. 
seems to be ok

[http://www.ubuntu.com/certification/make/Dell/laptops](http://www.ubuntu.com/certification/make/Dell/laptops)

[http://www.ubuntu.com/certification/hardware/201001-4961](http://www.ubuntu.com/certification/hardware/201001-4961)

---

