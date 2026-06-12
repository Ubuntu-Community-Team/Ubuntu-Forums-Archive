---
title: "Hardware error reported"
date: 2013-04-03
forum: Hardware
---

### Post by D0Ct0Rh4cK on 2013-04-03
Hello guys, here I come by describing  a problem that is making me constrict to change OS...

every time I boot my pc after a few minutes I run into the following error shown up in the screenshot:

[IMG]http://i.imgur.com/R9bwuAb.png[/IMG]

what can I do? as you can see same error gets reported twice or even 3 times... I don't know how to fix this.

Also beware that I am running a system which has an hybrid video card system... one nvidia and one Intel.. if this could help to figuring a way out.


Thanks.

---

### Post by slickymaster on 2013-04-03
Are you actually noticing problems with your GPU, other than these error messages?

If you aren't actually noticing problems with your GPU other than these error messages I'd say you can safely ignore them. Most probably it's related to a known bug affecting Apport: [Bug #1005573]("https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1005573")

If you are seeing any weird graphics related behavior, keep an eye on your logs - specifically **xorg.0.log** and **syslog**, but maybe the kernel logs as well. If you are noticing errors copy them down, and try to make a best guess (or ask) whether it is a driver problem, kernel problem or X11 problem. Then use apport to file the bug against what you determine to be the best package (for example for a nvidia driver I would enter apport-bug nvidia-current-updates), be as detailed as you can be in the resulting bug report and put the symptoms you experience and any errors you noticed into the description when you file the bug. More information about filing bugs is [here]("https://wiki.ubuntu.com/Bugs/FindRightPackage") and [here]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by D0Ct0Rh4cK on 2013-04-03
> **slickymaster said:**
> Are you actually noticing problems with your GPU, other than these error messages?

If you aren't actually noticing problems with your GPU other than these error messages I'd say you can safely ignore them. Most probably it's related to a known bug affecting Apport: [Bug #1005573]("https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1005573")

If you are seeing any weird graphics related behavior, keep an eye on your logs - specifically **xorg.0.log** and **syslog**, but maybe the kernel logs as well. If you are noticing errors copy them down, and try to make a best guess (or ask) whether it is a driver problem, kernel problem or X11 problem. Then use apport to file the bug against what you determine to be the best package (for example for a nvidia driver I would enter apport-bug nvidia-current-updates), be as detailed as you can be in the resulting bug report and put the symptoms you experience and any errors you noticed into the description when you file the bug. More information about filing bugs is [here]("https://wiki.ubuntu.com/Bugs/FindRightPackage") and [here]("https://help.ubuntu.com/community/ReportingBugs").

Thanks for your detailed answer to my question.

I don't notice any problems apart such report, but when I use firefox and open several tabs it's likely to freeze and after a few seconds (like 20 ) it gets unstuck (during which I can only move mouse arrow), but such problem used to happen even before that such problem was reported, it's likely to happen often but maybe this could be related to firefox and not to the Ubuntu 12.04 LTS in its wholeness, I don't know... any suggestions?

---

### Post by wojox on 2013-04-03
> **D0Ct0Rh4cK said:**
> I don't know... any suggestions?

You could disable apport, [How do I enable or disable Apport?]("http://askubuntu.com/a/93467/2973")

---

