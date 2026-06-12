---
title: "Quick user change problem"
date: 2008-10-27
forum: General Help
---

### Post by soho2014 on 2008-10-27
I am wondering if anyone else has encountered this problem with the release candidate of 8.10.  I notice that if I try to rapidly change from one user to the other, I get the error message:

"Graphic System Error:
The graphical interface which is needed for graphical logins did not start properly.  The X-window system or GDM may be misconfigured.

The X server failed to finish starting 3X failed.", and it brings me back to the original user place that I started in.

I am still able to choose logout and log into as another user, but as a quick change, I'm unable to do that.  I upgraded to 8.10 rather than clean install, and I have no other errors for this system that I can recall.:confused:

---

### Post by soho2014 on 2008-10-28
In my fumbling around trying to solve this problem, I managed to disable the nvidia driver, and then I found that it solved the problem.  Unfortunately, the screen didn't look as nice without that driver being used, so I reinstalled the use of the nvidia driver somehow, but sadly, the problem with the quick user change has re-appeared.  So the problem seems to rest with this particular nvidia driver, but I'm not sure how to determine exactly what the driver is.

---

