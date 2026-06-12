---
title: "Can't boot the install CD"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by cestes on 2006-01-25
Here's an odd one:

I'm trying to put Ubuntu on my father-in-law's machine -- it's an older Emachines Etower600is (600 Celeron, 192MB RAM, 10Gig HD).   It's currently running WindowsME (ewwww) -- any valuable docs are off the HD and I'm clear to format it.

I can't boot the Install CD, though.  I thought it was just one that I downloaded and burned.  Then I rummaged around in my cd pile and found one of the official ones that I got in the mail.  Still no dice.  When it boots, it goes throught the POST, the CD spins, and then it just sits there with a black screen, cursor flashing in the upper left.

The CD is good... I just booted my desktop machine using that very CD and it pops right up.  The hardware looks OK -- I can boot Knoppix without any problems.  I ran memtest for a while with no errors.

Strange that only the Ubuntu CD which I know is good won't boot there.  Anyone ever hear of this before???

Thanks!

-Chris-

---

### Post by byen on 2006-01-25
try this for starters...
1.How about installing with the ACPI off option during install
2.Try disabling the Legacy USB support in the boot menu
3.Do you have a graphics card? might wanna look arnd for your type and see if they are any issues..

try this out and let us know if there is any luck!I see this is your first post... Welcome to Ubuntu! Hope we get you started! Goodluck!

---

### Post by cestes on 2006-01-25
Thanks for the pointers...

I tried the APCI - no luck.
Tried the Legacy USB - no luck.
The video is the standard onboard Intel video that's on the mobo; I'm guessing it's pretty vanilla.

I even played with some bios options about PnP Aware OS and the Large Disk Access Mode (DOS vs. Other) neither of which made a difference.

Really odd...

I'm wondering if the CD drive has a problem -- the one that was in there was really old and had frozen up.  I replaced it with one I had on the workbench inthe basement that's really old.

Still, it's booting the Knoppix CD that was burned right alongside my Ubuntu CD and from the same pack of blank CDs!

I tried some Fedora and that wouldn't boot either -- Knoppix must not be picky!

Thanks again!

-Chris-

---

### Post by cestes on 2006-01-25
Got it!

I swapped out the really, really old CD drive (may have been the first one I ever owned) for a less old one (1997 !) and Ubuntu is booting up as we speak!

-Chris-

---

