---
title: "How safe would be to distro-upgrade to Jaunty?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by galvao on 2009-04-25
Greetings, some time ago (I believe it was the transition from Feisty to Gutsy) I've tried the automatic distro-upgrade and that ended up generating a lot of problems for me. 

I don't remember specifics now, but I've ultimately had to install from scratch. What I do remember, however was a lot of more experienced Linux users telling me that "dude, we *never* distro-upgrade". I was very impressed to hear that...

Although I'm well aware that backup is a needed and unavoidable process it's very painful for me to backup my whole home partition (> 40Gb), so I'd like to - once again - try the automatic distro-upgrade.

Well, I think you already guessed the point here, but the thing is I'm afraid to do it based on this past experience. My computer is old and tricky in terms of hardware (Nvidia drivers, more than one HD being one of them - where I will backup my data - a very old 60Gb and stuff like that), so the question is:

Is the automatic distro-upgrade safer/better/improved now? Is it recommended in my case (btw, I wanna upgrade from Intrepid to Jaunty)?

*If* I distro-upgrade and it fails horribly for some reason is there a fallback procedure, like (maybe) when grub displays the various kernel versions where you can choose an older kernel to boot from?

TIA,

---

### Post by cariboo on 2009-04-25
HAve a look at the [Release Notes]("http://www.ubuntu.com/testing/jaunty/beta") first. Then before you upgrade to Jaunty, make sure you comment out any ppa's and third party repositories, then make sure your current versions is up to date, then you can do the upgrade by pressing Alt-F2 and typing:

```
gksu update-manager -d
```

---

### Post by Tanker Bob on 2009-04-25
I upgraded last night from Intrepid to Jaunty using the Update Manager GUI and did not have any problems. The upgrade tool will automatically disable third party repositories, so you don't have to worry about that. The upgrade preserved my RAID1 and compiz-fusion setups and correctly updated for my 8800 GTS NVidia card. The result was a seemless experience, other than having to reinstall Flash support for Firefox. That was the only issue. You can read about my upgrade experience [here](http://reformedmusings.wordpress.com/2009/04/25/upgrading-from-ubuntu-810-intrepid-to-904-jaunty/).

YMMV, but if an upgrade doesn't work well, you can always follow-up with a fresh install.

---

### Post by galvao on 2009-04-26
Thank you all. I'll give it a shot.

---

