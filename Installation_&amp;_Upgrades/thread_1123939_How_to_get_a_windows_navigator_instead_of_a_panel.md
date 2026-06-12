---
title: "How to get a windows navigator instead of a panel?"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by connorh123 on 2009-04-12
The title says it, does anyone have a program like this? Perhaps a wbar or a Avant-Windows-Navigator? If so, I'd love to have one with a screen shot attached.
Thanks.

---

### Post by Partyboi2 on 2009-04-12
Awn
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

kiba dock
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

cairo dock
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by raymondh on 2009-04-12
here's mine using avant window navigator

---

### Post by raymondh on 2009-04-12
> **raymondhenson said:**
> here's mine using avant window navigator

ooops ,,,

---

### Post by connorh123 on 2009-04-13
For some strange reason AWN doesn't work. It went into applications/accessories, and then when I click on it, a screen pops up and goes away, all I could read from it was something about compiz.

---

### Post by raymondh on 2009-04-13
> **connorh123 said:**
> For some strange reason AWN doesn't work. It went into applications/accessories, and then when I click on it, a screen pops up and goes away, all I could read from it was something about compiz.

Do you have visual effects turned on?  Right click on desktop, change desktop background, visual effects to normal or extra.

Do you have CCSM (CompizConfig settings manager)?  I think AWN requires compositing to work.

If both (above) are ok, you need to run AWN at first.  Alt F2 and type avant-window-manager.  Then, you need to add AWN to sessions (system > preferences > session)

Let us know.  Good luck.

Enjoy.

Raymond

---

### Post by connorh123 on 2009-04-13
Can't run as normal.
About that compizconfig, how do I get that?
EDIT: This is what it says when I try to run it 
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

---

### Post by raymondh on 2009-04-14
System > Administration > Synaptic Package Manager.  Search for CompizConfig-Settings-manager and click.  It'll also "mark" necessary packages to run Compiz.  Click install.

Also ..... check if you have drivers (graphics) installed.  System  > Administration > hardware drivers.  Let it look for drivers and activate.

Now, go see if you can enable normal or extra in visual effects.  If you remember, right click desktop > change desktop background > tab visual effects.  If you prefer, system > preference > appearance

If abled, go alt+F2 and run avant-window-navigator.  Remember to include AWN in your sessions.  command is avant-window-navigator

Some reads for you as a guide:

[http://wiki.awn-project.org/Installation](http://wiki.awn-project.org/Installation)
[http://wiki.awn-project.org/FAQ](http://wiki.awn-project.org/FAQ)
[http://tombuntu.com/index.php/2008/11/11/installing-and-setting-up-avant-window-navigator/](http://tombuntu.com/index.php/2008/11/11/installing-and-setting-up-avant-window-navigator/)


Good Luck.  Enjoy

Raymond

---

### Post by connorh123 on 2009-04-14
Thanks. I fixed it by putting my visual effects on extra, thanks for the help :)

---

### Post by raymondh on 2009-04-14
> **connorh123 said:**
> Thanks. I fixed it by putting my visual effects on extra, thanks for the help :)

If you're thanking me .... you're welcome :)

If dilemna is solved, I think the forum staff would appreciate you marking the thread solved.

Enjoy Ubuntu.  As I always say, the learnings here with Ubuntu/linux easily transfer to any OS.

Best of Luck,

Raymond

---

