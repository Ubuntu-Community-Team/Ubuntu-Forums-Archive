---
title: "Some kind of SERIOUS ERROR: Won't load past login"
date: 2008-09-30
forum: General Help
---

### Post by dai_vernon on 2008-09-30
Here's the situation: I'm running Ubuntu Hardy 8.04.1 on a Compaq Presario F700 that was working just fine until 20 minutes ago.

I accidentally Alt-F8'd or something and it caused my screen to change to the crawl when you have a non-quiet boot.  Like a page of terminal output but no prompt.  I did a hard reboot (power button) and noticed a few things:

1) On "Loading restricted drivers..." there seemed to be some kind of ndiswrapper screwup.  I had recently deleted my wireless driver because my wireless had failed and was working on reinstalling it yesterday.

2) Nothing else was out of the ordinary except the entry "Loading Winbind Daemon winbind..." or something like it was met with a red [fail] on the other side of the screen.

When I get to a login screen, I can log in as myself, and I get a mouse, but the orange screen that appears before the desktop loads hangs indefinitely.  A white square appears in the upper left hand corner, but I can do nothing but move the mouse.  No click, no hotkeys to open things, no terminal, no ctrl-alt-delete, no nothing.  I need to hard reboot to get out of it.

Booting in recovery mode, I can get to a root terminal and see all my stuff, but no application I load will a) load a gui, or b) connect to the internet.  I tried using lynx to get online and irssi to get into IRC.  Finch just crashes.

Currently I am burning a live CD to try and get back in there and figure out what the hell, but I need advice as to what might be wrong.

My only idea at the moment is back everything up and do a complete hardy reinstall; which I do NOT want to do.

What's going on? ](*,)

---

### Post by dai_vernon on 2008-09-30
Ok, so

I went to the library and burned a live CD to try and look at what the hell was going on, and I came home and booted the thing, but it for some reason didn't boot from the CD.

I saw all the regular errors but kept through to the log in screen, where I logged in just to see what happened, even though I KNEW it was still broken.

And it worked.

I'm typing from hardy on my ethernet connection right now.  What the hell?  What do those errors mean in my verbose boot?  Why did it decide to work?

---

### Post by dai_vernon on 2008-09-30
Update #2: It appears to only be screwing up when I boot with my ethernet cable in.

Can anybody explain this?

---

