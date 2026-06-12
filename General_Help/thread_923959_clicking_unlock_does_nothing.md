---
title: "clicking unlock does nothing"
date: 2008-09-18
forum: General Help
---

### Post by pikaia on 2008-09-18
Hey everyone.

I did a CLi install of Hardy and then added Ubuntulite (which is actually pretty good on my old Thinkpad).  Big problem however is that when I try to access Services or Network managers, if I click the 'Unlock' button, nothing happens.  The keyring is installed, but I can't find any other packages that might affect this.  I saw something about a user account or something, but I got lost.

Thanks for helping out.

---

### Post by pikaia on 2008-09-19
I tried to sudo services-admin and it brought up the screen, but everything is still greyed out, including 'unlock.'  Any thoughts?  An I missing a package somewhere?  I've reinstalled the gnome control center but still don't have access to network manager or services... hmm. 

Please help.

---

### Post by cariboo on 2008-09-19
Here is a list of groups that my main user is a member of:

```
adm dialout cdrom plugdev fuse lpadmin admin sambashare
```

It sounds like you are missing one of the groups, either adm or admin.

Jim

---

### Post by pikaia on 2008-09-20
okay, probably dumb, but how do I check what groups I'm assigned to, and how do I add if I'm missing one?

Thanks.

---

