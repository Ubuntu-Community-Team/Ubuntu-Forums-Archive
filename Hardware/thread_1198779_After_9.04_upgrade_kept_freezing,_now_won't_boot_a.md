---
title: "After 9.04 upgrade: kept freezing, now won't boot at all, &quot;no init found&quot;"
date: 2009-06-27
forum: Hardware
---

### Post by peacechicken on 2009-06-27
I just upgraded to 9.04 and it seemed to work fine, than it froze up when I was using Firefox, so I hit restart. It wouldn't boot up again, just gave me this:

```
kinit: No resume image, doing normal boot
mount: mounting /dev/disk/by-uuid/{some numbers} on /root failed invalid: argument
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg
```

After finding another person with this issue ([here]("http://ubuntuforums.org/showthread.php?t=1014172")) I fixed it once by booting the live CD and running "sudo e2fsck /dev/sda1" but it froze up again and now that command doesn't do anything, it doesn't recognize any drives at all.

Nobody is responding to the previous thread so I'm hoping this one will get noticed.

---

### Post by beezix on 2009-07-07
I am experiencing the same symptoms though have not re-installed or booted from disk. Weeks of freezing after machine went to sleep, had to hard reboot, now "kinit: no resume image" etc. I had some error messages prior to this asking me to report a problem, which I saved to a text file, which I can't access now. When I try to boot I am logged into desktop with command line but never gets past command line mode - need to fix my profile, running most recent version and just updated, 9.04 sounds right.

---

### Post by peacechicken on 2009-07-07
> **beezix said:**
> I am experiencing the same symptoms though have not re-installed or booted from disk. Weeks of freezing after machine went to sleep, had to hard reboot, now "kinit: no resume image" etc. I had some error messages prior to this asking me to report a problem, which I saved to a text file, which I can't access now. When I try to boot I am logged into desktop with command line but never gets past command line mode - need to fix my profile, running most recent version and just updated, 9.04 sounds right.

Seems to be a pretty common problem then, unfortunately. I thought I had my problem fixed (first I fixed [some disc errors]("http://twitpic.com/8w574"), then thought it was a loose HD connection) but it's doing it all over again. Both the "init: no resume image" and the issue with sometimes not mounting the HD whatsoever. It also had issues after "sleeping" so much that I was afraid to leave it alone for very long for fear it would be frozen when I got back.

I don't know what to do at this point, I'm thinking I might make an 8.10 disc and go back to that if possible. I'm just tired of wasting my time on this issue, wish I never upgraded.

---

