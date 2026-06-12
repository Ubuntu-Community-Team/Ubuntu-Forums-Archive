---
title: "WINE and Add/Remove Missing Fresh Install"
date: 2008-07-23
forum: General Help
---

### Post by Killtodie on 2008-07-23
Just did a fresh install here and I just noticed that I dont have WINE and no addremove under Applications. Looked everywhere and its not here.... Dont know whats going on. Suggestions?

---

### Post by estyles on 2008-07-23
WINE is not part of the default install, you have to install it yourself.  Check under System->Administration->Synaptic Package Manager.  Synaptic fulfills the same function as Add/Remove, and I personally prefer it.  Not sure why Add/Remove isn't there, but Synaptic should work for whatever you need.

---

### Post by Killtodie on 2008-07-23
Synaptic aint here either.....

my other install came with wine I believe... yea.. looks like it needs a format

I got to users and try to unlock the user account and it fails

also loooking at it under privileges addmin controls are unchecked

yeah, i got no admin controls and no other user accounts. What can I do?

---

### Post by Killtodie on 2008-07-23
ok, so yeah. im stuck with an non admin account. cant create a new account. how can I make the current account an admin account?

---

### Post by Killtodie on 2008-07-23
anyone?

---

### Post by cpetercarter on 2008-07-23
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=865922&highlight=admin+user"). This will show you the commands you need to run in order to restore your "username" to the admin group so that you can again download and install programmes etc.

In order to do this, however, you need to reboot into recovery mode. At the beginning of the boot sequence, Grub gives you about 2 seconds to press the escape key. If you do this, you will find the boot menu - select "recovery mode". After a few minutes the recovery menu appears. Select "drop to root shell". A root command line will appear at the bottom of the screen. Be very careful what you do with it. When you are finished, type "exit" and you will be able to resume the normal boot sequence.

---

### Post by Killtodie on 2008-07-23
Thanks!

---

