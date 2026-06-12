---
title: "How do I downgrade back to 8.10?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by translucent juicebox on 2009-04-23
I don't like 9.04 at all, is there a way to downgrade back to 8.10 without having to do a fresh installation with the 8.10 CD?

---

### Post by Saabtite on 2009-04-23
Chances are you will have to reinstall with the 8.10 CD.  The 9.04 install removes ALOT of packages from 8.10.  And as far as I know, there isnt a downgrade function.

---

### Post by D1ZZ4ZZT3R on 2009-04-23
it just came out today. are you sure you don't want to actually try it first? i'm having a couple problems with it, myself, which i'm about to post a thread about but, i'm gonna give it a shot before i abandon all hope.

what don't you like about it? i find it to be essentially the same.

---

### Post by JK3mp on 2009-04-23
Yeah i'd give it a bit. At least continue to try it out on an additional partition give the updates a chance to fix some things. It JUST came out officially to the mass.

---

### Post by translucent juicebox on 2009-04-23
It's extremely slow for me.  I get 2 seconds of lag opening the applications menu, even when there are no other programs running.  I feel like I'm running a computer designed for Windows 98.  I'd rather just go back to 8.10 and try 9.04 again once all the bugs have been worked out.

---

### Post by D1ZZ4ZZT3R on 2009-04-23
in that case, you may want to wait a few months until 9.1 comes out. if i had a clue as to what was causing the lag i'd attempt to help.

if the slowness is all that's bothering you, check the forums or, start a thread asking for help about it. i'm sure someone can help you, and relatively quickly. do you have all the necessary drivers? also, have you checked for updates? i found a few right after i installed.

---

### Post by yeats on 2009-04-23
There will ALWAYS be bugs/issues/problems with the initial release that will be fixed in time.  If this is a big problem for you, it would probably be prudent to wait a month after a release to upgrade. :-)

---

### Post by Slim Odds on 2009-04-23
> **translucent juicebox said:**
> I don't like 9.04 at all, is there a way to downgrade back to 8.10 without having to do a fresh installation with the 8.10 CD?

Every six months ...... same question......

No, just like every other release, there is no reverse.

---

### Post by fletchoid on 2009-04-24
Here here!  9.04 totally buggered my fabulous graphics in 8.10.  If I try to install the fglrx driver for my ATI 4870, I can't boot into Ubuntu at all.  I get a bizarre screen and total lockup.  Grimmwolf had the solution:  start up in recovery mode, when you get to the menu, choose command prompt with networking, and type:
 apt-get remove --purge xorg-driver-fglrx
I can now get back into my system, but now, I am stuck with a HUGE step backwards in graphics. If I could go back to 8.10 which had fabulous graphics, I would in an instant.

---

### Post by pbpersson on 2009-04-24
> **chrissharp123 said:**
> There will ALWAYS be bugs/issues/problems with the initial release that will be fixed in time.  If this is a big problem for you, it would probably be prudent to wait a month after a release to upgrade. :-)

Yeah - I am using Jaunty on my test machine and everything looks good.....but it is not getting near my production machine anytime before June 1st.

---

### Post by sports fan Matt on 2009-04-24
I agree w/Chris...in all honesty this is why there are LTS  Ubuntu simply wont work for everyone, 100% of the time.  I can see why there are LTS--you dont automatically need to get the latest and greatest every 6 months--it comes down to a user's choice as to what they use their computer for.

---

### Post by JK3mp on 2009-04-24
Yeah alot of people stick with just using LTS releases.

---

### Post by Robster2 on 2009-04-25
This is so strange.    I upgraded to the 64 bit version of Intrepid Ibex from Hardy Herron -  It was a disaster !!  

I went back to Hardy Herron and now have upgraded to Jaunty Jakalope it has worked so well for me.

---

### Post by eaglewealth on 2009-04-25
Hi

Yes I noticed a little jerky playing Quake Arena and SecondLife was too slow to move.  It was fast and better in Unbuntu 8.10 with Quake Arena.

Did you notice firefox can resize the window than it was in Unbuntu 8.10??

---

### Post by Slim Odds on 2009-04-25
> **Robster2 said:**
> This is so strange.    I upgraded to the 64 bit version of Intrepid Ibex from Hardy Herron -  It was a disaster !!  

I went back to Hardy Herron and now have upgraded to Jaunty Jakalope it has worked so well for me.

There is no upgrade path from Hardy to Jaunty.

Only LTS releases support skipping releases in between.

---

### Post by ChrisChinchilla on 2009-04-25
> **fletchoid said:**
> Here here!  9.04 totally buggered my fabulous graphics in 8.10.  If I try to install the fglrx driver for my ATI 4870, I can't boot into Ubuntu at all.  I get a bizarre screen and total lockup.  Grimmwolf had the solution:  start up in recovery mode, when you get to the menu, choose command prompt with networking, and type:
 apt-get remove --purge xorg-driver-fglrx



Just wanted to say after upgrading my Dell Inspiron I just kept getting a black screen and funny coloured bars, your suggestion fixed it... We shall see what performance I get. Still can't enable compiz though, which i was hoping would be fixed... Trying KDE at the moment, finally got some eye candy back!

---

### Post by myxiplx on 2009-04-27
> **fletchoid said:**
> Here here!  9.04 totally buggered my fabulous graphics in 8.10.  If I try to install the fglrx driver for my ATI 4870, I can't boot into Ubuntu at all.  I get a bizarre screen and total lockup.  Grimmwolf had the solution:  start up in recovery mode, when you get to the menu, choose command prompt with networking, and type:
 apt-get remove --purge xorg-driver-fglrx
I can now get back into my system, but now, I am stuck with a HUGE step backwards in graphics. If I could go back to 8.10 which had fabulous graphics, I would in an instant.

Ditto, graphics are an absolute nightmare in 9.04.  I can't use the proprietary drivers at all, the open source drivers just crash me back to the logon screen by default (I had to reset my settings and disable compiz from another account), and even when I do get them working I have cursor corruption and can't run my monitors at their proper resolutions.

Bring back 8.10, this is horrible!

---

### Post by Slim Odds on 2009-04-27
> **myxiplx said:**
> Bring back 8.10, this is horrible!

8.10 never left. If you like it, use it.

I know some people are having "issues", but that happens every release. Most people don't have issues.

---

### Post by dkulchenko on 2009-04-27
Jaunty has just been a terrible experience for me. I've been using Ubuntu since 6.06, and haven't seen anything like this before. Intrepid was amazing, but Jaunty?...

I now have huge boot hard disk problems, the Terminal is firing fake messages at me, I'm getting standby/resume errors, the new GDM theme is a step backwards, the boot splash screen went away and is just text messages now, my fonts are now screwed up, printing doesn't work anymore, and on, and on. 

And with my customized system, I find it difficult and time-consuming to reinstall back to 8.10, so I guess I have no choice but to wait for Ubuntu to improve (back to the way it was) in the upcoming releases.

---

### Post by Slim Odds on 2009-04-27
> **dkulchenko said:**
> And with my customized system, I find it difficult and time-consuming to reinstall back to 8.10, so I guess I have no choice but to wait for Ubuntu to improve (back to the way it was) in the upcoming releases.

I feel for you, but that's what partimage and clonezilla, etc. are for.

Clone your system before you make a move like that.

---

### Post by Zebra Lord on 2009-04-27
Sorry for my ignorance, but is there a way to downgrade back to Intrepid or not without a clean install?  I have an Intel integrated driver so I lost all my eye candy.  If there is could someone pleas let me know how.

---

### Post by 73ckn797 on 2009-04-27
Jaunty runs great but I have been having problems with the drive it is installed on. Prior to this issue Jaunty, even in beta, was running very good. Hang in there and you just may find it to be quite good. My problems are on my desktop system. I upgraded my laptop and all is well and seems to be faster, even as a 32 bit system. My desktop is 64 bit and I will install the 64 bit version.

See specs below. I also have an Intel graphics on the laptop and it runs very good.

---

### Post by pbpersson on 2009-04-27
> **Zebra Lord said:**
> Sorry for my ignorance, but is there a way to downgrade back to Intrepid or not without a clean install?  I have an Intel integrated driver so I lost all my eye candy.  If there is could someone pleas let me know how.

There is never any way to go backwards when upgrading.  Time only goes in one direction.  The only way to go back in time is using a clean install.

---

### Post by dkulchenko on 2009-04-28
Well, time isn't a very good analogy here, because software upgrades aren't uni-directional. It is possible to downgrade Ubuntu without a clean install, but that has it's risks involved with it. See [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto) for more details.

---

### Post by zuheyr on 2009-04-28
Hello,

I already found out when I upgraded from 7.10 to 8.4 (and some experienced friends on the forum confirmed) that apparently it is not a good idea to upgrade. 

This does not seem logical as the Ubuntu people prove this function that must be ok.

Could you please tell us what is it that you do not like about 9.10? What is fundamentally different?

Thanks for reading and good luck, Regards, Zuheyr

---

### Post by ch90045 on 2009-04-28
For me the reason is that i have a MacBook Pro with a x1600 ATI card - it may not be Ubuntus fault, but with this card apparently not being supported anymore by the Xserver used by Jaunty this whole thing sucks like hell.

I am desperatly looking for the downgrade.

---

### Post by Slim Odds on 2009-04-28
> **zuheyr said:**
> Could you please tell us what is it that you do not like about 9.10? What is fundamentally different?

LOL

Getting a little ahead of yourself.... 9.10 wont be out until October.

:P

---

### Post by Lunx on 2009-04-28
> **JK3mp said:**
> Yeah alot of people stick with just using LTS releases.

Being fairly new to Ubuntu, I have messed around with the latest releases (8.10 and 9.04). Now I'm over all the excitement and finally have my box set up the way I like, I'm planning on sticking with Jaunty until the next LTS release comes out. Hopefully by that stage I'll have a new system which I'll put LTS on, and then I'll use this one for trialling latest releases and other distros besides Canonical offerings.

Wonder if the original poster in this thread has a seperate home folder so that system can be changed without too much disruption?

---

### Post by Scooby1 on 2009-04-28
Note to those with x-server problems in 9.04:

I have an ati x850 using radeon driver. With 9.04 was getting x-server crashes at random with compiz enabled (screen went black for a second and then it brought me back to login screen, when logged back in all windows and everything that was open was lost) . I noticed that 9.04 now uses EXA acceleration by default. So, went into xorg.config and added this line under devices to force XAA acceleration:

[FONT=monospace]Option "AccelMethod" "XAA"[/FONT]

Now all is perfect and I couldn't be more happy with Juanty.  Seems to be a bug in the EXA acceleration with some ati cards.

---

### Post by zuheyr on 2009-04-29
> **Slim Odds said:**
> LOL

Getting a little ahead of yourself.... 9.10 wont be out until October.

:P

:-) Freud must have explained that!

---

### Post by itendo on 2009-04-30
did you receive an error to the effect that your tracker was corrupted?

check out this thread regarding corrupted trackers:
[http://ubuntuforums.org/showthread.php?t=1138029](http://ubuntuforums.org/showthread.php?t=1138029)

one of the other side effects of the two bugs leading to this results in the processor being 50-100% occupied, which may be the cause of your lag.

they have a workaround for the mess if this is the problem

---

### Post by CoraCoronel on 2009-04-30
:P Hi!
 I just read my only solution is wait a bugs fixing on this 9.04 version, so until that day my video don't really work well anymore?
My lap is a toshiba satellite A205 SP5830, intel dual core, 2 mb ram and 160 gb hard disk, so I make my desktop like Mac with AWN manager, the dock works slowly (like all in this new version!!) My only question: I don't have a solution to make more quick my computer; I mean all graphics works slowly and some times my screen goes grey...I'm really worried!! Thanks for your help...:KS

---

### Post by -=KoS=- on 2009-05-01
For me 9.04 has 2 ways. I installed it into my desktop (works great, some problems with grey songbird and not very good version of amarok. but i use xmms fro now.) and i have 9.04 into 2 notebooks. in one i have no compiz effects at all (this is very bad) and into another small problems with compiz too and problems with windows sizes. My programms windows are leger than my screen resolution.
In that case as for me :
9.04 very good system for desctops, canonical you are the best.
And for laptops 8.10 is brilliant. canonical you are still the best.

---

### Post by TomB19 on 2009-05-01
> **Slim Odds said:**
> I know some people are having "issues", but that happens every release. Most people don't have issues.

The data in this forum does not support your statement.  Current stats show just under 28% of upgraders experienced a flawless installation.

As reference:

[http://ubuntuforums.org/showthread.php?t=1133869](http://ubuntuforums.org/showthread.php?t=1133869)


For what it's worth, I experienced a flawless upgrade on an Intel IGP 32 bit system from 8.04 to 9.04 on an Intel IGP system.  That system is now extremely slow but usable.

I have no intention of rolling back to 8.04 as the new graphics are knocking my eyes out.  Also, I find a few of the new productivity features provide enough of a work flow boost as to make up for some of the performance issues.

My main desktop is running x86_64 Kubuntu 8.10.  It would be nice to have some of the cool new Plasmoids but it's an AMD IGP system (AMD 790GX / SB750) so I know the upgrade will not go well.  Another factor in the hesitation to upgrade is how brilliantly 8.10 is working.


Let's not forget how difficult the bleeding edge can be.  Look at the teething pains of Vista or, for that matter, other *major* Ubuntu releases.  9.04 brings a lot of changes and some wonderful new functionality.  Changes on this scale are not without risk.

---

### Post by Guitar John on 2009-05-02
> **JK3mp said:**
> Yeah alot of people stick with just using LTS releases.

Speaking of LTS, is the next one going to be version 10.04?  The previous was 8.04 and the 6.06 before that - which I think was released a couple of months late.  So every two years seems to be the emerging pattern.

---

### Post by ibuclaw on 2009-05-02
> **Guitar John said:**
> Speaking of LTS, is the next one going to be version 10.04?  The previous was 8.04 and the 6.06 before that - which I think was released a couple of months late.  So every two years seems to be the emerging pattern.

depending on how it all pans out, that may or may not be the plan.

Debian's next stable release is deadlined at around October 2010, so the Ubuntu LTS release may be delayed by 6 months so a proper collaboration between the two projects may occur.

As Mark suggests on his [blog]("http://www.markshuttleworth.com/")

Regards
Iain

---

### Post by Guitar John on 2009-05-04
> **tinivole said:**
> 

Debian's next stable release is deadlined at around October 2010, so the Ubuntu LTS release may be delayed by 6 months so a proper collaboration between the two projects may occur.


Thank you.  
-John

---

### Post by nm4m on 2009-05-04
Normally I would agree with hanging around a bit and see how things get fixed, but Firefox is borked here (blank screen).  All else works fine.  I seem to be one of the few having this problem, so don't know how soon it will be fixed.  I've been using opera, but Firefox integrated and interacted so well, I'm really missing it.

Looks like my options are trying a from scratch install of 9.04, or going back to 8.10 by a from scratch install.

Dave 
NM4M

---

