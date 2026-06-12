---
title: "Error:Users $Home/.dmrc file is being ignored"
date: 2008-11-07
forum: General Help
---

### Post by elbono on 2008-11-07
Hi

When ever I log in I get the following error

> Users $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $Home directory must be owned by user and not writable by other users.

I can just accept the error and continue to use Ubuntu as usual but the pop up is just annoying me at this stage. It all started to happen when I accidently sent my home folder to the trash bin. I took everything out but I think something is missing. I saw this was an error on older versions on Ubuntu but I don't want to go messing around with stuff until I get some advice.

Any advice?

By the way I have GNOME and KDE installed and use KDE mainly ( I don't think this matters but just in case it does)

Eoin

---

### Post by sisco311 on 2008-11-07
open a terminal and run this commands:
```
sudo chown -R $USERNAME: $HOME
chmod 755 $HOME
chmod 644 $HOME/.dmrc
```

---

### Post by taurus on 2008-11-07
You just need to change the permissions.  From a terminal, run

```
chmod 644 ~/.dmrc
```
Log out and back in again to see if you still get that warning message.

---

### Post by geirha on 2008-11-07
Either your homedir or the .dmrc file has gotten the wrong permissions. These commands should put them back to the default permissions:
```
chmod 755 $HOME
chmod 600 $HOME/.dmrc
```

---

### Post by elbono on 2008-11-25
I didn't check back in for a while, thanks for all the help, I'll just try it now!

I'll let you all know (I'm sure you're dying to find out)


Edit: Yep that worked a treat, thanks for all the help.

---

### Post by pwebster25 on 2008-11-29
> **elbono said:**
> I didn't check back in for a while, thanks for all the help, I'll just try it now!

I'll let you all know (I'm sure you're dying to find out)


Edit: Yep that worked a treat, thanks for all the help.

Which one worked? There were a bunch of suggestions.
I've got the same thing after marking some folders in my home folder as shared.

---

