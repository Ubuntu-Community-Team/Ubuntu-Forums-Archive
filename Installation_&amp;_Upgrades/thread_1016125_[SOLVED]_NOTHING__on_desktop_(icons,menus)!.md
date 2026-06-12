---
title: "[SOLVED] NOTHING  on desktop (icons,menus)!"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by Donalb on 2008-12-19
Hey all, Just did a fresh 8.10 install on an old laptop (that had been dual-booting 8.04 & XP).
Did the usual stuff in a few steps, first Updates, then Ubuntu-tweak for the restricted repos, added 2nd user, installed some apps (Thunderbird, amarok, kalzium, awn) added some ff extensions, some deletions (Evolution mainly), Ubuntu Studio theme thru Synaptic. Everything seemed fine as I progressed. But after the last reboot the desktop comes up BLANK. (I can't remember I might have done 3 reboots.)

No icons, no App menu, no clock, network, etc. Tried launching Terminal or anything from the F keys but nothing except System Monitor comes up <Ctrl-F1>.
Right click on the desktop brings up the Create Folder, Change Desktop etc options bu they're no use to access any Apps.(Although I can use that to access Nautilus and the file system...)
I had allocated the Wins (Super L) key also as an Applications menu Launcher. That doesn't work either.
Access to Shutdown can be down thru Power key. A reboot does nothing.
I do have some supicion that it's the Ubuntu studio theme that might be responsible,but can't seem to delete it from the Change Desktop tab.  
 

I'm a bit stuck....Any hints?
There's no data, I <could> do a reinstall, but that wouldn't teach me anything.....!

(ps feel like an idiot but can't see that i actually did anything wrong)
 
Cheers

---

### Post by cariboo on 2008-12-19
I would suggest booting in recovery mode and at the menu select drop to root prompt. Once at the prompt type:

```
sudo apt-get install ubuntu-desktop
```

To see if that brings your desktop back.

Jim

---

### Post by Donalb on 2008-12-19
Thanks Jim.
That wasn't the problem, I tried it but it did nothing. i was wondering if something else was screwed up.

 OK, I decided to cheat after all and reinstall. Everything went fine.
Installed the same few apps. Left out Ubuntu Studio theme which I suspected.
Installed Ubuntu-tweak (latest version 0.4.4). Configured it, installed the extra repos, added a second Admin user (laptop is for my daughter since I can't afford a new one for her).

Logged out and back in......same problem. Only difference this time I have the 3 desktop icons (my computer, user home folder, trash) which I had set up to show in Ubuntu-tweak. Also when config'ing Tweak I had added the terminal to the right click options "open terminal here".

So this time I was able to get at the terminal, unlike the last.
So...
I uninstalled Tweak from the terminal, and removed the User also, and her home directory.
Logged out and back in. Everything ok! Desktop & menus back.
Created a new user for my daughter again, this time with Tweak gone.
Logged out and back in with her account. Everything still ok! Desktop & menus still fine.

So it seems to me the problem was Ubuntu-tweak and something with adding a 2nd user.?!?
For me, the cool thing here, is I'm gradually learning Ubuntu! I've been using it for 9 months. I think this is the first problem I've fixed myself,(well, enough to continue working).
But thanks for help, it's always good to know there's someone out there.

Of course, I'll still have to introduce my daughter to an older laptop, running some operating system she's only heard her geek dad mention!

But while she's in college, at least I won't be getting calls about virii and malware.

Regards

---

