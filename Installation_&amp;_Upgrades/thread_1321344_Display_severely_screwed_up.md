---
title: "Display severely screwed up"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by pointblank941 on 2009-11-10
I am a newbie to Ubuntu so go easy on me. I have a Compaq N600c with ubuntu 9.10 and am having severe display issues, there are color lines, artifacts, and it is going somewhat slow. I looked up the drivers but they were all for Windows xp/vista. How do i fix this?

---

### Post by Mark Phelps on 2009-11-10
According to Google, your machine has a Mobility Radeon AGP chipset -- which could be bad news because (1) ATI/AMD dropped support for all but the current chips back in May, and (2) I've read there are additional video problems with ATI chipsets using 9.10.

To see if you're running the restriced ATI driver, open a terminal and enter "fglrxinfo".  If you're running that driver, that could be the problem and then, you need to remove it and replace it with the open source driver, as shown below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

If you're not running the restricted driver, then you're in a real bind because you're already running the open source driver by default.

You could then check on the Phronix forums about the open source drivers to see if they have any tweaks you could try. They do a lot of testing of ATI drivers.

---

### Post by pointblank941 on 2009-11-10
I dont have that fglrx driver installed....
Ill look for something on that website you mentioned

---

### Post by mr_steve on 2009-11-10
> **pointblank941 said:**
> I am a newbie to Ubuntu so go easy on me. I have a Compaq N600c with ubuntu 9.10 and am having severe display issues, there are color lines, artifacts, and it is going somewhat slow. I looked up the drivers but they were all for Windows xp/vista. How do i fix this?

I have several of this exact laptop. It does indeed have a Radeon Mobility chipset. There are two things you should do to get this machine working decent.

First, turn of desktop effects. Go to System->Preferences->Appearance. On the Visual Effects tab, select None.

Second, see my post near the bottom of page 2 of [this thread]("http://ubuntuforums.org/showthread.php?t=1304635&page=2"), where I describe how to change the AccelMethod used by X.[URL="http://ubuntuforums.org/showthread.php?t=1304635&page=2"]
[/URL]

---

### Post by pointblank941 on 2009-11-11
Wow, that worked very well. Thanks! What exactly did your instructions do though?

---

### Post by mr_steve on 2009-11-11
> **pointblank941 said:**
> Wow, that worked very well. Thanks! What exactly did your instructions do though?

Basically, there are at least two possible methods of 3d acceleration in the ATI drivers. One is UXA, and the other is EXA. In Karmic, UXA is used by default, but this apparently causes some issues on certain ATI chips, like the one in our Evo N600cs.

So, my instructions simply switch the acceleration method back to EXA, which works fine. I'm not sure if it's quite as fast, especially since my N600c is short on RAM, but it works.

I believe it also has something to do with EXA and UXA handling video RAM differently, I think one can work on machines with less VRAM than the other.

To be honest I don't know much of the technical details of 3d Acceleration anymore, except that it used to be a colossal pain, but in Ubuntu it (usually) just works.

I had to spend a lot of time figuring this out when I first upgraded my spare laptop to Karmic, but now I just keep my old thread bookmarked. :p

---

