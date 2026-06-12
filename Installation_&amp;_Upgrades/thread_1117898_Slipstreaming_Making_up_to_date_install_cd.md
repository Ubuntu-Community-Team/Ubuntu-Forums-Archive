---
title: "Slipstreaming?? Making up to date install cd"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Hachi-Roku on 2009-04-06
Hey Hey,

In windows its called slipstreaming, not sure about what its called in the linux world...


So u install ubuntu and do all those little fixes and workarounds to get things in order.

Is it possible to then make an install cd which includes all the changes and mods you've done to save doing them again if you re install??

cheers

---

### Post by Didius Falco on 2009-04-06
> **Hachi-Roku said:**
> Hey Hey,

So u install ubuntu and do all those little fixes and workarounds to get things in order.

Is it possible to then make an install cd which includes all the changes and mods you've done to save doing them again if you re install??

cheers

I'm not quite sure exactly what you are after. If you want to save all your own customization, just backup/image your partitions.

If you are looking to save having to download all the *.deb packages you've already downloaded, you'll find them in the /var/cache/apt/archives directory. You should be able to  simply burn them all to a CD (or DVD) and add that CD to your Synaptic Package Manager and install them from there, or use a USB stick to do the same thing.

Fair warning: I've been using PCs since dos 3, so I do have quite a bit of experience, but I'm very new to Ubuntu. The above seems like it should work, but I'd much prefer someone with a lot more experience in Ubuntu confirm that my assumptions are all sound before you take my word as golden and screw up your install.

On the other hand, since you'd be reinstalling anyway, the worst it could hurt you would be to make you re-reinstall and download all the updates and apps again. <G>

I ran across a utility that automates the process called AptonCD, but it looks like it hasn't been updated since May of 2007. I haven't used it, so no guarantees...

I hope this helps. Good luck and report back on how it works out.

On Edit: APTonCD is available via Synaptic...

---

### Post by batharoy on 2009-04-06
[http://www.geekconnection.org/remastersys/remastersystool.html]("http://www.geekconnection.org/remastersys/remastersystool.html")

Remastersys is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.

   1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
   2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.

---

