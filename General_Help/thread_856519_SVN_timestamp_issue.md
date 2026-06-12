---
title: "SVN timestamp issue"
date: 2008-07-11
forum: General Help
---

### Post by KingTermite on 2008-07-11
I've been working on setting up this local SVN server on an Ubuntu machine. It's a pilot to try to get our group to switch to SVN.

My latest problem is that when I update (commit) a file from a client (windows machine using TortoiseSVN), the client keeps the modification time of the file and not the commit time.

I really don't care which time is used, as long as they time in the windows computer and the one in the repository match.

So far the only way I've found is to delete the file and repull it from the repository (there has GOT to be a better solution).


But the real problem is that the time stamp stored on the repository appears to be GMT, not local time. So when I pull it back it's about 8 hours off (I'm at GMT - 8).

**How can I ensure subversion uses local time, not GMT?**

---

