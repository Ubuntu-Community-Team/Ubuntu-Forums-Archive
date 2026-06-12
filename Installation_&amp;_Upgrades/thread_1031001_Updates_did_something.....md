---
title: "Updates did something...."
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by PanicIRAQ on 2009-01-04
Hey there, I'm a noob to ubuntu (or rather linux in general).  Anyways, I have recently installed Wubi and thus ubuntu linux and everything was going good until I tried to install flash and get the 213 updates that ubuntu told me I had ready to install.  I found a bunch of guides for installing flash and they half worked; youtube videos now show a gray box where the video is supposed to be where before it said i needed to install flash.  That was my first issue, however I downloaded all of the updates figuring that that issue would be fixed and instead I can not connect to the internet at all.  Can anyone help?

---

### Post by Bucky Ball on 2009-01-04
It may have something to do with the fact that you are using a wubi install, and not an install on dedicated partition. Not sure.

---

### Post by PanicIRAQ on 2009-01-04
> **Bucky Ball said:**
> It may have something to do with the fact that you are using a wubi install, and not an install on dedicated partition. Not sure.

Alright thanks.  Yeah I have been a Windows user for years now and I'm slowly trying to make the move to Linux.  That's why I liked the Wubi installer so that I can run both.  Is there anyway that I can reverse these updates either from ubuntu or from my Windows?

---

### Post by Bucky Ball on 2009-01-04
Not having much experience with wubi installs, I'm not sure, but there would definitely be a way of uninstalling it. Have you tried going to Settings/Control Panel/Add/Remove Applications (I think) and unistalling it from there? Apparently that is the way.

If you have a spare drive or some spare space on your windoze drive that you can clear out and make some free space, you can dual boot your machine (I have three dual booting with XP or Vista) and that will be both faster and you won't get so many probs. The grub installer will pick up your windoze install and add it to the menu list. There are some good sources for info on dual booting, most notably this one:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I use 8.04 LTS personally as it has support for the next two and a half years and is stable (LTS = long term support). Not saying 8.10 isn't, but most of the questions seem to be about it. Having said that, the more people that use and share their experiences of 8.10, the more stable it will become. :)

---

### Post by jamesstansell on 2009-01-04
> **PanicIRAQ said:**
> Alright thanks.  Yeah I have been a Windows user for years now and I'm slowly trying to make the move to Linux.  That's why I liked the Wubi installer so that I can run both.  Is there anyway that I can reverse these updates either from ubuntu or from my Windows?

I'm not speaking from any wubi experience, but in general the easiest way to backout the updates would be to use a backup or to re-install.

If I understand correctly, with wubi ubuntu is installed into a single file on your windows system.  So if you are doing backups in windows you may be able to just restore that file.

On the other hand, if updates are hosing an install (even a wubi install) then there is a serious bug somewhere.  (Assuming of course that the fault doesn't lie with operator error, which it doesn't sound like so far.)

In general the more you can say about what steps you did and what you see the more someone will be able to help you.

One question I have is about disk space.  In an ubuntu terminal window, what is the output of the "df" command?

---

### Post by PanicIRAQ on 2009-01-04
Alright thanks again to the both of you.  I am in college and taking Linux that's why I installed it to try out.  I did like what I saw even just from the literally two hours I was on ubuntu so I am going to use your information about dual-boot and try and get it hooked up.

As for the "df" command I will log back into ubuntu and try it out as well as the Add/Remove function for the updates.

---

### Post by PanicIRAQ on 2009-01-05
Alright I have found the fix thanks to a thread in the forums I read in the Wubi section.

Turns out 2 of those 213 updates that you have immediately after you install Wubi are the cause of my wireless troubles.

avahi-autoipd
avahi-daemon

They are updates that somehow mess up connections through wireless and wired.  Thank you guys again for the help.

---

### Post by Bucky Ball on 2009-01-05
A pleasure and nice work! You should go well in the Linux class! So now you know something about wubi and hopefully this thread can help out others.

Good luck with it all and keep asking questions ... :)

---

