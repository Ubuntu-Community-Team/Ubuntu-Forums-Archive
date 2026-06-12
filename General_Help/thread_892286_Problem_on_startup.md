---
title: "Problem on startup"
date: 2008-08-17
forum: General Help
---

### Post by Mashy on 2008-08-17
When I tried to start up Ubuntu (hardy) this morning, it came up with ```
init:ttyX main process ended, respawning
```,
X being a number from 1 to 6, or so.

This didn't seem right, it's never done that before, so I rebooted my computer and it didn't even get to that part, it got stuck on the word 'GRUB', where it would usually give my two seconds to press escape, it didn't and wouldn't progress.

The only thing that I think could have caused it was yesterday, where I tried to use ubuntu (it's on an external hard drive) at a friend's house. We selected the wrong type of monitor, and everything went weird, but we phoned my friend (who knows alot about linux) and told me things to type into the terminal, which fixed it (something to do with xserver and xorg and sudo or something like that).

If anybody knows how to fix this, then please do tell, as this is driving me mad.

Any help is much appreciated. 
Thanks.

Edit: Just tried again a couple of times, and it got past the scrolling bar, then some things appeared, something to do with plugins or something or other, and then the screen goes off, as though it was disconnected at the back of my computer.
But then if I press ctrl+alt+f2, the terminal window opens and the screen is back on and I can interact with it.
So I'm guessing that I should be able to type some command into here and it should make everything work again, hopefully.
Any ideas of what to do?

---

### Post by Mashy on 2008-08-17
Ok, because my installation of Ubuntu was new (I installed it on Friday evening) and I had nothing that wasn't already on my windows drive, I decided to reinstall Ubuntu onto the external hard drive.
Everything worked fine, until I updated the graphics card drivers (I have an Nvidia Geforce FX 5200), and then I restarted the computer, and I am having the same problem (where the screen goes off, as though it has been disconnected, but if I press alt + ctrl + f2 then it brings up the terminal fine).

Please help me with this. It's very odd. The drivers shouldn't do this, they worked on my previous Ubuntu installation until this morning.

Help, anyone?

---

### Post by Mashy on 2008-08-17
Hmm, I just tried it again, and tried to do the 'startx' command, which tried to connect to the xserver, but it failed (I think probably because it cannot connect to the internet unless I do it from the desktop. I have a speedtouch 330 which I use some program thing with, I'll find  the website if it's needed). 

I then tried 
```
sudo dpkg-reconfigure xserver-xorg
```
which is what I typed yesterday at my friend's house, only this time it did exactly the same, but had no effect.

But when I try rebooting it now, it comes up saying that xserver is not working, do I want to try and configure it, I say yes, and it comes up saying that it's failed, xserver has been disabled, and I should re-enable it again if I want to use it.

Please help!

If nobody knows how to help, then I will try to reinstall ubuntu again. How should I go about updating my graphics card drivers to avoid this in future?

---

