---
title: "AGP Video card to support 12.04 Precise?"
date: 2012-05-05
forum: Hardware
---

### Post by momist on 2012-05-05
Hi everyone,

It seems my Nvidia FX5200 card is no longer good enough for Ubuntu.  I'm currently stuck in Unity 2D and would really like to try out the new 3D facilities.

Current specs are:
```
Computer
Processor	2x AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
Memory	2051MB (1537MB used)

Display
Resolution	1280x1024 pixels
OpenGL Renderer	Unknown
X11 Vendor	The X.Org Foundation

Version
Kernel	Linux 3.2.0-24-generic (x86_64)
Compiled	#37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012
C Library	Unknown
Default C Compiler	GNU C Compiler version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5)
Distribution	Ubuntu 12.04 LTS

Display
Resolution	1280x1024 pixels
Vendor	The X.Org Foundation
Version	1.11.3
Monitors
Monitor 0	1280x1024 pixels

OpenGL
Vendor	Unknown
Renderer	Unknown
Version	Unknown
Direct Rendering	No

VGA compatible controller	NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA controller])

nouveau	nVidia Riva/TNT/GeForce
```

I really like the no-fan quietness of my 128MB video card, and would like to replace it with something similar or better, but supported by Ubuntu.  AGP, DVI to suit my motherboard.

Can anyone suggest a suitable card I might get for a decent price on eBay?

Thanks,
Ian

---

### Post by kurt18947 on 2012-05-05
Here's a list of currently supported Nvidia chipsets:

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

A cursory search of AGP cards shows the newest Nvidia AGP cards have Geforce 6200 chipsets.  ATI's linux support for older cards doesn't have an enviable reputation though i have no firsthand experience with newer ATI.  The 6200 chipset is currently supported by Nvidia but I don't know what features are supported.

---

### Post by momist on 2012-05-05
> **kurt18947 said:**
> Here's a list of currently supported Nvidia chipsets:
<snip>
 The 6200 chipset is currently supported by Nvidia but I don't know what features are supported.

Many thanks for that, just what I was looking for.  Other than Nvidia and ATI is there any other choice I should consider?  Indeed, are there any others at all?

I have just missed an FX 6200 on eBay, pity.  I'll keep looking.

---

### Post by kurt18947 on 2012-05-05
> **momist said:**
> Many thanks for that, just what I was looking for.  Other than Nvidia and ATI is there any other choice I should consider?  Indeed, are there any others at all?

I have just missed an FX 6200 on eBay, pity.  I'll keep looking.

The only other graphics chip vendor I'd consider would be Intel but for whatever reason I don't recall ever seeing an Intel video card.  Every Intel video setup has been part of the MoBo.

---

### Post by mips on 2012-05-05
The current drivers (295.xx +) support the **Geforce** 6xxx and up.

When it comes AGP your options stretch as far as the Geforce 7xxx series cards, beyond that it's all PCIe.

Your best bet is the 66xx-68xx & 76xx-78xx GT/GTX cards. The higher the second digit the better the performance. I would not consider anything with a second digit lower than 6, ideally you want to go for a 8.

New these cards are expensive so I suggest you shop around for second hand. I got a 7600GT for free the other day but it was PCIe.

---

### Post by momist on 2012-05-05
> **mips said:**
> 
I would not consider anything with a second digit lower than 6, ideally you want to go for a 8.

Thanks for clarifying the limits on AGP.  I've not yet looked beyond 6200, not being aware that I could go higher.  I'll go looking now though. :)

Edit:  They all seem to have those noisy fan things attached though!  Also; this is confusing.  Aren't the SP 6900 GeForce2 MX 64MB AGP4 cards actually older and slower than the 6200 GeForce 256MB cards?  What a crazy numbering system this is.

---

### Post by mips on 2012-05-05
> **momist said:**
> Thanks for clarifying the limits on AGP.  I've not yet looked beyond 6200, not being aware that I could go higher.  I'll go looking now though. :)

Edit:  They all seem to have those noisy fan things attached though!  Also; this is confusing.  Aren't the SP 6900 GeForce2 MX 64MB AGP4 cards actually older and slower than the 6200 GeForce 256MB cards?  What a crazy numbering system this is.

As suggested in that other thread also look at those GT430 & GT520 cards. I know a lot of people use them in their home theatre PCs due to many of them not having noisy fans. You get in in both versions.

---

### Post by momist on 2012-05-05
Thanks mips.  There's a GeForce 6200 card on its way, won on eBay.uk for less than a tenner that I'll give a try.  If I'm not happy with that, I'll look for the GT430/GT520 cards.  There are no used ones on there just now.

BTW did I hear your avatar is worth a lot of money?  :)

---

### Post by mips on 2012-05-05
> **momist said:**
> 
BTW did I hear your avatar is worth a lot of money?  :)

Also heard that, apparently about US$120 million. 

Anyone here wanna buy my avatar? :biggrin:

---

### Post by Yellow Pasque on 2012-05-05
Not sure why you bought a new card. Nvidia just needs to update its drivers for use with modern kernel/Xorg.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053)

---

### Post by momist on 2012-05-06
> **Temüjin said:**
> Not sure why you bought a new card. Nvidia just needs to update its drivers for use with modern kernel/Xorg.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053)

From your link:

"We're working on new ABI support for legacy branches right now; we're very sorry for the delays, we've been very busy with other stuff."

"Ubuntu can't fix this, nvidia should do that."

"In Natty the 96 package never got updated post-release even when nvidia released compatible driver."

So will they release a fix for this?  I'm not sure how old my video card actually is, since I bought it used to solve a similar issue about three years ago, but reviews indicate it dates from 2003.  So, nine years old technology, a limited number of Linux users, what's the pressure?  Call me cynical, but nVidia are there to sell new ones, preferably to those who spend megabucks on gaming.

Anyway, I view the continual messing about with my PC as a hobby, and the expenditure on used kit is not very high.  This is _much_ cheaper than, say, golf, or my other hobby, sailing.

The card in the post (I hope) has 256MB on board memory, which I think is double my current hardware, so that might mean a slight improvement.  Someone else suggested that Unity needs a minimum of 500MB, so maybe the replacement won't work for me.  All the 512MB cards seem to have DDR2 memory, I'm not clear if that comes with it's own controller, because my MB would not recognise such advanced stuff.  I know that some day soon I will have to do the big upgrade again with new MB, processor, memory, etc.  The longer I can put that off, the bigger the jump I will then make, and probably the more it will cost.  Maybe my birthday present next year?

---

### Post by kurt18947 on 2012-05-06
> **mips said:**
> As suggested in that other thread also look at those GT430 & GT520 cards. I know a lot of people use them in their home theatre PCs due to many of them not having noisy fans. You get in in both versions.

Not that will fit an AGP slot though, I think.

---

### Post by mips on 2012-05-06
> **kurt18947 said:**
> Not that will fit an AGP slot though, I think.

They make PCI versions of those particular cards which will fit in most computers and when I say PCI I don't mean PCIe.
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853%20600030348%20600007321&IsNodeId=1&name=GeForce%20G%2fGT%20series](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853%20600030348%20600007321&IsNodeId=1&name=GeForce%20G%2fGT%20series)

---

### Post by kurt18947 on 2012-05-07
> **mips said:**
> They make PCI versions of those particular cards which will fit in most computers and when I say PCI I don't mean PCIe.
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853%20600030348%20600007321&IsNodeId=1&name=GeForce%20G%2fGT%20series](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853%20600030348%20600007321&IsNodeId=1&name=GeForce%20G%2fGT%20series)

Those should work, uncommon beasties though.  I wonder how much the lower throughput of the PCI bus affects video performance.

---

### Post by mips on 2012-05-07
> **kurt18947 said:**
> I wonder how much the lower throughput of the PCI bus affects video performance.

No idea, the fastest PCI bus rate is 1/4 of the fastest AGP bus rate.

I do however know a lot of people use these cards in their HTPC setups for playing back full HD accelerated video.

---

### Post by momist on 2012-05-10
OK.  My new old 6200 AGP 256MB card arrived today, and I thumbed it straight in.  It worked straight off the bat, still using the nouveau driver, and immediately gave me Unity 3D.  Also, my slow old 2GHz dual core machine with 2GB DDR memory runs considerably faster and a lot quieter.  It seems the processor was working very hard to cover the failings of the old video card.  :P

I loaded the nvidia driver (recommended) and away we go - but there's a problem.  Scrolling web pages with frames causes the frames to overlap and destroy the content.  Scrolling pages with lines of text causes the text lines to overlap and destroy the content.  The effect sticks, in that once corrupted, the overlap moves up and down the screen as you scroll.

So, try the "version current-updates" driver instead.  Ah, that's better.  The corruption still happens, but it goes away after a second or two.

Better is still not good enough.  Is this down to Unity, or is something else going on?  Time for some drastic action.

I've put dual boot Lubuntu on my windows laptop (Dell D630), which I need for legacy software not available in Linux, and it really flies!  The menu system works for me, and I find I'm preferring it to Unity even if I disregard the extra speed and snappiness.  So I think I'll give the live CD a go on here, and see if the video problems still occur with this hardware.

I'll let you all know how things go.   ):P

---

### Post by mips on 2012-05-10
Try the latest 295.49 nvidia drivers ;)

---

### Post by SeijiSensei on 2012-05-10
If you're using Firefox, you can try changing the "smooth scrolling" mode in Edit > Preferences > Advanced.  Maybe that would help.

---

### Post by momist on 2012-05-10
Thanks SeijiSensei, I had totally forgotten about that setting.  Yes, that helps, in that it prevents the corruption.  However, the "smooth" scrolling seems to be delayed and rather jerky, albeit in small jumps rather than the usual big ones.  It's as if the machine is thinking "how do I do the next bit?" at intervals, so the incremental jumps are at random intervals.  Most disconcerting.

@mips, I'll have a go with that, but not tonight as it's late and I've had a bottle of beer  :grin:   
Thanks for the suggestion.

---

### Post by momist on 2012-05-14
This is interesting (at least to me).  ;)

I never did get around to trying the alternative driver 295.49 kindly suggested by mips.  I have been playing around with alternative desktops and systems on my old laptop before committing to a big change in my main desktop PC.

Having become undecided, I tried a couple of live sessions on the PC and then today loaded XFCE and KDE desktops on top of Ubuntu.  The process was much longer and more comprehensive than I imagined it would be, and loaded an enormous amount of new packages.

On final reboot, I'm met by the XFCE splash screen, and a drop down menu offering the new desktops and also the usual Gnome, Unity 2D, Unity 3D.  Wondering which of these was the default, I just entered my passward and hit return.  As expected this put me straight back into Unity 3D, but with a new error.  I now have to enter my password again, in order for the gnome keyring to be unlocked.  The second big change was that I was immediately met with a dialogue saying updates are available, which I naturally agreed to get, thinking that the new desktop packages maybe needed updates.

Among the many updates this installed, was a new Nvidea version current updates.  Is this simply coincidence? Or was my machine NOT getting the updates prior to loading the new repositories to get the alternative desktops?  With the new video driver running, the speed of the machine is now much faster than it was.  Not fast, compared to Ubuntu 10.04 I ran on a slower Geforce 4 video card, but less laggy and without the disconcerting screen corruptions I was getting.  :p

Getting curious, I thought I would look at what repositories I have got enabled now, but in standard Unity 3D Ubuntu I can see no graphical way of achieving this, unless you count the drop down menu at the top of the Ubuntu Software Centre, which includes the names of some of the "foreign" repositories I have added by command line.  For those of us not confident with the command line and terminal, this is a bit blinding.  I'd love to know if the updates were enabled prior to adding the Xbuntu and Kubuntu desktops.

I'm still not happy with the slowness of Unity 3D on my machine, and will migrate to some alternative.  I'm currently favouring Lubuntu for its sheer speed, and it seems I can still install my favourite packages, even the "heavy" ones, without too much detriment to that. I also like the transparency of the menu-driven desktop, and it feels like Lubuntu is not hiding stuff the way Unity feels.  Also, I don't have to remember the name of something to go find it, I just look for it.  :)

---

### Post by MrKappa on 2012-05-18
Hello',
I'm searching a decent agp video card too. I was using an old ATI Fury Pro and it was running fine until Ubuntu 9.04. 
Then I had to updgrade it to 12.04 (Xubuntu) recently and I see that, even if I get a normal screen resolution, I cannot watch decently any video content from internet from firefox or chrome both even flash or html5.
I suppose that kernel is the main reason and I have tried to a newer ATI with 512 Mb memory having the same issue.
I cannot install alternative drivers so far. Considering that I like to upgrade to another AGP card with DVI output, do you recommmend a card model which is running fine with internet videos on Ubuntu 12.04?

---

### Post by momist on 2012-05-19
@ MrKappa, Hi. 

I do not have any experience to help you, except of the one card I've recently bought very cheaply off eBay, just to run Unity.  This is an nVidia GeForce 6200.  My choice of video card is restricted by both the motherboard which offers only PCI or AGP, and by my very strong preference for a video card which does not have a fan.  I like an almost silent PC, and there are enough fans in there already without adding more.  My processor has a 5" slow turning fan with speed controlled by the motherboard, and the power supply has manual fan speed control turned down to the lowest speed I can get away with.

The nVidea 6200 card will run Ubuntu Unity 3D on my machine, but the whole system is very slow, and I simply could not tolerate the waiting time and the wondering about what it was doing that slowed it down so much.  I have changed to Lubuntu, which I'm also dissatisfied with.  Lubuntu is very fast, and I've no complaints there, but there seems to be so much missing, both bling and tools, that I'm thinking of trying something else.  Even grep doesn't work in Lubuntu - why?!

I've been running plain Ubuntu now on and off, since Warty Warthog, whatever year that was in, and with an occasional dip into Kubuntu.  At first I was dual booting with Windows98 and later with WindowsXP, but since about Hardy Heron I've used nothing but Ubuntu on my main machine.  This is the first release that has caused me such pain.


Sorry to be so negative, but I can't offer a good solution.

Ian

---

### Post by MrKappa on 2012-05-19
> **momist said:**
> @ MrKappa, Hi. 

I do not have any experience to help you, except of the one card I've recently bought very cheaply off eBay, just to run Unity.  This is an nVidia GeForce 6200.  My choice of video card is restricted by both the motherboard which offers only PCI or AGP, and by my very strong preference for a video card which does not have a fan.  I like an almost silent PC, and there are enough fans in there already without adding more.  My processor has a 5" slow turning fan with speed controlled by the motherboard, and the power supply has manual fan speed control turned down to the lowest speed I can get away with.

The nVidea 6200 card will run Ubuntu Unity 3D on my machine, but the whole system is very slow, and I simply could not tolerate the waiting time and the wondering about what it was doing that slowed it down so much.  I have changed to Lubuntu, which I'm also dissatisfied with.  Lubuntu is very fast, and I've no complaints there, but there seems to be so much missing, both bling and tools, that I'm thinking of trying something else.  Even grep doesn't work in Lubuntu - why?!

I've been running plain Ubuntu now on and off, since Warty Warthog, whatever year that was in, and with an occasional dip into Kubuntu.  At first I was dual booting with Windows98 and later with WindowsXP, but since about Hardy Heron I've used nothing but Ubuntu on my main machine.  This is the first release that has caused me such pain.


Sorry to be so negative, but I can't offer a good solution.

Ian

Hello' Ian,

many thanks for your reply. I had the same experience because older Ubuntu versions was better for the compatibility point of view. Something has changed on kernel level and perhaps it require more time for us to find the proper drivers/kernel or flash version.
But except the slowness with Unity 3D what about watching video from internet? Could you compare if you see difference watching video using flash and video with html5 of course in low resolution? 
I have tried with xfce desktop, perhaps you can see if you like it or is better for you then lubuntu version for options, menu etc.

---

### Post by momist on 2012-05-19
One of the first things I do is install Flash.  My system reports from the Flash test site:
"You have version 11,2,202,235 installed"
and I've just been watching some of the America's Cup at:
[http://www.youtube.com/americascup](http://www.youtube.com/americascup)
I do know that some sites give me a flash error:  Error# 2046, but this is a rare occurrance, although I'd love to know what causes it.  Those sites worked fine with Gnash before I installed Flash.

I'm not familiar with html5, and don't know which sites use it.  Maybe you could send me a link to test?  

BTW I'm using Firefox, although the LXDE that comes with Lubuntu has Chromium (open source version of Google's Chrome) as the default.  The Flash performance appears the same in both.

---

### Post by momist on 2012-05-19
OK, I found an html5 test facility from Wikipedia links.  Yes it works, but that is SO slow, it's almost unusable.  

html5test.com reports 345 out of 500, so I suppose that's not so bad, but the game I tried (bouncy something) ran too slowly to be called a game.

Edit: that was in Firefox.  Chromium reports 400/500.

Hope that helps.

---

### Post by MrKappa on 2012-05-20
Many thank for sharing your experience.

---

### Post by Skara Brae on 2012-05-20
Hello fellow AGP owners,

I thought I was the only one left :)

My AOPen "Aeolus" Geforce 6600GT runs fine in Ubuntu 10.04 and in Xubuntu 10.04 (and in XP Home, but we don't want to bring that up here, do we?). I replaced the cheap stock cooling fan with a Zalman VF700-Cu (which is a tiny bit of work, but easier than it may sound).

Next to xfce, I have Fluxbox installed. I have never had a faster OS than Xubuntu-and-Fluxbox! If you really don't need things to look nice, then I can recommend Fluxbox.

---

### Post by momist on 2012-05-20
> **Skara Brae said:**
> Hello fellow AGP owners,

I thought I was the only one left :)



Hi, I'm willing to bet there are more than are keen to admit it.  Your PC spec is not too different to mine, I'm on Asus A8V MB as well, and I've repeatedly tried to upgrade to 4GB of ram without success, it always makes the system unstable.

Back on the subject, my Ubuntu 10.04 ran without many problems at all, it was only moving to the next LTS release that broke things.  I've been playing with Mint 13 live CD with Cinnamon, and so far it all seems good.  I'll report back when the stable release comes out and I've tried it fully installed.

Ian

---

### Post by MrKappa on 2012-05-20
> **momist said:**
> Hi, I'm willing to bet here are more than are keen to admit it.  Your PC spec is not too different to mine, I'm on Asus A8V MB as well, and I've repeatedly tried to upgrade to 4GB of ram without success, it always makes the system unstable.

Back on the subject, my Ubuntu 10.04 ran without many problems at all, it was only moving to the next LTS release that broke things.  I've been playing with Mint 13 live CD with Cinnamon, and so far it all seems good.  I'll report back when the stable release comes out and I've tried it fully installed.

Ian

I'm not the expert but it seems that the problems for us are starting from Ubuntu 11.10 which I have tested shortly and I have the same problems as latest release. So 9.10 or 10.04 is ok. Not sure about Ubuntu 10.10 version
Of course we might need to stay with a recent Ubuntu to not miss all upgrades on firefox, libreoffice etc. 
For both major OEM (ATI, Nvidia) I see that official driver on the repository seesm to be not optimized for internet videos and the alternative drivers which are difficult to install due to dependency to other files and kernel issues.
I hope some other user can post here instead a positive experience with Ubuntu 12.04 and some good video card that does not suffer these issues.

@Ian: I have tested Linux Mint too but basically seems to be another flavour of Ubuntu 12.04 (same repository for most of the software for my understanding)

---

### Post by Bartender on 2012-05-20
> **MrKappa said:**
> @Ian: I have tested Linux Mint too but basically seems to be another flavour of Ubuntu 12.04 (same repository for most of the software for my understanding)

Yes, that is correct.  The Mint folks include proprietary drivers, and an alternative to Unity, but if there's some underlying glitch in Ubuntu that's giving you fits chances are good that it will present itself in Mint too.

I've got a 2006 vintage Acer 5920 Centrino laptop.  I installed 12.04 a few weeks ago.  The onboard Intel chipset is running Ubuntu 3D.  I checked a coupla different ways and both methods indicate Unity 3D.  This lappy has hosted several versions of Ubuntu.  I haven't run any tests, but subjectively speaking Unity 3D doesn't seem to be dragging it down.

What I'm trying to say is, are you SURE that it's the video card?  I'm wondering if there's some other weird incompatibility.  Or maybe there's a hardware problem that's completely unrelated to the OS?  Bulging capacitors, heatsink making poor connection, etc.?

---

### Post by MrKappa on 2012-05-21
Many thanks for the suggestion. This is something to consider even if I'm mostly considering the software uncompatibility. 
Personally what I did was to upgrade a pc from Ubuntu 9.04, where I had no issue watching internet videos, to Ubuntu 12.04.
I understand that the CPU is not a fast one (Athlon XP 2400) but it was running fine. I got all these problems after the upgrade.
In general the pc is running normally as before for most of the operations except watching internet videos.
To confirm what you mention (hardware issue) I would re-install the old Ubuntu 9.04 but it's maybe not possible as the repository maybe cannot be used anymore. 
The most feasibe test possibly I can do is to install an AGP video card which some user can report to work fine; and hopefully I should find the same compatible model in the used market.
I will contact some use on this thread here for this:
[http://ubuntuforums.org/showthread.php?t=361236](http://ubuntuforums.org/showthread.php?t=361236)

---

### Post by momist on 2012-05-21
@MrKappa,

Why don't you simply install Ubuntu 10.04 which is still a long term support edition (LTS)?  The repositories are all still maintained, and there is support until April next year, by which time you might have either new hardware or the video drivers will have been sorted out in 12.04.  I'm confident that the drivers in 10.04 are not different than those in 9.04.

Ian

---

### Post by momist on 2012-05-25
Well,  after quite a few days of trying various things, I have now settled on using the new Linux Mint 13 Maya with Cinnamon desktop, and using the Neuveau driver.  I believe there are still issues with the nVidia drivers for my new/old card.

I suppose I could have put Cinnamon onto plain Ubuntu 12.04, but I'm ha[p[y with Mint now, and it's quick enough for what I want to do, while so far I've had no issues and found everything "just works" like it was supposed to in Ubuntu.

I'll leave it there now.:D

---

### Post by MrKappa on 2012-05-26
I found this link, it seems that Nvidia has released some drivers that should be compatible with Ubuntu 12.04 hopefully.

[http://www.nvnews.net/vbulletin/showthread.php?p=2557225](http://www.nvnews.net/vbulletin/showthread.php?p=2557225)

Hello' momist, 
in the list of supported cards I see also your card.

---

### Post by momist on 2012-05-26
Thanks MrKappa,  that one had slipped by me. I'll give it a try when I've more time to think about it.

 I'll be out of touch for a while as I learned a few hours ago that I have just become a grandad!  :D

---

### Post by MrKappa on 2012-05-26
> **momist said:**
> 
 I'll be out of touch for a while as I learned a few hours ago that I have just become a grandad!  :D

Congratulation!!!

---

