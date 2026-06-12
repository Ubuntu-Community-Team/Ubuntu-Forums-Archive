---
title: "Newbie: How to cleanup partially installed packages?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by CarmineM on 2009-11-05
Hi to everyone,

I'm running an Ubuntu 9.04 server on which I'm experimenting.
I have set up the usual postfix/dovecot email server, and after messing with it, I decided to remove everything and start from scratch. So I wiped out the configurations under /etc and then issued:

apt-get remove dovecot-postfix.

At this point, the remove process failed with the system complaining about missing dovecot-postfix.conf file.

I tried to reinstall and it complains about missing "postfix-script".

Browsing the web, I found that an "apt-get clean" should have fixed the problem, but still, I'm stuck with the "cannot stat /etc/dovecot/dovecot-postfix.conf" error during removal.

Now, is there anything I could try to remove everything regarding dovecot/postfix, in order to reinstall it from scratch?

Thanks in advance for your help.
Regards,
Carmine

---

### Post by CarmineM on 2009-11-05
Sorry, wrong category! But I can't move te post.

---

### Post by ikisham on 2009-11-05
One thing you can do is open Synaptic, search for dovecot-postfix, select it and click on 'properties' and see the 'installed files'. Then remove one by one.

This will do it for the removal. IDK if dpkg or apt will complain about that (like if they will still think it's installed) but I guess it should be simple to fix and maybe if Synaptic reports a broken package then it can fix it by itself (Edit > Fix broken packages).

---

### Post by CarmineM on 2009-11-05
Hi!

> **ikisham said:**
> One thing you can do is open Synaptic, search for dovecot-postfix, select it and click on 'properties' and see the 'installed files'. Then remove one by one.

This will do it for the removal. IDK if dpkg or apt will complain about that (like if they will still think it's installed) but I guess it should be simple to fix and maybe if Synaptic reports a broken package then it can fix it by itself (Edit > Fix broken packages).

Does Synaptic works without a GUI? I'm on Ubuntu Server without X11 installed.
Thanks for your reply

---

### Post by ikisham on 2009-11-05
Oh sorry, I'm afraid not. But aptitude works in text mode and I read sometimes that it deals well with some die-hard apt errors.
Only I never use it so I can't tell you much but maybe a look in the manual will give you some clue.

---

### Post by Muskegman on 2009-11-05
You can also go into synaptic package manager and download "GtkOrphan" and try and remove the unwanted packages from there, this will also remove any orphaned and no longer used packages for you. Ive used it many times to remove no longer needed packages.

---

### Post by ikisham on 2009-11-06
And since you don't have a GUI then you try with deborphan. Maybe it's even already installed.

---

### Post by CarmineM on 2009-11-06
Thanks to everyone for your help.

I solved the issue with "dpkg --purge" and a clean reinstall of the packages.

By the way, aptitude failed too to recover from the error.

Thanks again

---

