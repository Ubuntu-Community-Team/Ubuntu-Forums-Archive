---
title: "Getting an ASUS U43JC soon. Are these configs up-to-date?"
date: 2011-02-16
forum: Hardware
---

### Post by TheoJava on 2011-02-16
The ones in this thread, I mean:

[http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)

I'd like to setup a dual boot of the Windows 7 it comes with, and Ubuntu; and be able to get it running as smooth as possible from the get-go.

I noticed the bottom of the main post in that thread says there's a few unresolved issues. Is that still true?

Is there any other documentation I should look into, that'll help me along? I'm not entirely a noob with Ubuntu, but I pretty much may as well be, because I've been largely reluctant to deal with anything relating to the command line. I'd like to start digging into it, once I get this ASUS though.

(P.S. I'm getting the U43JC-B1 model, if that matters at all. I'm guessing it doesn't matter much, cause the specs aren't all that different).

---

### Post by TheoJava on 2011-02-16
Bump

---

### Post by TheoJava on 2011-02-16
More bump

---

### Post by cascade9 on 2011-02-17
Seems to be a major pain to get that laptop running well on ubuntu. Have you considered finding a laptop thats not going to take that much hacking to run OK? 

BTW, you are meant to wait at least 24hrs between bumps.

---

### Post by TheoJava on 2011-02-17
From what I understand, it's going to run perfectly fine, out of the box. Those are just tweaks to get it working more correctly. It's a little too late to look at other laptops, cause that one is already on its way, plus I really enjoy its design.

Sorry about the bump spamming, I'm not entirely familiar with this forums etiquette yet. =^/ it won't happen again.

---

### Post by TheoJava on 2011-02-17
Now that I think about it, why is it preferred to have the Nvidia driver disabled?

---

### Post by cascade9 on 2011-02-18
> **TheoJava said:**
> Now that I think about it, why is it preferred to have the Nvidia driver disabled?

Optimus. Unless there is some BIOS switch I know nothing about for that model, you simply cant install he nvidia drivers. (nvidia doesnt suppoprt optimus with linux). So if you dont hack around, the nVidia GPU will just suck power and create heat (not a huge amount of heat, but still.....) 

Aside from having an nvidia GPU that unless you do some major terminal work to disable, I wouldnt call a laptop that needs that many hacks to run properly 'running perfectly fine out of the box'.

---

### Post by TheoJava on 2011-02-18
That's nice, but telling me I should have gotten a different laptop is not constructive; which is what I made this thread for.

So yeah, if anyone else is using this ASUS model, any tips or advice would be appreciated.

---

### Post by cascade9 on 2011-02-19
> **TheoJava said:**
> That's nice, but telling me I should have gotten a different laptop is not constructive; which is what I made this thread for.

Come on, I never said that. 

"Have you considered finding a laptop thats not going to take that much hacking to run OK?". 

You can take that any way you want though :lolflag: 

I do find it interesting that you came out with this after I give you the bad news that the nVidia GPU in your laptop is basicly useless with linux distros. ;)

---

### Post by TheoJava on 2011-02-19
So Nvidia is more of less universally unsupported?

Enh, oh well. I don't see myself doing anything on Ubuntu that'd require a dedicated GPU anyway.

---

### Post by Saprissa on 2011-04-25
> **TheoJava said:**
> The ones in this thread, I mean:

[http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)

I'd like to setup a dual boot of the Windows 7 it comes with, and Ubuntu; and be able to get it running as smooth as possible from the get-go.

I noticed the bottom of the main post in that thread says there's a few unresolved issues. Is that still true?

Is there any other documentation I should look into, that'll help me along? I'm not entirely a noob with Ubuntu, but I pretty much may as well be, because I've been largely reluctant to deal with anything relating to the command line. I'd like to start digging into it, once I get this ASUS though.

(P.S. I'm getting the U43JC-B1 model, if that matters at all. I'm guessing it doesn't matter much, cause the specs aren't all that different).

TheoJava,

Maybe you want to give this a try:

[http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html]("http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html")

[INDENT]There is a new module that provides hybrid graphics functionalities
using the nouveau drivers. Both the Intel and Nvidia cards can be used
with this method. It has been tested on an Asus UL30VT, but should
work for the following laptop models:...
[/INDENT]
Your model isn't listed but the U33JC is. Maybe you'd like to test it out?

---

