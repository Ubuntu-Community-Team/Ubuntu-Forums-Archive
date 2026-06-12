---
title: "amaroK and Kaffeine won't play music"
date: 2005-12-05
forum: General Help
---

### Post by McSnickered on 2005-12-05
After I upgraded from Hoary to Breezy, amaroK and Kaffeine stopped playing music.  I can add to the play lists, but Amarok doesn't do anything when I hit play and Kaffeine throws an error saying, "Could not get/set settings from/on resource".  When I try to stream music with amaroK, it says it's buffering and when it hits 100% it goes back to 0% and starts over.

I'm not too perturbed - it's part of upgrading.  But I would be very grateful if anyone can share if they've encountered the same issue.

Thanks,
Mac

---

### Post by McSnickered on 2005-12-05
I'll answer my own question.  After some more searching under "gstreamer" I found some others with similar problems.  I installed kaffeine-xine and amarok-xine and then changed the settings in each to use the xine engine rather than gstreamer.  That fixed up both.

---

