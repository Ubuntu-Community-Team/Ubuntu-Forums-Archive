---
title: "Install Troubles"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by nintendude794 on 2009-10-06
Howdy.  I heard about Linux in a recent HowStuffWorks podcast, not that I haven't heard of it before, and decided to try it out.

Yet, I've had some trouble getting 9.04 to work on my Windows 7 desktop.  I've burnt it to a CD and booted to it.  I select English, then "Try without any change";  it does some loading, including an Ubuntu logo with the alternating marquee progress bar, which switches to a regular loading bar.  That finishes, then it pulls up a blank command prompt screen, does more loading until I see a blippy version of the Windows 7 login screen.  That disappears after a few seconds and then it loads an Ubuntu login screen, which says, under the username field, "will login in ten seconds".  My keyboard and mouse don't work, and it doesn't login: not within ten seconds, not ever.

So, I decide "Well, okay.  I'll try installing it then."  I emergency shut down my computer and reboot it, this time selecting English and Install.  It does the Ubuntu loading screen again...  WOAH.  This time, instead of freezing at a black screen, it gives me a bunch of gibberish, that looks something like this:
[   139.351218]   [<co1e245d>]  ? bio_free+Ox3d/0x50

There about a dozen and a half more lines, all beginning with that same first bracket and closing with different middles and ends.  Should I redownload and/or reburn 9.04 to try all this again?  Or is there some other solution?

---

### Post by PherricOxide on 2009-10-06
Hm, it sounds like maybe the x-server is crashing. What sort of hardware do you have? Specifically video card.

---

### Post by Jimmyfj on 2009-10-06
You burn the iso out again but this time make sure you burn the disk at the lowest possible speed to avoid write errors.

Then, if you keep having troubles list the specs of your computer here: CPU, Graphics card and so on. That makes it easier to find the flaw.

---

### Post by berksted on 2009-10-06
There's a chance the cd you burned may be corrupted. You should be able to at least boot the live cd and test drive ubuntu before installing. You might try to burn another copy. It also wouldn't hurt to try 8.04 as well.

If that doesn't work you may have some hardware conflicts (as suggested by pherric oxide). In that case, what brand desktop are you running (custom, HP, Dell..etc) and video card ?

---

### Post by nintendude794 on 2009-10-06
Oh, that reminds me.  I did put it in my Mac and boot from it, to try without making changes, and I got to try it.  I like it, I just want to actually install it to my Windows desktop.  My MacBook's drive is full, with only 3GBs left on OS X's 90GB partition and several GBs available on the Win7 partition. And I like the fact that Ubuntu gives Windows a dual boot mechanism; if I can ever get Ubuntu to install to my Windows desktop, I'm curious to try installing Leopard.

When I burnt the disk from OS X, the lowest possible speed option was 8x, so I'm redownloading 9.04 to my Windows desktop to hopefully burn the ISO at 4x, or some speed lower than 8x.

Now what might the issue be, after clarification that I got it to work on my MacBook?  I also started the install process on my Mac and got to the partition screen on there.  I quit after that because I don't want to put it on the Mac, as I've said.

---

### Post by nintendude794 on 2009-10-06
Brand: Custom; my godfather built it for me.

Processor: 2.2 Ghz AMD Athlon XP (128 KB primary memory cache; 512 KB secondary memory cache)

Graphics Card: ATI RADEON 9600 Series

Hope this helps with your advice.

---

### Post by nintendude794 on 2009-10-08
Xubuntu 9.04 struggled as well.

I've installed Ubuntu 8.04, and it works up to the point where it's loading my desktop: the graphics just won't cooperate.

So I'm about to download Xubuntu 8.04.

---

