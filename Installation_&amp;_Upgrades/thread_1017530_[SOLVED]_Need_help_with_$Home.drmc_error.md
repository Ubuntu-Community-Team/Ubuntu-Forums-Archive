---
title: "[SOLVED] Need help with $Home/.drmc error"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Joesplace on 2008-12-21
Got everything installed but now I get this error every time I start my computer:

*User's $Home/.drmc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by others."*

What exactly do I do to cure this problem? 

thanks , , ,

---

### Post by snova on 2008-12-21
Press Alt-F2, and type 'gksudo nautilus'. Navigate to your home directory, show hidden files if necessary, right click on the .dmrc file, Properties, Permissions, and change the owner to yourself.

---

### Post by Joesplace on 2008-12-21
snova - Thanks for the reply, I followed your instructions exactly and here are the permissions:

Owner - Joe
Access - Read and Write
Group - nogroup
Access - None
Others - None
Access - None

I don't see anything wrong but I still get the error. What should the Group setting be, Admin or Nogroup? What else can I try?

---

### Post by snova on 2008-12-21
From what I know, the group is usually the same as your user (such as, snova:snova).

Well, try it from the command line anyway:

```
sudo chown <user>:<user> ~/.dmrc
chmod 644 ~/.dmrc
```

---

### Post by sisco311 on 2008-12-21
drs305 has a detailed tutorial here:

[http://ubuntuforums.org/showthread.php?t=976610]("http://ubuntuforums.org/showthread.php?t=976610")

---

### Post by Joesplace on 2008-12-21
sisco311 - I followed the tutorial and it fixed my problem! Thanks very much to all . . . 
- Joe -

---

