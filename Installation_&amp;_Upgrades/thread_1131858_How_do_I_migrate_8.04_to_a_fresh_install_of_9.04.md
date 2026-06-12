---
title: "How do I migrate 8.04 to a fresh install of 9.04?"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by duncanbourne on 2009-04-21
Hi,

I have a dell laptop running 8.04, and I'd like to do a complete fresh install with 9.04, rather than upgrading.

How do I move all the user files across to the new installation? If I back up the entire home directory, will I then have problems with file permissions after copying them to the new install?

Will copying the home directory bring across everything, or do I need other files too?

Duncan

---

### Post by Bios Element on 2009-04-21
Do yourself a favor. Get a HD big enough to copy everything in the home directory over and then install 9.04. Now DO NOT just dump everything in. GO through and get only what you need. A re-install is a great time to get rid of excess junk and un-needed config files.

---

### Post by duncanbourne on 2009-04-21
That sounds like a good plan. Will I have any problems with permission though? And are there any files outside of Home that should be saved?

Thanks

Duncan

---

### Post by 73ckn797 on 2009-04-21
I have never had a problem moving around my document directory or contents.

I will second the previous recommendation from bios-element about getting only what you need. All of your documents can be moved around.

---

### Post by rickbeton on 2009-04-21
When I install Ubuntu, I ALWAYS create at least three partitions: /, /home and swap. As Bios Element said, it's kinda good to replace your OS every six months/year with the new version and so purge all the unwanted cr*p accumulated by tinkering. If you don't tinker, you probably won't have this issue.

Either way, it's still jolly useful to have a /home partition - I don't understand why the guided partitioning doesn't do this by default.

To answer your question about permissions, in Unix/Linux they are based on the UID and GID of each user. Each file is tagged with a particular UID and GID of ownership. Changing these is not hard, e.g.

```
sudo chown -R rick.mygroup /home/rick
```

This fixes up files if your backup/restore has left them incorrect.

So you have two choices: either don't worry about ownership initially and fix it as above, or else make your new users match your old users' UIDs and GIDs before you restore /home. The 'id' command is useful to find these out - or simply inspect '/etc/passwd'.

Another tip: before upgrading, back up /etc so that you can refer to it later if you have forgotten your network settings etc.  But don't try restoring /etc over the new installation.

Rick :)

---

### Post by Bios Element on 2009-04-21
> **duncanbourne said:**
> That sounds like a good plan. Will I have any problems with permission though? And are there any files outside of Home that should be saved?

Thanks

Duncan

If you have any permission problems just type *gksudo nautilus* into console and change the owner to your username. Like I said, It's a good idea just to backup everything if your not sure. Myself, I save things from the /opt and /home folder since I run a dev server.

---

