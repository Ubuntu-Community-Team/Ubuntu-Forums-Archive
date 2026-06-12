---
title: "system instability worsened after 8.04 -&gt; 9.04 upgrade"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-05-24
I've had my Ubuntu install for about 8 months now, and over the last month or so it started getting a little odd.  Programs were very unstable and crashed often (firefox especially) and I thought I had found the problem when I realized that I was booting grub from a different partition (and therefore not receiving any kernel updates, while still receiving all the package updates made for those kernels).  I figured if I was going to upgrade I would go all the way and upgraded to 8.10 then 9.04, so that I would be using the latest kernel and all the latest packages.

This has made things a lot worse.  Nothing seems to run 'smoothly' anymore, there is a pause whenever I try to close firefox, virtualbox no longer allows me to resume a saved session and crashes often, and everything just feels slower and sluggish.  I have evacuated to a Fedora installation on another partition, it has become pretty frusterating to use.

I don't have a lot of important data on here and I could probably just nuke it, but one of the reasons I came to linux in the first place was stability, when I was using windows I would usually backup and nuke installations every six months or so, just to keep it healthy.  I'd really like to figure out what's going on here and find a way to fix my install.  

Is there a way to do a filesystem/kernel repair install or something like that?

---

### Post by bhishan on 2009-05-24
Did you do a online upgrade? Why don't you try a clean install of 9.04.

---

### Post by v1nsai on 2009-05-25
Is there a way to do a clean install without losing all my data?

---

### Post by aurelieng on 2009-05-25
If you keep your ${HOME} on a separate partition, you can ask the ubuntu installer to keep it during the upgrade, while all other partitions (/, /var, etc...) will be reformated.

---

### Post by v1nsai on 2009-05-25
I've looked around for a way to mount my home partition separately but never really got my mind around it, could you link me to a good guide for doing that?

---

### Post by merlinus on 2009-05-25
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by v1nsai on 2009-05-25
I think I remember reading that article when I first migrated to Linux.  Didn't understand the commands and never took the time to figure them out, I don't like running commands I don't understand so I never did it.  Looks like all you do is put home in the partition, then tell fstab to mount it.  Easy peesy, thanks for that, everything just clicked in my head.

---

