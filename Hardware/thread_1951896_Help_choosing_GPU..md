---
title: "Help choosing GPU."
date: 2012-04-03
forum: Hardware
---

### Post by dimmanramone on 2012-04-03
Hi all,

I'm about to buy a new GPU. So long I had an ATI 4850 but I want to upgrade it to something better. Lately I had problems with flickering with my ATI in both Unity and Gnome Shell but with the latest ATI drivers the flickering is gone but the performance sucks. Anyway I want a GPU that is working both in Unity and Gnome Shell without any problems, that I'm going to use proprietary drivers and that the price is around 200-300 USD. Any help, experience and proposal is more than welcome.

thanks in advance
/Dimmanramone

---

### Post by Ravi5kumar on 2012-04-03
Hey, You should buy nVidia graphic card. It works well both for Gnome and unity. Also nVidia has better support for Linux than ATI:guitar:. So from my point of view consider to buy a nVidia graphic cad:p!

---

### Post by Jagoly on 2012-04-03
560ti, the thing is AWESOME.
But wait a few weeks for the lower end keplar (6xx) cards to come out, and you can save some money on the already awesome value card.

---

### Post by dimmanramone on 2012-04-13
Thanks both of you for the answers, it seems that I'm going for an NVIDIA GPU, any recommendations on the brand or a specific one?
I was looking at Asus GeForce ENGTX560TI448.

/dimmanramone

---

### Post by mastablasta on 2012-04-13
> **Ravi5kumar said:**
>  Also nVidia has better support for Linux than ATI:guitar:. 
 
really? last time i checked nvidia said they will not support optimus (hybrid graphics) for linux at all while AMD is already supporting hybrid graphics.
Furthermore AMD is making drivers according to Ubuntu launch cycle. So that they are ready for the next Ubuntu release.
 
things change....

---

### Post by 0011235813 on 2012-04-13
Anyone who's ever compared nVidia drivers to AMD will tell you nVidia's are much better. Now, since you're willing to pay £130, I'd go for the nVidia GTX 560 Ti 1GB model, preferably an Asus or an EVGA model. Alternatively, you could wait for Kepler and GTX 660 Ti. If you **must** have ATI, go for 6770 in my opinion, as the new 7000 series are badly supported.

---

### Post by QIII on 2012-04-13
> **Ravi5kumar said:**
> Also nVidia has better support for Linux than ATI!

Incorrect, but the old into dies hard.

I use ATI cards with full hardware acceleration via VA-API (XvBA back end) all the time with no trouble at all.  I also use NVIDIA cards.

My only gripe with ATI right now is that they introduced the 7xxx series a step ahead of Linux support in a bumbled move.

---

### Post by QIII on 2012-04-13
> **0011235813 said:**
> Anyone who's ever compared nVidia drivers to AMD will tell you nVidia's are much better. 

Really?  The problem with an absolute statement is that a single anecdotal example to the contrary invalidates it.  I invalidate your statement.

You can't even say "most" without empirical evidence.  You may say "many".

---

### Post by 0011235813 on 2012-04-13
> **QIII said:**
> Incorrect, but the old into dies hard.

I use ATI cards with full hardware acceleration via VA-API (XvBA back end) all the time with no trouble at all.  I also use NVIDIA cards.

My only gripe with ATI right now is that they introduced the 7xxx series a step ahead of Linux support in a bumbled move.

...And nVidia cards remain fully supported! Let's face it, ATI doesn't really care about Linux. I would know, I use an ATI card, and the performance is quite suckish. It can barely decode 1080p video, and it makes a lot of flashes in Gnome 3. And no, I didn't install fglrx, I can't be bothered to install drivers every time I update the kernel.

---

### Post by QIII on 2012-04-13
If you can't be bothered to install the driver, your beef about performance is with open source developers, not AMD/ATI.  Again:  I get full hardware acceleration, including H.264 decoding, and flawless 1080p performance.

When I launch XBMC my conky shows an increase in CPU use commensurate with running any application.  When I start a video, CPU usage only increases marginally, while my conky shows a leap in GPU usage, which is what I want.  That means the GPU, rather than the CPU, is doing the heavy lifting.

What has led you to believe it is necessary to reinstall the drivers when your kernel is updated?  If you install from the repo, that happens automatically.

My performance doesn't suck.  Your experience and mine are both anecdotal and cannot be generalized.

By the way, AMD has been a member of the Linux foudation for a long time.  NVIDIA just got with the program a couple of weeks ago.

NVIDIA may jump the gun some day, too.

The Gnome issue is a known bug on the Gnome side, not the driver.

---

### Post by 23dornot23d on 2012-04-13
Whichever card you decide to go for ......

Do at least two things before you hand your money out .....

Check on google ...... 
[URL="https://www.google.co.uk/search?q=Nvidia+560ti+Ubuntu+Solved&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a"][COLOR=Blue][U][B]
Nvidia 560ti Ubuntu Solved[/B][/U][/COLOR][/URL]

[[COLOR=Blue]_**Nvidia 560ti Ubuntu Problems**_[/COLOR]]("https://www.google.co.uk/search?q=Nvidia+560ti+Ubuntu+Problems&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")


Once you are certain that the card is useable or fixable ..... only then go get one .

Getting the latest and greatest with Linux in my mind is a mistake .... the newer ones
need time to be fixed and sorted to work well with Linux in my past experience with them.

As I say check solved and problems ..... before you begin ..... if problems outnumber solutions its a small indication that the card you are choosing may not be suitable.

But read through a few threads first ..... *( as they may only be minor problems ...... )

Usually slightly older cards are already fixed for linux and work better IMHO
buying the newer ones may mean that you have to sort some problems out.

Just from what I see on the forums and I read them everyday ..... and specifically look
for graphics problems ...... people using Nvidia Cards in the past have always been
easier to fix ...... 

( that may change in the Future ...... but check the threads first )

[COLOR=Red]**If there are users with no problems with later ATI cards ..... give some specifications of the card .....**[/COLOR]

( Gnome Shell and a lot of ATI cards  ..was a big problem not so long back )

I too may change one day to ATI if they have solved all the problems with them - but
convince us  ....... will then check problems and solutions ..... for said card ....

---

### Post by 0011235813 on 2012-04-13
> **QIII said:**
> If you can't be bothered to install the driver, your beef about performance is with open source developers, not AMD/ATI.  Again:  I get full hardware acceleration, including H.264 decoding, and flawless 1080p performance.

What has led you to believe it is necessary to reinstall the drivers when your kernel is updated?  If you install from the repo, that happens automatically.

My performance doesn't suck.  Your experience and mine are both anecdotal and cannot be generalized.

By the way, AMD has been a member of the Linux foudation for a long time.  NVIDIA just got with the program a couple of weeks ago.

NVIDIA may jump the gun some day, too.

The Gnome issue is a known bug on the Gnome side, not the driver.
Well first of all, I couldn't even get the driver to install with the additional drivers application, I was merely told that the driver installation failed and that I should check a log file, which I couldn't find. 

I'll check this one to be sure, I might be out of date on this one.


I know that, but most of the benchmarks done by openbenchmarking.org and Phoronix show the closed nVidia drivers out perform the AMD ones, and of course, bot Galium and Nouveau suck. Galium doesn't even work on mine, it uses VESA.


Can you post a reference to this?

---

### Post by QIII on 2012-04-13
Here's a f'rinstance:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577)

A lot of people say NVIDIA gives better support for video acceleration out of the box with VDPAU.  There is a reason for that.  VDPAU is proprietary and they can include it in their proprietary drivers.

VDPAU doesn't belong to AMD/ATI.  Fglrx uses VA-API, which is an open, cross platform standard.  They don't include it with their drivers because their drivers are proprietary and they don't have proprietary hardware acceleration, choosing instead to leave that to an open standard like VA-API.

It takes adding just four packages from the repos to activate VA-API in Ubuntu.

Do the comparison tests you cite account for that?

If you are having trouble installing the AMD/ATI drivers, ask for help.  Some people have trouble installing NVIDIA drivers, too.

Instead of saying buy NVIDIA or buy ATI, we should be saying "Here are some places for you to look to do some research and decide what you want to do for the budget you have."

Being a fanboy apologist with someone else's money is at least fruitless and at worst arrogant.

---

### Post by QIII on 2012-04-13
> **23dornot23d said:**
> 
Just from what I see on the forums and I read them everyday ..... and specifically look
for graphics problems ...... people using Nvidia Cards in the past have always been
easier to fix ...... 

... unless I'm the guy who responds.

I'm tired of the fanboy competition.  Each company makes good, solid products.  Each makes cards in every budget range.  Each has its strengths an weaknesses.

---

### Post by 0011235813 on 2012-04-13
> **QIII said:**
> Here's a f'rinstance:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577)

A lot of people say NVIDIA gives better support for video acceleration out of the box with VDPAU.  There is a reason for that.  VDPAU is proprietary and they can include it in their proprietary drivers.

VDPAU doesn't belong to AMD/ATI.  Fglrx uses VA-API, which is an open, cross platform standard.  They don't include it with their drivers because their drivers are proprietary and they don't have proprietary hardware acceleration, choosing instead to leave that to an open standard like VA-API.

It takes adding just four packages from the repos to activate VA-API in Ubuntu.

Do the comparison tests you cite account for that?

If you are having trouble installing the AMD/ATI drivers, ask for help.  Some people have trouble installing NVIDIA drivers, too.

Instead of saying buy NVIDIA or buy ATI, we should be saying "Here are some places for you to look to do some research and decide what you want to do for the budget you have."

Being a fanboy apologist with someone else's money is at least fruitless and at worst arrogant.The problem is cited for the fglrx driver, not the VESA driver... I'm not sure if the bug applies to all ATI cards?! Because that would be quite a serious issue for ATI cards, regardless of whose fault it is.


I imagine they do, personally, I don't care much, since nVidias lower range products are quite inferior, and AMD/ATIs new 7000 series for the high end is confirmed to have bad performance under Linux, **with** their drivers.


I don't like fanboys, and I don't like ATI *or* nVidia. I wish Intel would make some discreet GPUs...

---

### Post by QIII on 2012-04-13
AMD/ATI provides the fglrx driver.

A problem with the VESA driver is a problem, but not caused by them directly.

The problem with the 7xxx series is that the fglrx driver does not work at all.  It was a serious mistake, no doubt, but not an indication that AMD/ATI doesn't care about Linux.  Don't get me wrong.  I'm outraged.  But this was a screw-up.  

Since AMD bought ATI (and ATI certainly did suck before that and that preconception still exists), ATI drivers have been timed to come out with Ubuntu releases.  Phoronix has an article every time about how the newest release of Ubuntu gets the ATI candy before anyone else.

The versions of the ATI drivers are even aligned with the Ubuntu releases when the latter is released.

12.04 is the current Beta, not available for public consumption (the one everyone else can get right now is 12.3), but found in the Precise (12.04) repository.

I'd say that indicates a commitment, wouldn't you?

NVIDIA is also committed to Linux, as demonstrated by their recent acceptance into the Linux Foundation.  The choice between NVIDIA and ATI is now largely a matter of Ford/Chevy brand loyalty and budget.  Buy the one that has the features you want and forget brand loyalty.

Intel has shown little interest in high-end graphics to date, so they are well behind the power curve.

---

### Post by 0011235813 on 2012-04-13
> **QIII said:**
> AMD/ATI provides the fglrx driver.

A problem with the VESA driver is a problem, but not caused by them directly.
If Gnome 3 has bugs with fglrx **and** VESA, then I don't really care, since it means Gnome will be annoying regardless of what driver I'm using, so no ATI...

---

### Post by QIII on 2012-04-13
> **0011235813 said:**
> If Gnome 3 has bugs with fglrx **and** VESA, then I don't really care, since it means Gnome will be annoying regardless of what driver I'm using, so no ATI...

That's fine.  However, the bug is not with fglrx, but Gnome and VESA.  Neither is under ATI's control.  The fglrx drivers work absolutely fine for me in both Kubuntu and Xubuntu -- except that Compiz effects have a bug in Xubuntu (a Compiz bug, not an fglrx) right now that keeps Compiz effects from working with fglrx.

Again:  These are Linux community-side bugs, not ATI bugs.  Don't say ATI doesn't support Linux.

As for the OP's original question:

This is all part of your research.  Consider it as you make your decision and buy appropriately.

If you want to use Gnome, be aware of the pitfalls and be aware that you might be hobbled.  Remember that the Gnome folks changed directions and they are feverishly working to make things better.  "Bug" does not mean they don't care.  It means they are human and have a lot on their plates.

---

### Post by 23dornot23d on 2012-04-13
> 
Each company makes good, solid products.  Each makes cards in every budget range.  Each has its strengths an weaknesses.
True statement .... the decision to choose one over the other ....

Depends on a few factors IMHO

a) How much support is there on linux to help people when they have problems with a
card ....

[http://ubuntuforums.org/showthread.php?t=1697185](http://ubuntuforums.org/showthread.php?t=1697185)

b) How happy the user is with the support and what they do when things seem impossible 
to resolve for them ....

[http://ubuntuforums.org/showthread.php?t=1956194](http://ubuntuforums.org/showthread.php?t=1956194)

If there is a easy fix for ATI .... it should be included by default into the Ubuntu OS
to save the USERs the problems they obviously face .....

If they are so easy to fix ..... a Help screen should pop up on installation for these
cards .......

Edit

if this is the typical answer too for the problem - then maybe it needs including in a Help Screen

> 
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

After i did this, i rebooted my system and then installed the drivers downloaded from ati site, then voilá! its working :wink:
A similar help screen too could be useful for Nvidia drivers ..... as purging and re-installing is sometimes the answer

> 
sudo apt-get update 

sudo apt-get install linux-headers-`uname -r`  

sudo apt-get remove --purge nvidia-* 

sudo apt-get install nvidia-current 

__________________________________________________  _____

  only needed if  coming from a desktop ( sudo service gdm restart )


When users load up multiple drivers ...... for their cards .... and they then find a black screen at start up

---

### Post by QIII on 2012-04-13
Now go find the NVIDIA problems.  Getting TwinView to work, for instance.

I don't care to, because I am not trying to say NVIDIA is a bad product.

What you find here is anecdotal.  People do not come to help forums looking for help when things work.  They come here when they don't.  

It is easy to assume that problems are universal when you find a bunch of problems on a help forum.  However, that assessment suffers from referral bias, rendering any conclusions drawn from the frequency of the issues invalid.

When a TV political pundit has a survey on what "everyone thinks", he is going to get a biased sample based on the viewer demographic.  That sample will tend to reflect the pundit's point of view because most of those who watch his show agree with it.

Help forums reflect problems instances.  They do not necessarily reflect the experience of the overall population.

Edit:  After reading your edit, I would agree that perhaps BOTH OEMs and purveyors of Distros could make that process easier.  It's a matter of expense, though.  Many users do not understand that the other OEM's drivers need to be removed, either.  Additionally, many Ubuntu users do not understand the wisdom of removing all third party drivers when updating to a new version instead of a clean installation.

I'm out.  I think we gave the OP a pretty good bit of info (if he's still around after two weeks) to chew on.  We needn't drag this on any further.

---

### Post by Jagoly on 2012-04-14
My 560ti works a hell of a lot better than my 5650 ever did in ubuntu. the 5650m had problems with most things I needed it to do, mainly oblivion and skyrim in wine, and minecraft. Problem after problem after problem. My 560ti does everything, and EASILY.

a better comparison would be my new laptop. my old laptop, with a 5650m, had problems with any less than standerd game (wine and minecraft). my new laptop, with a 525m, which is technically a slower card (in windows benchmarks), is at least 3 times quicker in those games. and no, the cpu in my old laptop was not the problem.

I could go into more technical detail, but I'm just decribing my experiences from a simple end users point of view. Nvidia cards are alot less hassle in ubuntu than those from amd/ati.

---

### Post by dimmanramone on 2012-04-16
Unfortunately it seems that my thread became a drivers/brands competition or whatever you want to call it.

From the things that I've read in my thread and read before in other threads is that older GPU has better support. I had NVIDIA before my ATI so I have a little experience that none of them are problem free. Both have disadvantages and advantages with the drivers etc and will have.

So mainly my question was which card should I buy from your experience, like: I have an NVIDIA 560ti using gnome and unity, have good performance and don't have any problems or I have the following problems with the latest drivers.

/dimmanramone

---

### Post by Yellow Pasque on 2012-04-16
> **dimmanramone said:**
> Unfortunately it seems that my thread became a drivers/brands competition or whatever you want to call it.
You act surprised..

---

### Post by dimmanramone on 2012-04-16
> **Temüjin said:**
> You act surprised..

Not really :) but I'm trying to get back to the topic.

---

### Post by QIII on 2012-04-16
Both ATI and NVIDIA are good products.  Each has its pluses and minuses.

I would spend some time on phoronix.com reading through their reviews.  They don't pull punches and I have found their reviews to be objective.

Just be aware that the "ATI doesn't support Linux" meme is a lingering legacy of the days before ATI was bought by AMD, before which time ATI support was definitely poor.  I'm not trying to sell ATI so much as put old news to rest.

---

### Post by 0011235813 on 2012-04-16
Oh bother, GPUs are always so complicated, with CPUs it's simple:
Cores& Transistors, Core clock& Turbos (if available), cache and cache types (i.e L2 or L3), die process, power consumption and that's about it. But GPUs! Oh no, we have to deal with VRAM, core clock, memory clock, shader clock, stream processors, shader processors, bus, ROPs, SIMDs, CUDA on nVidia....
The closest I've come to is this:
Low end video viewing etc. I would recommend AMD 5830. Or go for GTS450, it's slightly more expensive, but gives you more brawn, and in a cool and quiet package that doesn't cost too much PSU power. The GT430 is rubbish.
Mid end gaming etc. If you want playable fps at 1920*1080p, GTX 550 Ti is a good way to go, as it offers better AA than 5770. A bit more power, and GTX 560 Ti or 6770 are good ways to go.
High end gaming and video editing etc. The king of GPUs is GTX 680 no doubt. 7000 series is badly supported and the 6000 series is inferior. Although the GTX580 remains a good card. Or maybe a bit lower end for the GTX570. 6990 ain't bad, but nVidias more efficient architecture gives lower power consumption and more features with VSync or whatever they call it.

Ultra high end- this doesn't concern anyone here, this is reserved for Scientists needing to run climate models (why don't you just use the Uni's supercomputer?) or Doctors needing 3D rendering. Obviously, Quaddro is very popular, although I hear the AMD version is good too.

---

### Post by Jagoly on 2012-04-16
> **0011235813 said:**
> Oh bother, GPUs are always so complicated, with CPUs it's simple:
Cores& Transistors, Core clock& Turbos (if available), cache and cache types (i.e L2 or L3), die process, power consumption and that's about it. But GPUs! Oh no, we have to deal with VRAM, core clock, memory clock, shader clock, stream processors, shader processors, bus, ROPs, SIMDs, CUDA on nVidia....
The closest I've come to is this:
Low end video viewing etc. I would recommend AMD 5830. Or go for GTS450, it's slightly more expensive, but gives you more brawn, and in a cool and quiet package that doesn't cost too much PSU power. The GT430 is rubbish.
Mid end gaming etc. If you want playable fps at 1920*1080p, GTX 550 Ti is a good way to go, as it offers better AA than 5770. A bit more power, and GTX 560 Ti or 6770 are good ways to go.
High end gaming and video editing etc. The king of GPUs is GTX 680 no doubt. 7000 series is badly supported and the 6000 series is inferior. Although the GTX580 remains a good card. Or maybe a bit lower end for the GTX570. 6990 ain't bad, but nVidias more efficient architecture gives lower power consumption and more features with VSync or whatever they call it.

Ultra high end- this doesn't concern anyone here, this is reserved for Scientists needing to run climate models (why don't you just use the Uni's supercomputer?) or Doctors needing 3D rendering. Obviously, Quaddro is very popular, although I hear the AMD version is good too.

The 6770 is NOT anywhere near the 560ti. The AMD counterpart for the 560ti is the 6950.

@OP: Yes, I have a 560ti. Also note that the 560ti and 560ti 448 are different cards. The 448 is actually a lower-binned 570. In linux, where overclocking nvidia fermi/keplar cards is unsupported, I'd reccomend a heavily OC'd 560ti (non 448). Such as the MSI Twin Frozr 3 Hawk. Which I have, And have had absolutely no problems with whatsoever. I use the xorg-edgers ppa, and it's flawless on both 11.10 and 12.04 beta.

---

### Post by 0011235813 on 2012-04-17
> **Jagoly said:**
> The 6770 is NOT anywhere near the 560ti. The AMD counterpart for the 560ti is the 6950.

@OP: Yes, I have a 560ti. Also note that the 560ti and 560ti 448 are different cards. The 448 is actually a lower-binned 570. In linux, where overclocking nvidia fermi/keplar cards is unsupported, I'd reccomend a heavily OC'd 560ti (non 448). Such as the MSI Twin Frozr 3 Hawk. Which I have, And have had absolutely no problems with whatsoever. I use the xorg-edgers ppa, and it's flawless on both 11.10 and 12.04 beta.

Well the nVidia card is cooler, quieter and offers relatively equal performance at relatively equal prices with pretty much the same power consumption. I wouldn't call that an overwhelming victory for nVidia, but I agree the card **is** [superior]("http://www.guru3d.com/article/radeon-hd-6950-1gb-vs-geforce-gtx-560-ti-review/1").

---

### Post by Dlambert on 2012-04-17
I also have no problems with my ASUS GTX 560 Ti TOP (Overclocked) edition card.

---

### Post by dimmanramone on 2012-04-19
Thx everyone for your answers, it seems that people with NVIDIA 560 TI doesn't have problems and they are satisfied with the performance. And if I would go for an ATI the Radeon HD 6950 should be one of my choices. 

Still I haven't decided yet if I'm going for ATI or NVIDIA but when I decide and install my new GPU I'll report with the results.

/dimmanramone

---

