---
title: "Fast User Switch is resetting existing logins"
date: 2008-08-02
forum: General Help
---

### Post by bsmith1051 on 2008-08-02
I have been using Fast User Switcher since 7.04.  Now it is standard in 8.04 but it's not working correctly.  Ever since I upgraded (about a month ago) it's been inconsistent -- sometimes the 2nd user can't use it to switch back to the 1st user, it just ignores the request.  The workaround was to use the 'slow' method, i.e., the Shutdown/Switch button > Switch User.

Now, in just the past few days, it's gotten much worse.  Now, when the 2nd user switches back to the 1st, it resets the 1st user's desktop environment?  The desktop is totally empty, as if all open programs had been force-closed.

I tried reinstalling the application in Synaptic but it hasn't helped.  Is there some way to reset the configuration, maybe fix some latent incompatibility with the earlier install?

Also, when it clears the 1st user, the Nvidia logo appears -- as if you'd just booted-up fresh.  (We're using the latest official Nvidia driver 173 because the simpler Ubuntu-provided driver doesn't work anymore, since 8.04).

---

### Post by bsmith1051 on 2008-08-03
I uninstalled the advanced Nvidia driver and it works!  I also notice that when I go to switch back to the other user account, there's a checkbox next to their name.  Before (when it wasn't working) there wasn't a checkbox.  So apparently the Nvidia video driver was preventing the Fast User Switch program from realizing the other account was already logged-in.

---

