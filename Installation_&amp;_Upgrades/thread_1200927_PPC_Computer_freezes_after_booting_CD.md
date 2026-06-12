---
title: "PPC Computer freezes after booting CD"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by QuigleyQ on 2009-06-30
I recently burned a CD of Jaunty Jackalope for PowerPC. I might have screwed up making the CD, so here's how I went about it. I downloaded 9.04 for PowerPC from [http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/) I couldn't find an md5 hash to compare it against, so I downloaded it twice and compared the hashes of those. They were identical, so the download was probably intact (correct me if I'm wrong). I then burned it to a CD, which went fine. Now, I can boot from the CD, but all I get is a black screen with some white text. It says to input something after "boot:" I pushed enter like it said, and got "Loading, please wait..." which was quickly replaced by an underscore. The computer doesn't respond after that. I tried putting live, live-powerpc, live video=ofonly, live-powerpc video=ofonly, after the "boot:", but everything gets the same result. I am using a beachball iMac running Mac OSX, Version 10.4.11, uses a 700MHz PowerPC G4 processor, and has 640 MB of RAM. Can someone tell me what I did wrong?

---

### Post by shishko on 2009-07-09
Hi,

I'm having exact problem on my Quicksilver G4/867! Did you find any solution so far?

---

### Post by Donzieja on 2009-08-10
I'm having the same problem on my g5.  Im gonna try the alternate install cd.

Also, you should try 8.04 first then upgrade to 9.04.

---

### Post by ronparent on 2009-08-10
Using the live cd, try hiting f6 at the screen after language selection. Use the spacebar to deselect apic and lapic and see if you can continue to boot into a live session. This isn't a definitive solution, but it worked for me on two pc's and a laptop that would otherwise freeze.

---

