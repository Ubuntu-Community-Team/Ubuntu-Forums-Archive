---
title: "Back up specific partitions (in time machine like manner)"
date: 2008-11-04
forum: General Help
---

### Post by sans on 2008-11-04
(Hardy Heron)

Hi everyone

I was hoping you could show me an app (or pseudo-rsync-code) that will let me back-up specific partitions. Preferably in a time machine like manner.

Here's what I've tried so far:

- TimeVault which crashed.
- Flyback which would start back up the inclusion folder but not its contents.
- Writing my own rsync script but I couldn't get past the first hurdle of (conveniently) setting specific sources using --include-from.

I like the time machine approach and its use of symbolic links. However, I'm more than happy if it is a simple incremental back-up (to that end, I tried an app called "Keep" but it kept complaining about my back up drive -- a mounted USB disk.)

I'm not the type that needs his hand held and do prefer finding / figuring stuff out on my own but I've come to realize I'm playing with my livelihood :) Every extra day without running back-up is one too many (I previously kept all my files on an OSX box.)

Anyway, anything you can share... Thank you!

---

### Post by handydan918 on 2008-11-04
Is there any reason rsync as a cronjob wouldn't work for you?

---

### Post by sans on 2008-11-05
Handyhan, no, not at all. I'd prefer it I think. What matters most is that I can set which partitions/folders to include.

For example, I'm just looking to back up these
/media/external/allespast/active/ 
/media/external/logodebut/active/
/media/assets/fonts/

And nothing else on those volumes (or the system or /home or elsewhere.)
It would also be great if it would keep the structure intact (so a backup resides at /backup/media/external/allespast/active.)

I've been trying that using include-from (and exclude-from) where I keep a text file with all the folders that need to be included. And that's where I get stuck. Storing files in a time-machine like manner would be an added bonus but not necessarily at all.

---

### Post by beercz on 2008-11-05
Is [rsnapshot]("http://rsnapshot.org") what you are looking for?

---

### Post by sans on 2008-11-05
Oh wow, looks like it does!
I'm going to give that a try now :)
Thank you Ian!

---

### Post by beercz on 2008-11-05
> **sans said:**
> Oh wow, looks like it does!
I'm going to give that a try now :)
Thank you Ian!
You are welcome.

It's a bit tricky to set up but once done, use cron to run it automatically.

I use it every day on several machines (including backing up to remote machines over the internet) and all my backups run like clockwork.  I output my backups to log files so I can check if my backups are successful or otherwise (which is very rare).

Ask if you need more help.

Good luck.

---

### Post by sans on 2008-11-05
Wow, so far so good!
I really need to understand cron though!

I did a few test runs... can I safely remove the contents of my snapshot directory or will that mess up the count (currently I have hourly.0 and hourly.1)

---

### Post by sans on 2008-11-05
Also, would it be possible [not] to set a relative path inside the snapshot root?

The man suggests "local/", which would result in something like:

*/backup/hourly.0/local/things-i-backed-up*

whereas I would prefer:

*/backup/hourly.0/things-i-backed-up*

---

### Post by sans on 2008-11-05
I realized rsnapshot du  relies on this, so the above question can be ignored.

---

