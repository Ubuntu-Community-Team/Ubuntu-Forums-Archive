---
title: "Screen resolution fluctuations in laptop"
date: 2011-05-30
forum: Hardware
---

### Post by johan34 on 2011-05-30
Hi. I have a HP 620 laptop that ran 10.04 perfectly. I recently did a clean install of 11.04 (natty) and everything works just fine, except I'v set the system to blank screen when i close the lid. This was fine in 10.04 but in natty, when i reopen the lid, the screen resolution changes to a narrow one (screenshot attached), or half my screen is inaccessible, usually it follows that my whole screen blanks out. Its really annoying any solutions? (Im using unity interface and iv set vBlank to off in compiz manager as suggested by someone. No help)

---

### Post by johan34 on 2011-06-06
Nobody? Okay can i jus ask, i installed the system from a usb disk i created. Is it inadvisable to do so?

---

### Post by ThinkEntropy on 2011-06-08
I think I'm having the same, or similar problem.  I've been running 11.04 without issue for the last couple weeks, and then all of the sudden today my screen decided to not display the sides anymore.  I changed nothing, and it was (seemingly) random.  Mine looks exactly like yours does, but this this just started today for me.

When I was running 10.10 I noticed that if I booted fresh into Ubuntu it wouldn't display the bottom and top of the screen, not the left and right sides like it is now.  It would only fix itself after logging out and then back in  #-o

But now, I've tried logging out and back in, restarting, and changing my resolution and I can't for the life of me get it to display on the entire screen anymore.  So, I think I'm in the same boat as you...hopefully someone can provide some insight into the problem.

I'm running a Dell Latitude E5400.  BUMP!

---

### Post by meijer.o on 2011-06-08
> **johan34 said:**
> Hi. I have a HP 620 laptop that ran 10.04 perfectly. I recently did a clean install of 11.04 (natty) and everything works just fine, except I'v set the system to blank screen when i close the lid. This was fine in 10.04 but in natty, when i reopen the lid, the screen resolution changes to a narrow one (screenshot attached), or half my screen is inaccessible, usually it follows that my whole screen blanks out. Its really annoying any solutions? (Im using unity interface and iv set vBlank to off in compiz manager as suggested by someone. No help)

Try adding the following to /etc/default/grub as boot parameter: video=SVIDEO-1:d
Solved the issue for me.

Otto Meijer

---

### Post by ThinkEntropy on 2011-06-08
> **meijer.o said:**
> Try adding the following to /etc/default/grub as boot parameter: video=SVIDEO-1:d
Solved the issue for me.

Otto Meijer

Thank you for the suggestion meijer.  Although I can't speak for the OP, adding that line into grub did not fix the issue for me.  If I find that the OP and I don't share the same issue I'll start another thread. The input however is much appreciated.

---

### Post by ThinkEntropy on 2011-06-09
I'm discovering a slew of issues with 11.04 beyond the one posted here so I'm going to be downgrading back to 10.04 (which worked great for me for many months).  But, I figured I'd bump this thread anyway with the hope that someone can still help the OP...

---

### Post by johan34 on 2011-06-17
Bump!
ThinEntropy i also downgraded to my previous 10.04 which for me has been arguably the most stable option. I must say im quite disappointed with certain natty features, i fear they rushed with the new unity interfaces and as a result natty is a bit buggy. I gues i shall upgrade only to the next LTS since year after year its getting difficult reverting back to older versions bcoz of problems. But i shall keep u informed should i stumble on anything!

---

### Post by gary@web.ca on 2011-09-24
Same problem.  Here's the odd thing.  When I use the live disk, the whole screen is used and the screen is quite stable.  Under live disk, Settings > Monitor says 1366 x 768 which the HP specks call for.  After an install, Settings > monitor says 1024 X 768 and the usable screen is in the middle with black bars on either side.  Trying to change the setting to 1366 x 768 does not change the setting.  The screen is unstable goes on and off eventually just goes black.  

In this last attempt, Settings > monitor say 1366 x 768.  The black bar on the left is gone.  There is a black bar on the right and whatever should be on that part of the screen is invisible (missing).  within a few minutes the screen went blank and no keystrokes brought it back. Turned off the laptop, turned it back on.  when it came up again, the I could see both sides of the working screen, but the black bars on each side appeared and Settings > monitor now says 1024 x 768.

Why does the live disk session work while the install generates such a flaky screen?

Now it seems to be working properly????? No idea why or if something else will happen.

Gary Campbell

---

### Post by johan34 on 2011-10-01
Yes exactly the same thing!!! I hope someone can find solutions for this quick, 11.10 coming soon, ive liked the way ubuntus making progress, but it disappoints me that such bugs happen! I wonder what this problem is! :s

---

