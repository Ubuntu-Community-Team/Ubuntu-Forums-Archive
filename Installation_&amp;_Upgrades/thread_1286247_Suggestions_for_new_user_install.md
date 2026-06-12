---
title: "Suggestions for new user install"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by borahshadow on 2009-10-08
Hi, a relative of mine just asked me to install linux on his computer. I use Kubuntu and have a server running ubuntu server edition. I consider myself an advanced/experienced user. 

I think that the reason that he wants me to install Linux on his computer is that he is tired of Windows making his computer slow and probably other minor complaints that just built up until the camel's back broke. As such I want to make sure that I install it in such a way that it is the best possible experience for him and so that is where my questions come from. I told him that I would probably wait for karmic to come out so that he has the newest and does not have a release that is 5 months old from the start.

First the things that he told me his computer will mostly be used for. A pretty basic but common list.
[LIST]
[*]Internet (email, blogs, etc)
[*]Office Suite. He Ok'd Open Office "as long as it is compatible" I explained that there would be a small learning curve but, worst case scenario I persuade him to buy crossover to run Office 2007
[*]Pictures
[*]He didn't tell me this but I think I remember that he needs to vpn from time to time.
[/LIST]
He has a Pentium D processor. Should I install 64-bit? I have not kept up on the debate recently. How is gnash coming along? what about Flash 10 Beta or whatever? Java? any other issues that 64 might cause that I should watch out for?

Kubuntu or Ubuntu? I use Kubuntu so that is what I am most familiar with if he needs help but I think I could help with gnome just fine if I needed to. I used to hear that Kubuntu was more Windows user friendly but IMO KDE 4 probably changed that.

Install Karmic or Jaunty? I think I mostly already decided this but if anybody knows of any known issues with karmic that might be a stumbling block this would be a good time to point them out.

Best VPN and Remote Desktop solutions? I guess it needs PPTP support I think that is what windows has built in and he used XP's built in VPN support I think.

Keep his Windows partition? I originally figured that I would keep his Windows as a dual boot but I just remembered the pain that resizing partitions can be. I suppose I could reinstall Windows on a small partition and then install Ubuntu.

One other thing... I recently convinced him (didn't take much prodding he was vary easily convinced) to install Folding @ Home on his computer. Before I got a chance to install it under Windows he decided that he wanted Linux. Should I install it right off the bat or should I wait until he is used to his new system? I have it on my computer and I don't notice much slowdown (I seem to notice a little but it might not be Folding) but results could vary.

Any other suggestions to make a new users experience as smooth as possible.

Thank You.

---

### Post by zvacet on 2009-10-09
Choosing between 32 and 64 bit version depends of ram not processor.If your friend have less then 4GB of ram then 32 bit.Karmic is still beta so I would go for Jaunty and possible upgrade later (end of November let say).

>  I originally figured that I would keep his Windows as a dual boot but I just remembered the pain that resizing partitions can be.

Download [Gparted live CD]("http://gparted.sourceforge.net/") and resize Windows partition with it and then install Ubuntu.

---

### Post by borahshadow on 2009-10-10
I know that for the most part 64 bit is determined by ram but I just said that his processor was capable of 64-bit. Correct me if I am wrong but even with less than 4GB of ram I thought 64 bit was supposed to be a little faster.

Well I was just going to wait until Karmic comes out unless you convince me I should wait until some updates start rolling out for Karmic (November) . He does not want me to install it for about 2 weeks and by then Karmic is just about 1 week away.

I guess I will try to resize the windows partition. I just remember the last time I tried that it was a bit of a pain.

Thanks for the reply.

Ps. I just realized another benifit of waiting for Karmic rather than upgrading from Jaunty is that then it will have Grub 2 and I won't have to go through the attempt of upgrading that(or not).

---

### Post by jeremyswalker on 2009-10-10
On your Ubuntu vs Kubuntu question, I think this is largely user preference. So, it would be which one you think your friend would prefer. Personally, I am not a fan of kde4. I was ok with kde3, but I'm a Gnome guy.

As far as 32-bit vs 64-bit goes, I think I would install 32-bit. This is mainly because it is for a new user. I have had both 64-bit and 32-bit on my desktop, and I noticed more problems on the 64-bit (i.e. flash). My opinion.

---

### Post by QIII on 2009-10-10
> **zvacet said:**
> Choosing between 32 and 64 bit version depends of ram not processor.

Not exactly.

64 bit machine architecture (that is a 64 bit processor) is required to run a 64 bit OS.  

You may run a 32 bit OS on a 64 bit processor, but you cannot run a 64 bit OS on a 32 bit processor.

But that point is moot, since the processor is 64 bit.

The 32 bit version is limited to addressing roughly 4GB.  In practical terms, however, you will be limited to around 3.25GB due to other considerations.

The 64 bit version can address 16EB (in theory), which is a fantastically large number.

There is no reason to limit yourself to a 32 bit OS simply because you have only 4GB of memory.  A 64 bit OS has the advantage of much more efficient processing, even when limited to a relatively small amount of RAM.

There is no reason, given 64 bit architecture, not to use a 64 bit OS.  There are 64 bit versions of nearly everything out there now, because that is the direction of the industry.

Edit:  64 bit Flash is available and I use it.

---

### Post by jeremyswalker on 2009-10-10
> **QIII said:**
> Edit:  64 bit Flash is available and I use it.

Yeah, it wasn't available the last time I used 64 bit. Thinking back, that may have been the only *real* issue I had running 64 bit. How is it? Is it comparable to flash on 32 bit?

---

### Post by QIII on 2009-10-10
Substantially better.

However, installing it at this point may be beyond the OP's skill if he is new.

The 32 bit version works passably in the 64 bit OS.

---

### Post by borahshadow on 2009-10-10
No it is not beyond my ability. I'm just asking questions about the best optio(s) for a new user that asked me to install Ubuntu for them.

It sounds like currently I am leaning towards showing him Gnome and KDE4 and let him choose. Useing 64-bit, waiting for Karmic, and resizeing his Windows partition.

Do you happen to have a link to a 64-bit Flash guide/download page?
Is there anything besides flash that sometimes could be a problem to *some *users with 64-bit.

---

### Post by QIII on 2009-10-10
You may want to locate all the instances of libflashplayer.so.

The basic idea is here, but you will have to take a look at what the correct current version (it's an Alpha of a new version) is, and replace the tar file he downloads with the current one.


[http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/01/how-to-install-flash-64-bit-on-ubuntu-jaunty-904/)

---

### Post by jeremyswalker on 2009-10-10
Here is a link to Adobe Labs with the current version of 64 bit flash.
[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

---

### Post by QIII on 2009-10-10
Correct.

10.0.32.18, I think.  That's the last I updated to.

I happened also to think that you might want to put the .so in

/home/whatever/.mozilla/plugins

depending on how you are set up.

---

### Post by borahshadow on 2009-10-10
Ok great. So you have had pretty good luck with the beta 64-bit flash? It's been stable and stuff?

---

### Post by QIII on 2009-10-10
I've been using 64 bit Flash for some time without complaints.

---

### Post by borahshadow on 2009-10-11
Good. That's what I'll plan on doing then. 

Anyother suggestions or comments are still welcome however.

---

### Post by oboedad55 on 2009-10-11
> **borahshadow said:**
> I know that for the most part 64 bit is determined by ram but I just said that his processor was capable of 64-bit. Correct me if I am wrong but even with less than 4GB of ram I thought 64 bit was supposed to be a little faster.

Well I was just going to wait until Karmic comes out unless you convince me I should wait until some updates start rolling out for Karmic (November) . He does not want me to install it for about 2 weeks and by then Karmic is just about 1 week away.

I guess I will try to resize the windows partition. I just remember the last time I tried that it was a bit of a pain.

Thanks for the reply.

Ps. I just realized another benifit of waiting for Karmic rather than upgrading from Jaunty is that then it will have Grub 2 and I won't have to go through the attempt of upgrading that(or not).

Learn from my experience and make sure to defrag windows before you resize the partition. I learned that the hard way once. I also agree with the suggestion that you use Parted Magic to do the resizing. Nothing is perfect but I've never had ill results using this method.

---

### Post by borahshadow on 2009-10-11
Thanks for the advice. I probably would have forgotten/not known to do that. Parted Magic or Gparted? or are they the same thing?

---

### Post by oboedad55 on 2009-10-11
> **borahshadow said:**
> Thanks for the advice. I probably would have forgotten/not known to do that. Parted Magic or Gparted? or are they the same thing?

They're not the same thing but either will work fine. I have used Parted Magic and I know it works well so I'm more comfortable with it.

---

