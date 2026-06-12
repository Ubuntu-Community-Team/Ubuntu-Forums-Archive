---
title: "random lockups"
date: 2008-09-24
forum: General Help
---

### Post by Naegling23 on 2008-09-24
I've been running hardy since its release without any problems whatsoever, until about a week ago.  I first noticed it when I would return to my computer, and it would have just locked up...frozen screen, unable to do anything including ctl atl bksp.  Yesterday, when I was trying to transfer media to a memory card, it got even worse.  I would have about 15-30 minutes of up time before the system would lock up.  Once the screen just went black, they monitor game me a signal not detected, and that was it.  I've heard some issues with hardy and stability, but I only recently started experiencing them, so was there a recent update that could have done this (im a kubuntu user, so kde updates could be something...oh, and compiz too)?  
Im also aware it could be a hardware issue, but I would like to eliminate software before I start trying to troubleshoot that mess.

---

### Post by Naegling23 on 2008-09-24
hmmmm, occassionally, when I start the computer up, I get a black screen, no beeps, no bios, nothing.  If I go away for a while and try again, it works.  This phenomina started a couple of weeks before the random lockups.  A google search on this topic suggests it might be bad ram....anyone want to second that?

When I get home, I'll try cleaning (gently with an isopropanol wipe) and swapping out my ram (ive got 2gb spread over 4 chips, so, ill just remove two at a time, leaving them paired).  Maybe this will solve my problem.

In all my years of building computers I always diagnosed bad ram from the beeping...I guess failing ram is a different story...learn something new every day I guess.

If anyone has any advice/info/opinions on my problems, please help me out.

---

### Post by Kevbert on 2008-09-24
If you think you have memory problems, try running memtest from the boot menu over several passes.  It may be failing as the memory warms up.  You've tried using a cleaner so I assume you don't have any dust problems (dust can be conductive). Also check all cables and that all cards are properly seated in their sockets.

---

### Post by Naegling23 on 2008-09-24
havnt cleaned them yet.  I cleaned out the case yesterday thinking that could be part of the problem, but it didnt seem to help.  I have 2 pairs of 512 sticks on ram for 2gb total.  Im going to pull all of them out, clean them, and put 2 back in.  If things dont work out, ill try the other two.  Hopefully this can solve the problem....of course that is if this is the problem.  Ill try the memtest a few times to see if that helps.  It could be as it heats up since the computer tends to fail after a while (tranfering data would likely be a big stressor too).

---

### Post by Kevbert on 2008-09-24
The only thing you should need to do is make sure there's no dust in and around the connectors on the motherboard.  The edge connectors on the memory cards should be bright and shiny (try not to touch these as static will destroy them.  The memory test should show if there's a chip problem or that the memory is not seated properly.  If you get any failures in the test try running the test without one or more sticks.  If you think you've found a suspect memory stick, try it in a different socket, in case it's the socket that's the problem.
Good luck, the tests will take a while, please be patient.

---

### Post by Naegling23 on 2008-09-25
well, I went home, opened up the computer, and removed all of my RAM.  I cleaned all four using isopropanol, one of them was pretty dirty, and I had to gently scrub the dust off (this could be the problem).  Anyway, I put two of the sticks back in, turned on the computer and ran memtest (thanks for the suggestion).  Everything came back normal, so I booted up.  The computer ran fine for the rest of the day until I shut it down at night (didnt put it under a full load, but I transfered some data which was where I first really noticed the problem).  My next step is to try out the other two sticks, and run memtest again to determine if they are bad, or were just dirty.  So, the answer appears to be hardware related.

---

