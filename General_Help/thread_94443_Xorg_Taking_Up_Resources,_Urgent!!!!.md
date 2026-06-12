---
title: "Xorg Taking Up Resources, Urgent!!!!"
date: 2005-11-24
forum: General Help
---

### Post by GrootBrak on 2005-11-24
Here is a serious flaw coming all the way from Warty it seems. I only recently experienced problems. Since the hoary support is close to deaths door, I feel the need to transfer this to Breezy release as well.

Here is the original threads.

> [http://www.ubuntuforums.org/showthread.php?t=18197&page=16](http://www.ubuntuforums.org/showthread.php?t=18197&page=16)

Here is my latest updates.

> I found this thread after much searching about getting frame rate up.
Whoever said things was/is connected to video card or settings have it way wrong. I have an Intel 915 chipset. My graphics originally was a bit slow. After I changed my xorg.conf file a bit I got it working pretty well.
I upgraded from Warty to Hoary to Breezy. No problems. A week or so ago my kids complained their games was slow. Now they do have the tendency of playing everything and not always closing windows, thus slowing things down, I never thought much of it.

Until recently I noticed my games is also jumpy. GLXGEARS start fine for a few seconds and then simply dies down to very slow clicks. So I started another futile search.... My config files is still the same, my hardware is still onboard graphics from Intel etc. The game supertux only play normally when I disable the OpenGL option. All other games is now buggered. Screen savers overheats my PC. (How about CPU savers?!!!) 

During my search I notice a few "Xorgs eats my processor" posts, but I thought thats not my problem. After reading and testing and trying this post, I can say the bugger has to do with Xorg. Unfortunately upgrading to Breezy removed my Kubuntu, darn... so I cannot test the fallback.

But good as this forum may be, as soon as you ask "strange" questions, a deep silence envelopes your post. In the end the only replies you get is babies breastfeeding babies. No gains, no losses, only a waste of time.

I certainly would love to see what the resolve would be, else I will try and fall back to my old kernel, and hopefully that will work.

> Fallback to old kernels still suck my CPU dry. I monitored my CPU when starting glxgears. CPU goes from about 1% when opened and then glxgears run fast. As the CPU reaches about 60% it starts slowing down. At 99,7% glxgears is very very slow. Running this small app for more than a minute, my cpu fan runs full blast, and you can actually feel the extra heat out of the air outlet after three minutes. So whatever is causing this bug, will also cause early CPU failures. I think this needs URGENT ATTENTION. I never even heard my cpu speeds up before this thing cropped up.

CAN SOMEONE PLEASE PAY URGENT ATTENTION TO THIS, I certainly have no plans destroying my CPU, I would rather stick to windows for the time being.

---

### Post by towsonu2003 on 2005-11-24
sounds like you did dist-upgrades all the way up to breezy, which is amazing. I'm sure I misunderstood... 

okay, now the part where you'll wanna kick me **hard**: try doing a fresh install... that's the only thin I can come up with, sorry :(

---

### Post by tzembi on 2005-11-24
Hi,

maybe this could solve your problem:

I had a similar behavior that started when i installed Gdesklets. "top" shows me when these tools are loaded a python process slowly eats up all my memory and some CPU time... The system starts swapping after some time  and everything gets slow... :confused: 

So i disabled these... Hope they´ll look after that in future gdesklets releases.

Just look in a console with "top" which process does what. Could be gdesklets or something else , depends on what you have installed.

HTH,
TZembi

---

### Post by GrootBrak on 2005-11-25
> Just look in a console with "top" which process does what.
Its Xorg that slowly starts eating up processor resources. Moving a window sucks up 25% of the processor.

> try doing a fresh install
Not a good idea. I will loose too many data and my internet is real slow, it takes days to download. I would rather seek a fix, even though it may never happen. 

Any other idea how to re-install without loosing all my data etc?

---

### Post by hw-tph on 2005-11-26
Just a quick couple of thoughts:

What DRI driver is in use? Type **sudo glxinfo | grep renderer** to see what driver is used in OpenGL applications. You might also want to run that same command without the sudo part to see if the normal user really has access to direct rendering. If you're using MESA you're bound to get poor results because it is a software renderer.

Using [xrestop](http://freedesktop.org/wiki/Software_2fxrestop) you can see what X clients use the most memory in the X server if X memory use is an issue.


Håkan

---

### Post by GrootBrak on 2005-11-26
This is the result I get.

> jacques@HomePC:~ $ sudo glxinfo | grep renderer
OpenGL renderer string: Mesa GLX Indirect

Get the same result if I do not use sudo as well. I checked with Synaptic what will happen if I should remove Mesa, but almost everything else will be removed as well. Darn darn darn..... I am willing to try and engineer around this problem, but I don't feel like reinstalling all my apps. I did it once to get alsa working with my games, it was a PIA.

I would rather switch to KDE because it is reported that the problem does not appear in KDE. Please keep up the info.

---

### Post by endersshadow on 2005-11-26
Same issue, but it's with this output for my OpenGL:

```
eric@homesteadgrays:~$ sudo glxinfo | grep renderer
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225
```

---

### Post by GrootBrak on 2005-12-02
Xrestop don't give me much that I can understand. How fo you interpret it? Running glxgears with xrestop, glxgears sits almost right at the bottom, but it still slows down. 

I hope this thread does not die as so many other "tecnical" threads. Google yields nothing worthwhile. Regards

---

### Post by rama on 2005-12-03
I 'd also like to see a "translation" of what xrestop outputs ...

---

### Post by GrootBrak on 2005-12-11
So far I had not recieved any help. Why is there always a drag as soon as you start asking technical questions? I am using windows too often nowadays. Simply because my scanner is still not working and mostly because of this problem. Upgrading to Breezy was the worst mistake I ever made. All previous upgrades got my system better and better. But here is no resolve forthcoming. 

WHERE IS THE DEVELOPERS???

---

### Post by M3ta7h3ad on 2005-12-11
I think you will find its perfectly normal behaviour for software rendering.

Before blowing your lid hows about you just sit and listen/read for a bit.

You dont have a "decent" 3d graphics card. You are using software rendering for 3d applications, it will drag like a dead elephant and it will also whore your CPU.

Suggestions: Upgrade your computer (it sounds like its a laptop however), or.. stop trying to play 3d graphic games on a computer that clearly struggles under it.

[http://www.intel.com/products/chipsets/855gm/](http://www.intel.com/products/chipsets/855gm/) << is your chipset. You have "intel Extreme Graphics II" which I know struggles even with the most basic of games.

What you may also need to install is cpufreq or at least try and configure it to clock your processor down a bit to prevent it overheating. Plenty of how-to's both on the web and in the forums I would have thought for that.

Your question isnt technical at all, it just contains very very little information beyond the symptoms, and a rant.

---

### Post by 23meg on 2005-12-11
[QUOTE=GrootBrak] Why is there always a drag as soon as you start asking technical questions?  
[/QUOTE]
There isn't. Technical questions are the very reason of existence of these forums, and most of them are answered and solved. Don't generalize just because *your* problem hasn't been solved.
[QUOTE=GootBrak]WHERE IS THE DEVELOPERS???[/QUOTE]Not here. If you think yours is a reproducible bug and wish to notify them of the issue, report it as a bug in the bugzilla.

---

### Post by GrootBrak on 2005-12-12
> Suggestions: Upgrade your computer (it sounds like its a laptop however), or.. stop trying to play 3d graphic games on a computer that clearly struggles under it.

Typical info. My computer never struggled before. Its a Pentium 4, 2,4GHz if I recall, and no, its a desktop. Meaning about as fast as you can get in a year old machine. And my 3d games in windows is working perfectly, even though its much more intensive. (The worst 3d game I have on Linux is Penguinracer.) If glxgears drags down my cpu or just rezing a window, sorry I'm using Linux.... 2D games is just as bad...

Here is a link to my processor. [http://www.intel.com/products/processor/pentium4/product-brief/index.htm](http://www.intel.com/products/processor/pentium4/product-brief/index.htm)

I have the 915 chipset, also unsupported by Linux. I admid that I don't have gigs of ram lying around, but is'nt this why linux rule over windows? Much older PC's can get going faster than mine. I have a 486 clonker with 32M ram, that does a better job than my "new" PC.

> What you may also need to install is cpufreq or at least try and configure it to clock your processor down a bit to prevent it overheating
And slow my system down further? Your solutions is little real help for those with similair problems. 

And BTW, I removed Ubuntu completely, formatted my disk, and installed Hoary from CD. Loaded only the base system, with one user. Started "top" same problem.
Removed Ubuntu again, installed Mandrake 10.0 fresh. Started "top" and things are much better. Still not too happy with glxgears running my cpu hot, but at least its not stuttering. But I never add videoram to my Xorg.conf file in Mandrake. I still have to figure the Mandrake nuances out.


> If you think yours is a reproducible bug and wish to notify them of the issue, report it as a bug in the bugzilla.
Thanx, this problem is already filed as a bug. But it gets stuck with mainly an NVDIA card problem. At this stage there has been no new posts about this bug. I think I should file a new one. 

Apologies to my percieved rant. But just search under my name, and you will see a long list dating back from Hoary of unsolved issues. Many well meaning users start out helping and then just drops out. Sound, scanner and now Xorg threads never get solved. Now with Breezy, I cannot get my scanner to work at all, even trying my best from the Sane website instructions. But that is another post.

---

### Post by M3ta7h3ad on 2005-12-12
[QUOTE=GrootBrak]Typical info. My computer never struggled before. Its a Pentium 4, 2,4GHz if I recall, and no, its a desktop. Meaning about as fast as you can get in a year old machine. And my 3d games in windows is working perfectly, even though its much more intensive. (The worst 3d game I have on Linux is Penguinracer.) If glxgears drags down my cpu or just rezing a window, sorry I'm using Linux.... 2D games is just as bad...
[/quote]
3d games in windows will work perfectly as there will be drivers for your chipset as you mention below your chipset is not supported directly by linux.

You have no 3d acceleration according to linux, therefore all of your 3d performance is down to software rendering, which will make your processor work like hell to try and play any games.

Stop using 3d games when you dont have 3d acceleration. Simple.

> 
Here is a link to my processor. [http://www.intel.com/products/processor/pentium4/product-brief/index.htm](http://www.intel.com/products/processor/pentium4/product-brief/index.htm)

I have the 915 chipset, also unsupported by Linux. I admid that I don't have gigs of ram lying around, but is'nt this why linux rule over windows? Much older PC's can get going faster than mine. I have a 486 clonker with 32M ram, that does a better job than my "new" PC.

Actually I've found GDM to be a wee bit of a ram whore, in fact the only ram friendly distro I've found is feather linux and thats using XVesa I believe, specifically designed for older computers.


> And slow my system down further? Your solutions is little real help for those with similair problems. 


CPUFreq is clearly needing to be configured correctly if your computer is overheating from use. I am thinking not to "slow down your experience" but to actually prevent damage occurring to your hardware.

> 
And BTW, I removed Ubuntu completely, formatted my disk, and installed Hoary from CD. Loaded only the base system, with one user. Started "top" same problem.
Removed Ubuntu again, installed Mandrake 10.0 fresh. Started "top" and things are much better. Still not too happy with glxgears running my cpu hot, but at least its not stuttering. But I never add videoram to my Xorg.conf file in Mandrake. I still have to figure the Mandrake nuances out.


Well done for finding a distro that works a little better with your hardware. I hope it works out for you.

> 

Thanx, this problem is already filed as a bug. But it gets stuck with mainly an NVDIA card problem. At this stage there has been no new posts about this bug. I think I should file a new one. 

Apologies to my percieved rant. But just search under my name, and you will see a long list dating back from Hoary of unsolved issues. Many well meaning users start out helping and then just drops out. Sound, scanner and now Xorg threads never get solved. Now with Breezy, I cannot get my scanner to work at all, even trying my best from the Sane website instructions. But that is another post.

I dont believe what you are experiencing is a "bug" its a mere issue of incompatibility.

As for people dropping out of helping you, then im not surprised considering your attitude in your posts. Who in there right mind expects people to search users for past history.

I am pretty sure there is a HCL somewhere around here for ubuntu, I think in future your better off checking your hardware against the HCL for whatever distro you intend to use.

---

### Post by awaldram on 2005-12-12
Don't know what all this bumph is about.

Your issue is your machine is using software rendering when it should be using hardware rendering.

As your cpu is having to work its buns off to render the display it obviously gets hot.

your 915 does support hardware dri

I cant help you directly as my laptop has the i830m but dri is working fine here

try following the links in this thread

[http://ubuntuforums.org/showthread.php?t=40865&page=1](http://ubuntuforums.org/showthread.php?t=40865&page=1)

---

### Post by GrootBrak on 2005-12-21
> Your issue is your machine is using software rendering when it should be using hardware rendering.

As your cpu is having to work its buns off to render the display it obviously gets hot.

your 915 does support hardware dri

Guys and gals, please bear with me. I did not have any problems until recently. 3d and 2d games and whatever worked just fine. The problem came after I upgraded to Breezy in my case. Other users have had the same problem from Warty still dragging along. 

Thanx for the link awaldram. Originally I followed the thread to the letter to get my fps up, but it did not help my case. In the end I only had to add videoram to my xorg.conf file and my slow frame rate was gone. At that time my cpu did not heat up in Ubuntu so that the fan pulls the box of the table!!! (Not the case with windows at the time...) Currently my frame rate reported is still high, but its visibly slow. I still play the same games as with my old "working" system.

Even folks with video graphics cards have problems with Xorg sucking up the resources. I planned to switch back to XFree86, but cannot make much sense of the procedure to change to Xfree86. Although the Xfree86 is still in Synaptic, its not available anymore for installation.

---

### Post by GrootBrak on 2005-12-21
For those that want to see the original thread, here is the link again.

[http://www.ubuntuforums.org/showthread.php?t=18197&page=17](http://www.ubuntuforums.org/showthread.php?t=18197&page=17)

It has been viewed over 21300 times according to this forums, I am sure that will accound for something.

---

