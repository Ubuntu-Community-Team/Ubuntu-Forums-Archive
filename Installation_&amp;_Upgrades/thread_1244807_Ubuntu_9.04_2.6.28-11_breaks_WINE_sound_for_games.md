---
title: "Ubuntu 9.04 2.6.28-11 breaks WINE sound for games"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by MisterBill on 2009-08-19
Hello everyone, I'm wondering if any of you have encountered a problem like the following (or, better still, have found a solution or work-around to it):

I have been using various versions of Ubuntu, starting with 7.10, as a platform (via the WINE compatibility layer) upon which to run Windows games, in particular Blizzard's popular "Diablo II Lord of Destruction" ("LoD"), and all has been well until now.

However, shortly after I dutifully installed the 2.6.28-11-generic kernel update, sound began behaving erratically in my WINE / LoD sessions. After about 15 to 20 minutes of game play, the sound simply shuts off :confused:, and although I can reset it by completely exiting WINE and restarting both it and my game, this is annoying.

Oddly, sound output outside the WINE session still works perfectly, and if (for example) I am running Rhythmbox as a GNOME task while I have Diablo going under WINE, even if the sound shuts off in the Windows emulation session, it still continues in the Rhythmbox session, so I'm pretty sure this is something going on with WINE... however, a kernel update should not do this kind of thing to an application like WINE. Doesn't anybody ever test for problems like this? (Or am I the "tester", in this case.)

Anybody got any guesses as to what's happening, or how to fix it? As a temporary measure, I can always boot into the previous kernel via the GNOME boot menu, but that's kind of a half measure. Other than for this issue, the computer (like the other 3 I have Jaunty and Intrepid loaded on) is working beautifully, even the DVD playback keys on my Logitech multimedia keyboard work perfectly... "go back to Window$? you've *got* to be kidding, mate".

BTW, this is on a HP Pavilion DV6000 laptop with 2 Gb RAM, nVidia Corporation MCP67 High Definition Audio (rev a1) as the sound h/w.

Cheers

Mr. Bill

---

### Post by running_rabbit07 on 2009-08-20
I think it was 2.6.28-15 that came out today. I don't use Wine but thought I would throw that out there. I think you can change the thread title if you edit your original post.

---

