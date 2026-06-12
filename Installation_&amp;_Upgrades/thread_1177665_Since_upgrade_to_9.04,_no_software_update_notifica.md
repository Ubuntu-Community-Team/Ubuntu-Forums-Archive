---
title: "Since upgrade to 9.04, no software update notifications on two machines"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by Aaron44126 on 2009-06-03
Hi everyone;

I have two machines that have not been receiving update notifications since I upgraded them to 9.04.  Both of these machines were upgraded using the command line (i.e., do-release-upgrade), I don't know if that would make any difference.  My other machine that I upgraded with the GUI is working fine.

I know there's update notifications are different than before in 9.04.  I'm not getting any update notifications at all.  Here's what I mean:

 - I have the system set to check for updates once every day in the "Software Sources" control panel.  So, once an update is available, I expect my system to find it within a day and prompt me to install it.
 - I wait several days after I know updates have been released... nothing.
 - If I go to the command line and type "sudo apt-get update", wham, now the update notification appears.

So it seems it is not automatically checking for updates in the background, even though I told it to.  One of these machines is a server, and I have it set to automatically install security updates.  It still doesn't do anything, though, until I manually do a "sudo apt-get update" (although it was working fine in 8.10).

Any ideas?  Thanks!

---

### Post by jodrre on 2009-06-03
My appears to have the same issue. I have it set to look every day and prompt me when its about to install

However: today was the first time in a couple weeks that the update manager appeared and asked me to install.
Maybe releases aren't being sent out very fast?

---

### Post by yma981 on 2009-06-04
I have the same problem As Aaron44126...

The update notification doesn't appear at all eventhough it is set as check once per day .... , I manually check for update (GUI + CLI) NOTHING Appears ...

---

### Post by mcduck on 2009-06-04
Since 9.04, the update manager will only open once a week, unless there are security updates available. Also notification icon isn't used at all any more. It makes no difference how often you configure the system to *check* for available updates, you will still be informed about them once every seven days.

In case you prefer the old behavior, press Alt-F2 and run "gconf-editor", browse to apps/update-notifier and disable the "auto_launch"-key.

---

### Post by Aaron44126 on 2009-06-22
Hi, I would have written back sooner but somehow I didn't get any reply notifications on this thread.  :-P

I know about the changes to the update manager in 9.04.  I am *still* not getting any update notifications, security or otherwise, even though it is set to check daily.  I have to manually refresh the repositories (sudo aptitude update), and then I am immediately notified of updates.  I have two machines displaying this issue (and a third machine that works fine).

To be sure, I left a machine on and logged in while I went out of town for two weeks.  I returned to find no updates being offered.  Sure enough, as soon as I manually refreshed the repository, 60+ updates are available (including many security updates).  The only conclusion I can draw is that whatever background process that is supposed to check for updates every now and then is somehow not working.

Let me know if you're aware of anything else I can check as to why this is not working.  For more information, see the bug I filed on this issue yesterday: [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/390319](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/390319)

---

### Post by Aaron44126 on 2009-06-23
Found the problem, I believe, as noted in my bug report:
> Found the problem (I think).

The /etc/cron.daily/apt script, which I believe handles the automatic update setting, was not marked executable on either machine.

This reveals two problems:

 - /etc/cron.daily/apt lost its executable status during the do-release-upgrade process (I'm quite sure I didn't change the permissions on that file myself)
 - The GUI for configuring the automatic update interval should check this and warn you if this script is not executable! (Or just fix it itself.)

---

