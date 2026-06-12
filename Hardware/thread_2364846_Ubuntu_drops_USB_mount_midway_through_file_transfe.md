---
title: "Ubuntu drops USB mount midway through file transfer"
date: 2017-06-28
forum: Hardware
---

### Post by rogersma on 2017-06-28
Strange problem when I use "sneaker net" to transfer files between two Ubuntu machines at home.  I move files onto a 16GB USB stick on one machine, verify the files are there (e.g., open directly from the stick), unmount the stick, plug it into the second machine, start copying files, then suddenly the mount fails.  Unplug the stick, wait a couple of seconds, then plug it back in.  Sometimes I can finish transferring files, sometimes I must repeat the process.

As a consequence, I've learned never to move (mv) files but only to copy (cp) them in case the process fails.  Otherwise files get truncated.  It's extremely annoying but using cp instead of mv at least means I'm not losing data any longer.

I've tried this with ext4 and with FAT systems on the USB, and I've tried it with several different USB sticks (4GB up to 32GB), but all combinations exhibit the same behavior.

One machine is running 14.04 while the other is on 16.04.  I'd really like to think it's not OS version incompatibility!

In all cases I allow the machine to automount the USB, and there doesn't seem to be any problem.  Only once I start copying files do I see the problem.

I've not found this particular issue online, but I can't believe I'm the only one who's seen it.  Any ideas most appreciated!

---

### Post by Autodave on 2017-06-28
I really don't have an answer for you except that I personally have never heard of using the "move" command except from one part of the HD to another part, or from one machine to another directly hooked up by a cable where I could have the other machine's file system visible on the first machine.

I would use the cut and paste to put them on the USB stick and again the cut and paste to take them from the stick to the other machine. I don't see that using any more time or resources. And, much less chance of losing data.

---

### Post by rogersma on 2017-07-04
Unfortunately Cut and Paste have the same issue as mv (except for the GUI I think it's the same thing, no?)  Copy/paste at least has the benefit of saving the original.

So far, the most robust method seems to be rsync (strange, but true).  Possibly someone who knows cp, mv and rsync intimately could explain why.

For the moment I'm happy to consider the issue closed, but I would still be interested to know why the mount stays up with rsync but not with cp/mv...

---

