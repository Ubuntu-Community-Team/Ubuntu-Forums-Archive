---
title: "Corrupted system -- having trouble reinstalling"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2009-07-20
I presently have 8.04.3 installed but it is corrupted somehow.  I have no panels showing on my desktop so I can't start any programs.  Having spent several days looking for answers I am giving up.  There seems to be a lot of people having this same problem on distros from Hardy to Jaunty.  I have tried every suggested fix and nothing has worked.

I downloaded the latest 8.04.3 iso and want to reinstall the system from scratch.  The official documentation says I can select a "repair system" option but there doesn't seem to be such on option on the disk.  Fortunately, I have my home mounted as a separate partition, so I should be able to rewrite over the old root partition, right?

What is the best method to fix my broken system?  Using Windows to post this is like admitting defeat, but with a little help I hope I can turn this situation around.

---

### Post by merlinus on 2009-07-20
Since you have a separate /home partition, reinstalling is probably the easiest solution.  You can install into your existing / partition, but make sure not to format /home.

But be aware that some of the configurations and such in /home may be part of your problem.

---

