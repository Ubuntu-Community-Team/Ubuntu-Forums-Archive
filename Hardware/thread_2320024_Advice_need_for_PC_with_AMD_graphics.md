---
title: "Advice need for PC with AMD graphics"
date: 2016-04-09
forum: Hardware
---

### Post by onlineguy on 2016-04-09
Hi,

I run Ubuntu 15.10 on my PC with an AMD R9 280X graphics adapter. I mainly use this computer for surfing the web playing a few games, mostly War Thunder and some games via Steam. 

A few weeks ago I read about the deprecated flgrx driver in 16.04 but had no time to dig into this til now. My understanding is that IF I upgrade right away I'll end up with crappy graphics performance because the graphics adapter will not be supported by the new AMDGPU driver, at least for now. Ubuntu 15.10 will have its EOL by the end of June which isn't terribly far away as well. An updated version of AMDGPU seems to be targetd at 16.04.1 which will be released way after 15.10 had been out of support. 

So, what kind of options do I have? I couldn't find any news giving me some hope or pointing at a possible way out of this dead-end. Did I miss anything?

---

### Post by v3.xx on 2016-04-09
> I couldn't find any news giving me some hope or pointing at a possible way out of this dead-end. Did I miss anything?

No, you pretty much have the big picture.

[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Dropping-fglrx](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Dropping-fglrx)

> So, what kind of options do I have?

Run 15.10 pass its EOL or upgrade and hope for the best, maybe your games will be ok.

Or go the other direction.  14.04 will be supported till 2019 and when your ready to move on, it can be upgraded direct to 16.04.  LTS releases (12.04; 14.04; 16.04) are supported for five years and will upgrade from LTS to LTS, skipping the interm releases.

---

### Post by grahammechanical on 2016-04-09
> because the graphics adapter will not be supported by the new AMDGPU driver,

I suggest it is more accurate to state that it is a work in progress. The fact is. if you upgrade to 16.04 at any time the AMD proprietary video driver will be removed and the system will fall back to using either Radeon or amdgpu depending on the hardware. It is all in the 16.04 release notes. Including this statement
> 
The fglrx driver is now deprecated in 16.04, and we recommend its open  source alternatives (radeon and amdgpu). AMD put a lot of work into the  drivers, and we backported kernel code from Linux 4.5 to provide a  better experience.

Ubuntu 16.04 does not yet have kernel 4.5.

You could dual boot with 16.04 and see how things run with your normal working arrangements before upgrading the production OS. This is a "see how it goes & see how it develops" situation.

Regards.

---

### Post by onlineguy on 2016-04-11
I setup a dual boot with 14.04.4 and the open source driver's performance is pretty bad in War Thunder up to a point where the system freezes. Haven't tried the other games yet. I guess I can't expect huge improvements in 16.04 since AMD shifted they're efforts towards AMDGPU, can I?

---

