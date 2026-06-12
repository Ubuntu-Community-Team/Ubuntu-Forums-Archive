---
title: "Bugged default drivers for Radeon HD 6650M in 18.04 LTS. What to do next?"
date: 2019-12-08
forum: Hardware
---

### Post by charles-scoville on 2019-12-08
Hola good folks,

So, I have a laptop with...

[LIST]
[*]**CPU** ----     Intel Core i3-2310m (Sandybridge Mobile) 
[*]**iGPU** ---     Intel HD Graphics 3000 (Sandybridge Mobile) 
[*]**dGPU** -- Radeon HD 6650M (TeraScale     2 (VLIW5) "Evergreen" - Northern Islands) 
[/LIST]

  Well... the default drivers that ship with Ubuntu (Kubuntu, actually) 18.04 LTS are pretty bugged for this system. Near as I can tell, the drivers for the dGPU don't properly support OpenGL somewhere around OpenGL 3.1 and up. This is most reproducible with Blender, wherever I invoke the Eevee render, as this requires OpenGL 3.3+ to work properly. 
 
If it was *JUST* 3D, I wouldn't have too much problems with it, but there are also issues with the desktop environment. Window frames will sometimes get flickering ghost images of what's under them when they are moved (broken transparency), or disappear entirely. With MPV player (Probably also using OpenGL) if I pause the video, or rapidly minimize/maximize the window, the video gets stuck in a short , flickery loop. Sometimes this will cause the backdrop to go all black too. If I do enough screwing around, eventually the graphical problems will get to the point of making the desktop unrecognizable, unstable, and I am left with no choice but to restart.

Here is some more details.
 
[LIST]
[*] The package that seems to be     supplying my drivers is Mesa (v19.0.8). (This is just userland     OpenGL though, right?) 
[*] The actual 3D driver is r600g,     which should be correct for the TeraScale 2 - Northern Islands.     (Mesa matrix decoder ring doesn't find the "HD 6650**_m_**",     but does find the "HD 6650" as r600g/TeraScale 2) 
[*] Command [FONT=fixedsys]"lspci"[/FONT] lists my GPU as _[AMD/ATI]     Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] (rev ff) (For a     time, I believe this was showing up as TURKS, not Whistler.     Hopefully that means it's being worked on!?)_ 
[*] Command [FONT=fixedsys]"lsmod" lists the[/FONT] Kernel module as "radeon" 
[*] **[FONT=fixedsys]_"modinfo radeon"_[/FONT]***_     does not show "Whistler" as an available firmware. I have     no idea what it's actually using!_* 
[/LIST]
 
Some other notes, in order of preference.
 
[LIST]
[*] I have working switchable     graphics; DRI_PRIME=n works very well. (And I'd like to keep it that     way) 
[*] I'm using KDE Plasma DE. (And     I'd like to keep it that way) 
[*] I'm using Kubuntu 18.04 LTS. (And I'd like to keep it that     way) 
[/LIST]

 The reason I'm here is that I'm not really sure what to do about this? On the one hand, everything seems to be using the best available option. On the other hand, it's not working right. Is this a Mesa problem, a r600g problem, or a kernel module problem? The fglrx.ko module possibly (probably) has the correct firmware, but that's depreciated since Kernel version 4.4, and I'm on 4.15. How do I even work with this? Do I need to switch distros/versions? Or is that even going to work? Can I shoehorn in fglrx.ko? Or is that even going to work? Is this a known problem, and a fix is on the way? Will there even be a fix? Do I have to just live with this?

 :confused:

I'd like to at least get the dedicated GPU working 100%. Worst case, seems like I (a) switch distros to use an older kernel, (b) disable the iGPU/switchable graphics, and (c) take the power usage hit. I *REALLY* don't want to have to do this . . .

---

### Post by CatKiller on 2019-12-08
fglrx is dead. It's definitely not worth trying to staple its corpse to your install.

There are PPAs that provide newer versions of the Mesa stack. I haven't used them, so I couldn't recommend a specific one, but I understand that a whole bunch of enablement stuff is ongoing, even for older generations of graphics.

---

### Post by charles-scoville on 2019-12-08
Hi! Thanks for the reply. ^_^


_**About fglrx.**_
As it relates to 18.04., "message received." I'm much more inline with doing something better. (read below)

However, I'd like to point out (using your analogy) that, with software, I have the power of time travel; I could easily install a full stack/OS from a time when fglrx was still alive and kicking. And, *IF* that's what I have to do to make my computer Just Work&#8482; I could probably live with it. I don't like it either, but I gotta do what I gotta do. TBH, Window$ is even on the table at this point :shudders:, if that's any indicator of how bad this is getting for me.


_**About Mesa PPA.**_
Could you point me to the right place for looking into this vector? First search engine hit was this...
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

What are the odds this will brick my OS install you think? I can DD a backup image, just to be sure. (I'm actually going to do that right after I post) Page above says I can PPA purge to get back to stock. That's obviously assuming I have a command shell though...

PS. It should go without saying, any advice you give won't be held against you. I make my own decisions ultimately.

---

### Post by CatKiller on 2019-12-08
> **charles-scoville said:**
> Could you point me to the right place for looking into this vector? First search engine hit was this...
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) 

That is one that I've seen mentioned. The other one I can recall is [Padoka stable.](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa) It really depends on how new you end up needing. 

> What are the odds this will brick my OS install you think? I can DD a backup image, just to be sure. (I'm actually going to do that right after I post) Page above says I can PPA purge to get back to stock. That's obviously assuming I have a command shell though...

The odds of it bricking your install are essentially nil, but backups are sensible things to have always. If you end up using bleeding-edge stuff you may encounter bugs, although you mentioned that you've got those anyway. 

ppa-purge generally does what it's supposed to. I don't think it's installed by default. 

Not even being able to boot to a command line isn't actually an impediment to being able to fix stuff; you can boot a live USB and still do package management and file operations as a chroot to your install, should you ever need to. I regularly use SSH from my phone to manage my headless computers, too.

---

### Post by charles-scoville on 2019-12-09
OK. Backup images put on external, in duplicate. Wish me luck.\\:D/

---

### Post by charles-scoville on 2019-12-09
It may be premature, but, so far . . . 



Substantially better with Obiaf's PPA. 

In particular, MPV player doesn't hang/loop anymore, no matter how much I abuse min/max || pause/play.

Blender + eevee render was still broken, but I did some checking, and it turns out that Blender 2.80 was/is broken. The latest version, 2.81a, doesn't have the same issue.  

Now I just need to know how, or if I even can, freeze those updates so that I can keep the fixes I have gained. 
As it says ...
"* all packages are automatically built twice a day, when there are upstream changes"
And, as you said, the PPA in question is potentially unstable. 

Anyway, thank you very much. I'm going to mark this thread as solved for now. I'll be back if this problem comes back. ~Off to the search engine I go now.

---

### Post by CatKiller on 2019-12-09
Glad to hear things are working better for you now. 

> **charles-scoville said:**
> 
Now I just need to know how, or if I even can, freeze those updates so that I can keep the fixes I have gained. 
As it says ...
"* all packages are automatically built twice a day, when there are upstream changes"
And, as you said, the PPA in question is potentially unstable. 

Now that you know fixes went in somewhere between 18.04 and the ever-moving now, you could find a PPA that's after those fixes but with a slower cadence. There's a Padoka Unstable as well as the Padoka Stable, or the [x-swat PPA](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates). One of those might give you the balance that you're after. 

Another option is to simply hold off from doing upgrades until you also have security updates from the normal repositories. Kubuntu's panel indicator displays those states separately. That way you'll only be updating roughly weekly rather than every day. 

Commenting out the entries from your sources.list is technically an option that will mean that you don't get any more updates. You'll need to remember to uncomment them and then run ppa-purge before you upgrade to 20.04. I think the versions from the PPA are sufficiently ahead of the normal versions that you won't get version conflicts for a while, but the Hardware Enablement Stack will get updated at some point - February, I think - so you'll want to see what's coming down the pipe around then to decide whether to purge or re-enable the PPA at that point.

---

### Post by eg-bnb on 2020-02-06
> **charles-scoville said:**
> It may be premature, but, so far . . . 
Substantially better with Obiaf's PPA. 


Can you post a summary of what you did?  Some of this is not particularly interpretative to me, a quasi newbie. I looking for better connections to 4k/UHD TVs (monitors) for both viewing and (light) editing of video and photos.  

I have a Mac-Mini with a i52529M CPU with a Radeon HD 6630M gPU
This hardware should have lifetime for the next decade for stuff more than email, web surfing and streaming... possibly gaming.

Thanks in advance.

---

### Post by mastablasta on 2020-02-07
instructions are found here: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

issue in your case is the mobile radeon chip. even the new AMD do not have such good support for mobile chips as they do on desktop. still support does improve in time but not as much as they should

since it's mac wouldn't it be better to use the MacOS or whatever it's called now? at least hardware is properly supported there.

---

### Post by eg-bnb on 2020-02-09
Thank you... I will look & experiment, as appropriate.
Funny thing is, I swapped TV displays - from a 2005 Panasonic to a 2015 Vizio - both 1080i.  The over/underscan issue is gone.  I know TVs don't make the best PC monitors, but right now I am pleased with the generic drivers for videos/movies.

the Mac-Mini is a 2011 version & depreciated by Apple (no updated OS).  
Nevermind that I really don't like their OS.  
I was hoping it was going to be suitable platform for this **ok boomer** to get deeper in Linux.  
Thanks again.

---

### Post by charles-scoville on 2020-03-06
Hello again.
it's been a few months, and I just  thought I would report back how it's been going so far. (Sorry if that  also means I'm necroing this thread.)

I'm still running on  Obiaf's PPA. No, I didn't actually bother to freeze anything like I had  planned. Even so, I have not, as of yet, run in to any problems updating  with this PPA. However, my problems have not actually gone away. Things  got substantially better, yes, but there are still problems. In  particular, I can cause a very specific error on demand with MPV.  Basically, if I pause MPV player for an amount of time, when I go to  play it again, there is a short delay, then the next several frames get  stuck in a tight loop. Audio continues playing fine, but video is  borked. Seeking back real quick resets the video.

...

I am  just now reading that this may be a known bug. See the following if you  are also having this problem; virtually identical symptoms.
[https://gitlab.freedesktop.org/mesa/mesa/issues/485](https://gitlab.freedesktop.org/mesa/mesa/issues/485)

Other than that, all's been good~ :cool:.

---

