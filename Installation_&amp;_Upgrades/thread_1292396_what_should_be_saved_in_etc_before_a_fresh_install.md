---
title: "what should be saved in /etc before a fresh install?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by relic70 on 2009-10-15
I intend to do a fresh install when Karmic is released. I have a separate /home partition which I intend to backup but also during the fresh install I will set it as a mount point /home but not do a format.

A couple of people have indicated in the forums that the /etc should also be backed up because of some settings stored in that directory.

My concern is whether those settings on the previous installation (Jaunty) will be compatible with the new installation (Karmic).

If not does one simply backup the entire /etc directory and copy it over to the new installation? 

Or, are there particular files or directories within /etc that should be backed up and then copied over to the new installation?

Would appreciate any clarification on this.

---

### Post by jeremyswalker on 2009-10-15
Really, I wouldn't worry about it. The only possible exception being if you hand-edited some configuration files in there. Personnally, I never transfer anything but my home folder from install to install.

---

### Post by relic70 on 2009-10-16
Thanks for your feedback.

---

### Post by phillw on 2009-10-16
For normal installations, just ~home is fine.

I'm dreading mine - I have various servers set-up (Apache2, MySQL, Mail, etc ...)

Cue a FULL Backup of absolutely EVERYTHING.

Before doing any stuff like that - I'd heartily suggest doing a full backup anyway.

To grab a list of all the extra things you have put on, try this thread...

[http://ubuntuforums.org/showthread.php?t=1057608&highlight=synaptic+package+manager](http://ubuntuforums.org/showthread.php?t=1057608&highlight=synaptic+package+manager)

To do a full backup, this is a good thread ....

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Regards,

Phill.

---

### Post by relic70 on 2009-10-16
Thanks Phill,
Mine is a normal install. Nothing like you with servers. I did see that other post previously and made note of the various suggestions.

---

