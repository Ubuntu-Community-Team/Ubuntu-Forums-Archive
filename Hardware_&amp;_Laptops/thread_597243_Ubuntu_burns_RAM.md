---
title: "Ubuntu burns RAM"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by DerMeister on 2007-10-30
Here's a funny story... I know it's long, but please bear with me.

I was just getting warm to Ubuntu on my BenQ laptop, almost shouting its name off the balcony of my apartment and praising it among my friends, because that's how great I found it to be. I was preparing the ground to cross over to Ubuntu (I have just upgraded it from 7.04 to 7.10) and completely get rid of Windows XP. Well, not completely, I need Win for .NET projects at school and gaming, but you get the point.

Last night, I was doing my usual thing - chatting with my friends on Pidgin Messenger, surfing the net and tackling some PHP files. I opened a web page that I use frequently to check the latest news headlines - [www.monitor.hr](www.monitor.hr) - which contains many tiny flash commercials. That page can make Firefox eat my memory in Windows like crazy (I haven't checked with Firefox in Ubuntu yet), and it usually takes 80-90% of the CPU time. Now, it was obvious that Firefox was having a hard time displaying it - it spat out a couple of warning messages about the flash script not running correctly (unresponsive) and that they should be stopped. I clicked 'Stop' button on all of them, then went on to chat with a friend of mine.

When I clicked back in Firefox, Ubuntu sounded with a "bzzt" and garbled up my screen with some horizontal lines. The mouse pointer disappeared and the computer became unresponsive. I shut it down and waited for a couple of seconds. I turned it back again and got the grub boot menu all garbled up the same way (this time they were vertical, dotted lines)! "Whoa!" sad I, "Well this has never happened before!". I booted into Windows, just to find the desktop totally messed up. After clicking a bit here and there, Windows hanged and showed me the nefarious Blue Screen (that was a surprise, I haven't seen one in XP since 2002!).

It turned out to be the RAM card, burned. It was Kingston DDR266 512MB, and I tried it on my friend's HP laptop to no effect. I had two 512MB cards, both Kingston, but the burnt one was 266, and the one still alive 333MHz. I'm just wondering how could that have happened?

Now I'm afraid to boot into Ubuntu again. :) The hype I felt about it blew up in billion pieces in an instant. I'll keep away from it for a while now...

My configuration is:
Centrino 1.5GHz
used to be 1GB RAM (Kingston DDR333 512MB + Kingston DDR266 512MB), now only DDR333
Intel 855/855GM onboard graphics
80GB Samsung

I anyone else had something similar happen to them, please share.

---

### Post by stchman on 2007-10-30
> **DerMeister said:**
> Here's a funny story... I know it's long, but please bear with me.

I was just getting warm to Ubuntu on my BenQ laptop, almost shouting its name off the balcony of my apartment and praising it among my friends, because that's how great I found it to be. I was preparing the ground to cross over to Ubuntu (I have just upgraded it from 7.04 to 7.10) and completely get rid of Windows XP. Well, not completely, I need Win for .NET projects at school and gaming, but you get the point.

Last night, I was doing my usual thing - chatting with my friends on Pidgin Messenger, surfing the net and tackling some PHP files. I opened a web page that I use frequently to check the latest news headlines - [www.monitor.hr](www.monitor.hr) - which contains many tiny flash commercials. That page can make Firefox eat my memory in Windows like crazy (I haven't checked with Firefox in Ubuntu yet), and it usually takes 80-90% of the CPU time. Now, it was obvious that Firefox was having a hard time displaying it - it spat out a couple of warning messages about the flash script not running correctly (unresponsive) and that they should be stopped. I clicked 'Stop' button on all of them, then went on to chat with a friend of mine.

When I clicked back in Firefox, Ubuntu sounded with a "bzzt" and garbled up my screen with some horizontal lines. The mouse pointer disappeared and the computer became unresponsive. I shut it down and waited for a couple of seconds. I turned it back again and got the grub boot menu all garbled up the same way (this time they were vertical, dotted lines)! "Whoa!" sad I, "Well this has never happened before!". I booted into Windows, just to find the desktop totally messed up. After clicking a bit here and there, Windows hanged and showed me the nefarious Blue Screen (that was a surprise, I haven't seen one in XP since 2002!).

It turned out to be the RAM card, burned. It was Kingston DDR266 512MB, and I tried it on my friend's HP laptop to no effect. I had two 512MB cards, both Kingston, but the burnt one was 266, and the one still alive 333MHz. I'm just wondering how could that have happened?

Now I'm afraid to boot into Ubuntu again. :) The hype I felt about it blew up in billion pieces in an instant. I'll keep away from it for a while now...

My configuration is:
Centrino 1.5GHz
used to be 1GB RAM (Kingston DDR333 512MB + Kingston DDR266 512MB), now only DDR333
Intel 855/855GM onboard graphics
80GB Samsung

I anyone else had something similar happen to them, please share.

So you are blaming RAM failure on Ubuntu?  That is a new one I must say.  It is not possible that that RAM failed regardless of the OS?

---

### Post by dabl on 2007-10-30
> **DerMeister said:**
> Here's a funny story... I know it's long, but please bear with me.

I anyone else had something similar happen to them, please share.



Yeah, thanks -- I wondered what was causing this.  Ever since I started using Ubuntu I keep forgetting to take my meds ...







:lolflag:

---

### Post by JBAlaska on 2007-10-30
It's never a good idea to mix ram module speeds (Even if it sometimes works).

Sorry to here about your loss, But I'm betting it was a coincidental thing possibly triggered by intensive ram usage (firefox)

---

### Post by kerry_s on 2007-10-30
your mixing ram and you think nothing is going to happen. what you describe can happen on any os. your just lucky you didn't lose them both. they tell you that using 2 different speed rams, it will run at the slowest, the 266 in your case, but if you read the fine print it tells you don't mix ram. but go head blame linux if it makes you feel better and just stick with your safe windows system.

and for that site you need to get noscript or flash block, that's just ridicules to have that many flash ad's.

---

### Post by altu on 2007-10-30
Ubuntu Burned your ram? Are you for real?

---

### Post by Cannaregio on 2007-10-30
> **DerMeister said:**
> That page can make Firefox eat my memory in Windows like crazy (I haven't checked with Firefox in Ubuntu yet), and it usually takes 80-90% of the CPU time. Now, it was obvious that Firefox was having a hard time displaying it - it spat out a couple of warning messages about the flash script not running correctly (unresponsive) and that they should be stopped. I clicked 'Stop' button on all of them, then went on to chat with a friend of mine.

This hasn't got much to do with your OS, and seems to have a  lot to do with the browser you use and the pages you visit.

A suggestion I'll give you, if you often visit that kind of crap pages on the web, is to use [OPERA]("http://www.opera.com/") instead of Firefox, and get acquinted with its very powerful "right click -- >block content on the fly' features. Opera out of the box seems also to have a better memory management vis-à-vis a firefox with too many finetunings and additions.
Just try opera out, both in linux and in windows, and judge by yourself.

---

### Post by vikrant82 on 2007-10-30
Damn! you shouldn't have gone to that site. Its notorious for burning RAMs. :popcorn:

Yea, but we do understand your pain. So how does it feel on half the RAM. I think it should be running faster since this RAM is faster. With old RAM this one was also running at 266Mhz.

---

### Post by JBAlaska on 2007-10-30
Good point vikrant82, I bet it's noticeably faster now....so Ubuntu fixed your laptop would be a better title for this thread LOL

---

### Post by zmatt on 2007-10-30
I doubt that the ram being faster will makeup for the fact that he now has half the ram he had before, IMO 512mb 266mhz > 256mb 333mhz. but i could be wrong.

---

### Post by Koziasty on 2007-10-30
Guys, you're such flamers. He came here, asking, if that was possible, and you all ubuntu geeks started insulting him and call him a noob... 

A bit of distance to yourselves is useful, and no mistake.

Sorry about your ram, mate, but I would just carry on using Ubuntu, cos, although rude and with no distance, these guys may actually be right..

---

### Post by vikrant82 on 2007-10-30
> 512mb 266mhz > 256mb 333mhz

In his case, probably 512mb 333mhz > 1g 266mhz.

---

### Post by BDNiner on 2007-10-30
you should not have mixed the different frequencies of RAM. It may not have caused your chip to burn but it could have been a factor.

---

### Post by misfitpierce on 2007-10-30
Could of been faulty hardware from company also. I never heard of an OS burning up ram literally though. But I don't read much so I don't know.

---

### Post by DerMeister on 2007-10-30
yeah I know about mixing ram speeds, in fact my Windoze seems little more responsive after I removed the 266 ram (don't know about Ubuntu, haven't tried yet).

but guys (@kerry_s especially), I've been using that configuration for more than a year and a half! I tell you, I opened that page a gazillion times in Windows and, apart from obvious slowdown, nothing else happened. Firefox got a bit unresponsive from time to time, but that's it! and I got that ram long ago because no other were available at the local stores in those days, so I tried it and it worked and I just kinda let it be...

what more, I used the same ram config with Ubuntu Edgy when it came out a year ago and visited the same freakin page over and over without a glitch (without having my ram burned, that is).

maybe it has something to do with the recent upgrade I did. I'm just saying that like all of you, I've NEVER before heard of an OS burning ram (that's the reason I'm writing this), and I admit that mixed frequencies could have been a major factor, but why didn't it happen before, and why not in 'safe Win' (@kerry_s again)? does the mixed ram frequencies bother Ubuntu that much? is it possible that there were too many memory page faults or smth for Ubuntu to handle?

now, I can say I'm AT LEAST an "experienced computer user", I can tell what might have caused this and how to fix it, but think in more layman terms. say this happens to an utter noob. he would curse Ubuntu and all of its children (well, its descendants - I'm trying to translate the worst curse in my native language :) ), especially since he's got noone to turn to for warranty or smth, and all he's left with are forums like this where he's told to 'go back to his safe Win' (of course, @kerry_s :) - sorry dude, you seemed to take my post particularly personally)!

man, do I like to write! there should be a limit as to how many characters you can type (is there? should I dare try? :) )...

I appreciate all the feedback people!

---

### Post by kerry_s on 2007-10-30
well then if it's as you say it's old ram it just might of come to it's end, but saying "Ubuntu burns RAM" as if you know for sure the cause was the os and not simple hardware failure. just that you know i don't take it personally, but just cause your using linux at the time of the failure doesn't mean the os is at fault, it's just simple fud and intern gives ubuntu/linux a bad image, it's on par with ms scare tactics. ask yourself if it happened in windows would you say "windows burns ram" or would you say "my ram died" .just my 2 cents.

---

