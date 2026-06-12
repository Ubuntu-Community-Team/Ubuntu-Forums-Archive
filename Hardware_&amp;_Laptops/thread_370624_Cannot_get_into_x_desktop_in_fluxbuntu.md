---
title: "Cannot get into x desktop in fluxbuntu"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by shellhrs on 2007-02-25
I am running Fluxbuntu 6.10 on my Thinkpad 600e (triple boot with Dreamlinux 2.0 and W2K). Sometimes, I couldn't login to Fluxbuntu. The login screen appeared, and after I entered my username and password, it disappeared, and then appeared again. I know for sure that I entered my login correctly (otherwise it would have displayed "Login Incorrect").

I even tried Ctrl-Alt-F2 to get text login, which let me in, but when I "startx", it gave me an error which recommended me to remove X0-temp (I guess).

I had to shutdown the machine, and even initialize the BIOS before I can have the desktop.

Is this just my machine, or anyone else have the same problem?

FYI, I had been using Ubuntu 6.06 with Fluxbox before, but for some reason (I guess because I've read somewhere that Fluxbuntu is a better choice for the system) I replaced it with Fluxbuntu. :)

---

### Post by n8bounds on 2007-02-25
Fluxbuntu hasn't really released a first stable version yet.  You have a developmental version.  If you're not beta testing some feature xyz, there is no validity to your final claim.

---

### Post by shellhrs on 2007-02-26
> **n8bounds said:**
> Fluxbuntu hasn't really released a first stable version yet.  You have a developmental version.

Check [this]("http://wiki.fluxbuntu.org/index.php?title=Main_Page#Is_Fluxbuntu_stable") out. While it is true that the version I use is nbuild1-rev2, it "is not intended to infer instability of the OS itself."

> **n8bounds said:**
> If you're not beta testing some feature xyz, there is no validity to your final claim.

I don't remember claiming anything. If there is something close to a "claim", I guess it would be the sentence: "I guess because I've read somewhere that Fluxbuntu is a better choice for the system".

I get the idea to install Fluxbuntu from [here]("http://www.ubuntuforums.org/showthread.php?t=333796"). As you can see, the validity is from people's comments, not from my own. Nonetheless, because I have installed it in my system, I can say for sure that FLUXBUNTU IS A BETTER CHOICE FOR MY SYSTEM.

Now, THAT'S a CLAIM. :) :) :)

Although I've tried Dreamlinux 2.2 MM, and it is now a contender to Fluxbuntu (it is faster to load and look great, but it still have problems with my PCMCIA and mounting drives is somewhat annoying). :popcorn:

---

### Post by hendrikE on 2007-03-06
Hello, I am new to this forum and to the world of ubuntu. I found this post because I "suffer" the same problem. I tried to boot fluxbuntu in graphics safe mode on an IBM T20 but I can't start x. So its just the console. Does it have anything to do with graphic drivers? I'll try Ubuntu now. So if you have any update on this topic I'd like to now. Thanks

---

### Post by shellhrs on 2007-03-21
I don't have logging-in problem all the time. Only when I restart Fluxbuntu.
If I cold boot after at least 1 minute, I got no problem at all.

---

### Post by kerry_s on 2007-03-21
> **shellhrs said:**
> I don't have logging-in problem all the time. Only when I restart Fluxbuntu.
If I cold boot after at least 1 minute, I got no problem at all.

Try installing GDM a more updated login manager, XDM is old as hell and does not work well with the newer xorg.

---

