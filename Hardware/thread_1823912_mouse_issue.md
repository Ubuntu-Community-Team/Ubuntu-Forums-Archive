---
title: "mouse issue"
date: 2011-08-12
forum: Hardware
---

### Post by acidincense27 on 2011-08-12
My mouse keeps messing up on me and it's starting to do some damage and causing VERY much frustration. I have 11.04 Natty, and these issues started up about a month ago. I've been just dealing with it but I've seriously had enough now. Here's what's wrong.

The clicks are being registered multiple times. I know it isn't the mouse because I've tried two other ones and it still happens. If I try to open a new tab in my browsers (Firefox or Chrome) by using the middle-click button, it opens one to four tabs each time, all the same. I'd say three out of five times it does this. If I right click something, it'll sometimes think I've right-clicked twice and choose the first option on the right-click menu. For instance, I was trying to delete a video file by right-clicking it yesterday. Before I could even choose what option I wanted, it chose the first option, Play with VLC. I right-clicked three times trying to open up the menu and it didn't work. This caused three instances of VLC to be opened and it ate up A LOT of my memory. It took like twenty minutes to get the sys. monitor to open so I could kill the processes.

I'm sorry for being so worked up about it, but it's so very frustrating. Does anyone know what this issue might be and how to solve it?

---

### Post by Bladeforger on 2011-09-15
Yeah, me too!

Clunky way to handle it is with a very deliberate mouse press and a release half a second to one second later.  Your problem is with Natty.  Mine is with Karmic.  Looks like it's an ongoing problem that doesn't affect all mice.  Maybe I'll go get another rodent and try that.

---

### Post by acidincense27 on 2011-09-15
No, see it's not the mouse. I've tried four different ones and they all have the same problem. It's got to be some sort of bug because it happens in Firefox, Chrome, and when I right-click various things on the desktop.

---

### Post by sanderd17 on 2011-09-15
Have you tried it on a live environment?

---

### Post by Bladeforger on 2011-09-15
> **acidincense27 said:**
> No, see it's not the mouse. I've tried four different ones and they all have the same problem. It's got to be some sort of bug because it happens in Firefox, Chrome, and when I right-click various things on the desktop.

I'm curious if all the mice you've tried were USB or if any of them were the older PS/2 hook-up.  There has to be some reason why:
1. The problem did not appear on my computer until about two weeks ago and
2. The problem does not exist on ALL computers running Ubuntu--or even all computers running Karmic and/or Natty.

Moreover there has to be some good fix besides upgrading--especially for you because Natty should still be supported.

> **sanderd17 said:**
> Have you tried it on a live environment?
My Karmic is live.

I can't remember if the problem appeared immediately after an update or not... is there a history file somewhere I could look at?

---

### Post by sanderd17 on 2011-09-16
could someone try mev to see if their clicks are really registered as double clicks?

[http://manpages.ubuntu.com/manpages/natty/man1/mev.1.html](http://manpages.ubuntu.com/manpages/natty/man1/mev.1.html)

---

### Post by Bladeforger on 2011-09-24
> **sanderd17 said:**
> could someone try mev to see if their clicks are really registered as double clicks?

[http://manpages.ubuntu.com/manpages/natty/man1/mev.1.html](http://manpages.ubuntu.com/manpages/natty/man1/mev.1.html)

Many thanks, Sanderd, for your response and willingness to help.  I didn't get around to researching mev.  

Rather, I tried to upgrade to Lucid.  It didn't go well.  I ended up finally with an unbootable system that no amount of tweaking grub2 would fix.  (Kept the old drive for backup but Karmic was the problem all along.)

Since I had to set up a _whole new system_ with all the parameters, wiping the new hard drive clean, and finding packages to install, and getting the VMs working again, and setting up the samba shares, and figuring out all over again how I got KDE3.5 installed, I decided this time to try Linux Mint.  There were two reasons for that:
1. I was frustrated with the upgrade to Lucid going awry... and Linux Mint uses a different approach with a methodology to backup first data files and second a list of installed packages.  After this, a clean install is recommended.  Seems okay; I'll find out in 2013.
2. I also was not happy with the idea that in 2013 my upgrade would be to a version of Ubuntu that has Unity with no option for classic menus.

All this because of one little clicking problem with the mouse.  

I do, indeed, appreciate your attention, and I hope that whatever was causing the mouse problem doesn't persist for all eternity and keep coming back in later versions, after all Linux Mint is built on the Ubuntu Linux.  It seems to be a nonissue with Mint Isadora, which is built on Ubuntu Lucid.  If it happens again, I'll go buy mice until one works. :popcorn:

Keith

---

### Post by sanderd17 on 2011-09-25
I hope you did right by choosing Mint, but I'm becoming a bit afraid of it.

Mint had enough developers to maintain their own software center and their own menu, but I doubt they will be able to maintain their own DE or even DE shell. And they have to do that because they don't want to use the gnome shell or Unity.

Anyway, I hope it all turns out well for them. I really liked Mint in the past.

---

