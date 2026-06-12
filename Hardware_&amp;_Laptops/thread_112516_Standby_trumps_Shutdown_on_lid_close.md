---
title: "Standby trumps Shutdown on lid close"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by hod139 on 2006-01-04
Hi all,

I was playing around with the KLaptop Control center (maybe this post belongs in the Kubuntu forum, but there was no laptop section in that forum) and set my laptop to suspend when the lid is closed.   

The problem I am having is if I shutdown the computer and close the lid before the shutdown process has finished.  If I close the lid early, the computer goes to standby midway through the shutdown process!  If I then resume from standby, it continues to shutdown properly.   The easy solution is to simply wait until the laptop has finished shutting down before closing the lid, but that is kind of a pain.

I would think that a shutdown command should have a higher priority than the standby command.  Is this a correct assumption?  If it is, then the acpi scripts should all check if the computer is shuting down before executing.  Or is there a reason that one might want to have standby take priority?  I was thinking of filing this as a bug, but wanted to get feedback from others first.

---

### Post by audax321 on 2006-01-04
Haven't used standby, but I'd file it as a bug... I don't see any reason why standby would be needed if the computer is shutting down.

---

### Post by hod139 on 2006-01-05
I filed it as a [bug:]("http://bugzilla.ubuntu.com/show_bug.cgi?id=21904") (bug 21904)

Also, I have heard that this problem exists for Windows users.  Can anyone confirm this?

---

### Post by Botond on 2006-01-05
Well, there&#8217;s no accounting for taste. For example I prefer to suspend the laptop manually, because in rare cases I want it to keep on doing something.

But your problem must be easy to solve: the suspend script (for ACPI this may be /etc/acpi/sleep.sh) must check out the actual runlevel before it does anythig. If this is not 2, then it shall simply exit.

---

### Post by hod139 on 2006-01-05
[QUOTE=Botond]
But your problem must be easy to solve: the suspend script (for ACPI this may be /etc/acpi/sleep.sh) must check out the actual runlevel before it does anythig. If this is not 2, then it shall simply exit.[/QUOTE]

I had similar thoughts, but I was more wondering why the script writers themselves did not check the runlevel first.  Is there some reason that a suspend call should take precedance over the shutdown script?  I can't think of any reasons, hence the bug report I filed; but I am more interested in finding out if this behavior is intentional.

Also when in the shutdown process does the runlevel actually change?  This simple check will save the day if the lid is closed after the shutdown process has finally changed the runlevel, but when does that actually occur?

---

