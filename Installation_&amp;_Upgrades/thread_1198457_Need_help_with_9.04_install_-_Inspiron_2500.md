---
title: "Need help with 9.04 install - Inspiron 2500"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by awerking on 2009-06-27
Hi all from a true Ubuntu noob.  Completed my first install a few weeks back on an old desktop - I'm loving Ubuntu!

I'm trying to resurrect an old Inspiron 2500 laptop by installing 9.04, and I'm having some problems.  When I boot from the Live cd (same cd used to complete successful install on my desktop a couple weeks ago) the install hangs right after I select my install option.  All I get is a black screen with a blinking cursor.  I've tried messing with many of the options in the first screen, and have gotten the install to go as far as the language selection screen, but then it always hangs there.

Any advice or direction would be greatly appreciated.

Thanks!

---

### Post by merlinus on 2009-06-27
Check system specs against requirements for ubuntu.  You may not have enough ram to install from the live cd.

If so, you might try the text-based alternate install cd.

---

### Post by linuxmagick on 2009-06-27
> **merlinus said:**
> Check system specs against requirements for ubuntu.  You may not have enough ram to install from the live cd.

If so, you might try the text-based alternate install cd.

I'll second that.  I had similar issues with the Kubuntu 9.04 live CD.  The alternate CD worked just fine and I haven't had any issues after installing from it. To the original poster: The text based install may not be quite as friendly to you if you're new to Linux, but it's pretty straightforward.  If you run into issues with it, there should be plenty of people on this forum that can help you out.

---

### Post by awerking on 2009-06-30
SUCCESS!!  Thanks to all for the very helpful responses.

Xubuntu 9.04 alternate install cd, expert mode, and no apci did the trick for me.

Now that I've got Xubuntu up and running on the old Inspiron, I've run into a couple more issues.

1) Wireless card is not supported.  I have found Ndiswrapper and the appropriate driver and am confident that I can solve that issue by using Ndiswrapper, but I cannot get it to install.  That leads me to question/issue 2
2) When I try sudo commands I get an error message that says I am not an authorized "sudoer".  Xubuntu will not let me log in as root from the login screen, so I'm not sure how to get sudo permissions for my user account.  For obvious reasons, this will be necessary going forward.

Any help or direction with respect to issue number 2 would be greatly appreciated.  Thanks in advance for the help!

---

