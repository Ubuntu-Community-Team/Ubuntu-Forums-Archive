---
title: "[Solved] Acer Aspire 5100 Keyboard Problem post-login screen"
date: 2010-10-12
forum: Hardware
---

### Post by _rH on 2010-10-12
I was originally intending to post to the forum found below (it's read only) so my solution is here instead:
[http://ubuntuforums.org/showthread.php?t=631046]("http://ubuntuforums.org/showthread.php?t=631046")

PROBLEM:
I have an Acer Aspire 5100, running Ubuntu 10.04. 
After playing with Wine and mashing keys, I found that the keyboard in the GUI was suddenly unresponsive. 
Three things I noticed, however:
> Keyboard was fine when logging into Ubuntu (password/user)
> Keyboard was fine using other accounts on the Acer
> With hindsight, I recalled the "Sticky Keys" options coming up during a gaming session.

SOLUTION:
* Logged into my afunctional keyboard account on the Acer, and clicked to 'Keyboard' settings. 
* At 'Accessibility', de-selected "Accessibility features can be toggled with keyboard shortcuts"
* De-selected "Only accept long keypresses". Moved slider to "Short" as a backup plan.

I believe that during my key mashing, I had somehow selected to make only long key presses accepted by the GUI. 

Well, it works as it should now. Hope this may help.

---

