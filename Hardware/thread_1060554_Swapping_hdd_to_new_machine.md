---
title: "Swapping hdd to new machine?"
date: 2009-02-04
forum: Hardware
---

### Post by silverbullet007 on 2009-02-04
Question is.. Would it be a bad idea to pull the hdd out of my existing desktop, swap in a new motherboard and proc (changing from Intel to AMD) then replace the drive?  Whats the chances everything will work?

I realize with different hardware comes different drivers and different ways the hardware is recognized.  In a Windows pc this would be disaster most likely.  However I've done it once with zero bad results.  Im currently running on an HP XW4300 workstation, Pentium D 3.4ghz.  The original machine was an XW4200 workstation.. yeah I know little difference but the proc and obviously motherboard did change.

---

### Post by silverbullet007 on 2009-02-08
No one?

Even if it's a stupid question and I'm the idiot for asking.. someone tell me :-)

---

### Post by n5wy on 2009-02-08
I'll take a stab at this. I think its probably a bad idea. 

Yesterday I spent the whole day fixing a similar issue on my machine. I had copied the list of installed packages from my laptop to my desktop and thought, great now they will have the same programs on both. 

The two machines have different hardware, so the video, wireless NIC, wired NIC, etc got screwed up. I manually had to go through groping in the dark via cli to get stuff fixed to where it would at least login and not crash the x-session. Now I will work on sorting out the rest of the mess. I am trying not to do a fresh install, but might get there if I cant make more progress on the stuff I broke.

---

### Post by shad0w_walker on 2009-02-08
I did this less than 5 months ago (Finally moved to Core2duo from Athlon 64) and basically everything detected out of the box. You may have to reconfigure things like Xorg but as long as you don't have a processor specific kernel, it should be fairly safe.

Even if it doesn't work though, the worst case is you have to reinstall anyway. Just be prepared on the off chance and give it a try. If it works, horrah, if not, you're prepared to deal with it anyway.

---

### Post by silverbullet007 on 2009-02-09
Excellent information there.. 

Another question here though.. aside from xorg.conf, are there any other files that I should copy to a safe folder prior to making a swap like this?

Or perhaps a method of "backing up" my current system config so in case that first boot in a new machine wont overwrite what I've changed so far?

---

