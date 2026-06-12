---
title: "Not getting notified of updates?"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by dankegel on 2009-07-03
My Jaunty machines hardly ever prompt me to install any
updates, even though I know Chrome is updated weekly.
After glaring at them for days, it dawned on me that
update-notifier has a bug: when no security updates are
waiting, it won't launch update-manager unless it's been
a week since you last installed something.
The way it tells you've installed something is by checking
the date on /var/log/dpkg.log.
But since logs are rotated weekly, that means it almost
never hits a week before that file is touched again,
and so it never launches update manager!

Anyone feel like verifying this theory?

See also [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152)

I wrote a little perl script that prints out why
update-notifier isn't launching update-manager; it's at
[http://kegel.com/linux/ubuntu-autoupdate-diagnostic-pl.txt](http://kegel.com/linux/ubuntu-autoupdate-diagnostic-pl.txt)
This is what led me to figure out what was going on.

---

### Post by QIII on 2009-07-03
It's a "feature".  Don't know why anyone thought it was a good idea.

I don't remember where I found it, but I used the work around.

If someone doesn't get back to you, I'll see if I can find you a URL.

---

### Post by dankegel on 2009-07-03
> **QIII said:**
> It's a "feature".

No, I understand what they intended: that you
not be bothered with noncritical updates for a week
after you last ran update-manager or apt-get install manually.

But it's not working as they intended!  They expect
it to show you noncritical updates after a week
of inactivity, but because the log rotation looks
like activity to update-notifier, it *never* shows
noncritical updates.  That was not their intent when
they made the change.

Sigh.  Maybe I'll have to become a MOTU and upload a fix myself...

---

### Post by oldfred on 2009-07-03
When I saw this when I upgraded,  I happened across a setting that changed it back. Mine works like always with a icon in the tool bar when ever any update is available. I had to look in google to find the setting again.
This site has the setting. [http://maketecheasier.com/remove-the-annoying-update-manager-pop-up-in-ubuntu-jaunty/2009/06/18](http://maketecheasier.com/remove-the-annoying-update-manager-pop-up-in-ubuntu-jaunty/2009/06/18)
You use gconf-editor in terminal and Navigate to [I]Apps->Update Notifier and uncheck the auto launch box. Seems backwards to me but it works.
[/I]

---

### Post by dankegel on 2009-07-03
I don't want the old behavior back.  I want the new behavior 
to work as designed.  I don't care about my computer; I'm
worried about the 99% of Ubuntu users who are using
the default settings.   They should get notified of nonsecurity
updates after no more than a week, as the update-notifier
author intended, and this bug makes them wait longer.

---

### Post by dankegel on 2009-07-04
> **dankegel said:**
> They expect
it to show you noncritical updates after a week
of inactivity, but because the log rotation looks
like activity to update-notifier, it *never* shows
noncritical updates. 

Correction: the dpkg.log and apt/term.log files are
rotated monthly, so this bug only causes an extra
week of no updates.  Now I think in the average month,
in the absence of security updates, users will get
prompted to install nonsecurity updates three times instead
of four as a result of this particular bug.

So, it's only 1/4 as awful as I thought.  Still worth
fixing.

---

