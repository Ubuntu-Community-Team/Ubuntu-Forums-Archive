---
title: "HD5770 working w/full 3d , probly others too!"
date: 2011-03-20
forum: Hardware
---

### Post by Linkdead on 2011-03-20
I thought this wordy tutorial might help someone out there . I'll start off with my pc specs, problems I have had, and my fix. 

**Motherboard:** GigaByte EP45-UD3P
**Memory:** OCZ FLEX|EX PC9600 DDR2 1200Mhz 2x2gig
**CPU: **Core2Duo E6600 2.4 Ghz ( 4.0 stable )
**Video card: **Sapphire HD5770 1gig GDDR5
**Video Display:** Optoma EP1690 720p Projector 
Ubuntu 10.10 / Mac OSX / Windows 7 

Built primarily for entertainment, I use it mostly for schoolwork and self study now.


_**Every** distribution_ I tried had an **annoying pink line** on left side of my screen. Deal breaker for me (at the time), and probably  a lot of others. I decided to give it another chance on my HTPC after signing up for a LPIC (Linux Professional Institute Certification) training class.

Installation 10.10:

My first install of 10.10 had that pink line, with added bonus features of a locked, non native resolution, with no 2d or 3d. I decided that I was going to fix it, or die trying! A short time after booting I had the pink line **_[B][U]fixed with [U][B]ATI's proprietary**_[/U][/B] driver (11.2)[/U][/B] that was downloaded from there site. I had 2d functionality, but I wanted to be cool like all those kids on youtube and have 3d. 10 hours later the only thing I found was a reference to try alpha drivers ( [www.x.org](www.x.org) ). Tried that, with no change to my lack of 3d. I decided to mess with other things at that point, and broke my installation.

When booting into my second installation of 10.10, _**[U][B][B]I installed the ATI drivers again, except not the same way.**[/B]_[/B][/U] I clicked System > Administration > Additional Drivers and let it do its thing.  Surprisingly 3d had full function this time!

So the moral of the tutorial is this:

**_If a program is not working try installing it a different way! _**Linux is buggy when it comes to user environments, and historically alot more with ATI products.

---

