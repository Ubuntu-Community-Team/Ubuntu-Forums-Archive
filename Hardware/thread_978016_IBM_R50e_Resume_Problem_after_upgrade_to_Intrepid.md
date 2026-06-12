---
title: "IBM R50e Resume Problem after upgrade to Intrepid"
date: 2008-11-10
forum: Hardware
---

### Post by soapboxllc on 2008-11-10
I have searched pretty exhaustively for a solution to this problem. 

Since I upgraded to 8.10 my resume does not work properly. When I resume, the screen is black and the mouse is visible and moves. While I move the mouse around I can see that the cursor turns into the text entry cursor where the password entry window should be. I can even enter my password and can tell that the windows are "there" but I cant see them based on cursor activity.

I have tried fiddling around with a lot of stuff so things might be messed up, but I think I have my original settings intact.

I am newish so go easy on me.

Thanks

---

### Post by Steve1961 on 2008-12-26
I'm not sure there's a solution to this problem yet.  I originally installed dapper on my r50e a few years ago and the fixes posted on the thinkwiki site worked and resume worked great.  When I upgraded to hardy I was able to get it working again by reverting to the old i810 video driver, but modifying my xorg.conf to use this driver with intrepid doesn't work - I'm assuming it's not included with the new kernel.  Anyway, in summary, none of the fixes on the internet are for intrepid - or at least none I've found - and so far nothing fixes the resume from suspend issue, which has something to do with the new intel video driver.

---

