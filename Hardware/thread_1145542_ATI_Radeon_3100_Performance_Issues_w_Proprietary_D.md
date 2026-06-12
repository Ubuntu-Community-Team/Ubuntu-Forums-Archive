---
title: "ATI Radeon 3100 Performance Issues w/ Proprietary Driver"
date: 2009-05-01
forum: Hardware
---

### Post by gerowen on 2009-05-01
I have tried the one packaged with Ubuntu, and then downloaded the one from amd.com and still have this issue. It's not a "huge" issue, but it's in regards to 3-D gaming. The issue is that there seems to be a consistent "start & stop" behavior that happens randomly while doing some of the following things.

1) Playing World of Warcraft w/ Wine
2) Playing Nintendo 64 games with Mupen64

Both of these activites run pretty good, but it's like, it'll run fine for 5 seconds, and then it's like it'll skip when it drops a frame instead of transitioning to the next frame smoothly. It's like millisecond pause that randomly happens when doing these two things. I haven't yet tried any 3-D Linux games like Nexuiz, but I'm wondering if this is an issue with the ATI driver or with Xorg or what? This card has 256MB of video memory, and all these things worked fine in Windows (the machine shipped with Vista), now I'm not comparing this to Windows necessarily, I'm just noting that the video card is more than capable, so the issue is obviously software related.

Edit: I am using the Linux version of Mupen64.

---

### Post by push_back on 2009-06-16
Well, I have tried neither of the two above programs, but I can report other problems with the flgrx proprietary ATI driver for this card in 9.04.  Large white spaces, as can be found in websites like google and wikipedia, often get buggy and diplay large black rectangles with jagged edges, seemingly at random.

Also, about once a day I am forced to restart X because the graphical display messes up completely.  It's a very strange bunch of behaviours: Not updating windows unless I switch viewports is one.  The rest are...hard to describe, but clearly graphical malfunctions. 

Anyhow two of us have identical systems, and we both came across this bug.  Changing to the open source driver fixed this, but of course isn't compatible with and desktop effects.

---

