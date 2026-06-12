---
title: "s3 savage 8 3d card, can lucid make its 3d capabilities work?"
date: 2010-06-17
forum: Hardware
---

### Post by spaceshipguy on 2010-06-17
I have an old laptop :mad: but Ubuntu Lucid works fast and stable :p
All except 3D acceleration. I have an old, old card. A Prosavage8 VT8375 km266/kl266 from S3 Inc. Almost all the threads where people were actively trying to get these things to work come from about five years ago. But there are always poop SOBs like me bumping them in the hopes of an answer.

Most threads are tales of woe, but [in this thread they got 3D working on savage]("http://ubuntuforums.org/showthread.php?t=32043") , working good enough to play games.

But the thread says, **"This is for Ubuntu Breezy ONLY**. Please do not use this howto on  any other subsequent releases (Dapper, Edgy, etc)"

So my questions.

Is this the savage driver that now comes as standard and my laptop uses?
If so is there something I need to do to turn 3D on? (I don't like editing xorg, and I heard Lucid tries to ignore it, but I will if I need to)

If this is something clever and different that didn't make it into Lucid:-
Why Breezy only?
The solution does not seem to require messing with xorg, so in theory it is doable with Lucid, or am I missing something?
Would copying and pasting the commands from the first post into a terminal totally bork my system?
How would I update them for Lucid?

This post turned into a bit of a long-winded ramble, but if anyone managed to plough through it and come up with any answers I'd be glad to hear them.

---

### Post by tormod on 2011-08-08
Late reply, just searching for unanswered savage posts :) The savage cards now have 3D support out-of-the-box, that's why that old post was for Breezy only. There was a kernel bug that just got fixed in kernel 3.0 so upgrading to this is recommended. If on 10.10 make sure you have all updates since it released with a bug.

---

