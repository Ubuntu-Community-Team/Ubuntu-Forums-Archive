---
title: "Graphix Card and Halo 1"
date: 2012-07-27
forum: Hardware
---

### Post by HoCo xXSamXx on 2012-07-27
I posted this question before, but It got marked as solved. I know I did not do this, and it does frustrate me a but that this happened. I know that this community has a lot of great staff, as I have met alot of them. I dont know, maybe the post was in the wrong section or something but here it is again. (I know Im double posting. Could a staff member delete this old thread? [http://ubuntuforums.org/showthread.php?t=2034082](http://ubuntuforums.org/showthread.php?t=2034082))

This is the OP:
> So recently I inherited my Mom's old laptop (Shes not dead, just got a mac,  ) Anyways, I installed Ubuntu v12.04 and the latest versions of wine and PLayOnLinux. I secondarily installed Halo, but When I run it, I get no video. Let me expound on what I mean:

Halo opens and I see the publisher's videos for Microsoft an the other company.
I then get a black screen, but I can hear the halo music.

Is it my graphix card? I used to play Halo on this laptop, when it ran Win7, so is it the graphix driver?

Help me! lol Thanks, 
HoCo

---

### Post by Icarus315 on 2012-07-28
You probably should start on the WINE AppDB page for: [Halo](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720).  It is full of tips.  Like what extra packages you have to install into the Play on Linux prefix.

Keep in mind that not all software from Windows will work under WINE or PoL.  Sometimes even later versions of WINE will break things that used to work with earlier versions.  That is where PoL's ability to manage multiple versions of WINE comes in super handy.  Make sure you know how to use that.  So, go to the above link, make sure your Halo is patched to the latest version to remove the CD-Check, and use the same WINE version as given on that AppDB page and also install the extra packages as given on the same page.

Also, if you are running a 64-bit system you'll most likely need to install 32-bit libraries.  The basic way to do this is:
```
sudo apt-get install ia32-libs
```
Again, 64-bit, more libraries, 32-bit ones, may be needed but the above should pull in most of what you need.

You should also be running proprietary drivers if you have either an AMD/ATI or nVidia graphics card.  Proprietary drivers are a necessary evil because they usually offer much more performance than their open-source counterparts.  Performance is important when you are using your system for graphically-intense games.

---

