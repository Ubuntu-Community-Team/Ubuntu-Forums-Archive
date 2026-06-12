---
title: "session saving?"
date: 2008-09-20
forum: General Help
---

### Post by karleberts on 2008-09-20
Hello all,
Before I begin, I am using XUbuntu 8.04.
I've been having a bit of trouble getting my system to NOT save sessions, or reload the last session upon logging out/in.  I thought I had turned this off in the "Sessions and Startup" tab of the Settings Manager (unticked the "Automatically save session on logout" box), and I have tried messing around with sessions options at the login screen.  However it still seems to reload programs, even after reboots.  I can close most of them, but I'm pretty sure sometimes it loads things in the background that I'm not using, and I don't always notice right away.  I was just wondering if anyone could tell me all the config files that would control this behavior, because I must be missing something somewhere.
Thanks.

---

### Post by john.nicholls on 2008-09-20
You could go to the Xfce Settings Manager and check under Autostarted Applications to see if there is anything there that you don't want.

---

### Post by karleberts on 2008-09-23
I've checked there, and eliminated the programs that I don't want to start.  It's not that the same programs start each time I boot, either.

---

### Post by hyper_ch on 2008-09-23
what does it load?

---

### Post by karleberts on 2008-09-27
Well, it seems to change.  For example, I just booted up, and my terminal program started up.  I don't even think I was using the terminal when I shut down the computer, but I'm not totally sure.  I think for a while it would start AbiWord every time I would start up the computer, but something stopped that a while ago.  Anyway, I'm not sure if it's loading any other programs in the background that I don't even know about, and that's what I'm actually worried about.  It's not that hard to exit the programs that come up (I'd still prefer that they didn't come up at all) but I'd really like to be sure there aren't any processes being started that I don't see.

I don't know how many scripts should be starting programs whenever I log in, but I appreciate any help figuring out where to start checking.
Thanks.

---

