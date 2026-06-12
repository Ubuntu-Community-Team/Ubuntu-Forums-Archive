---
title: "firefox history and bookmarks?(reinstalling)"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by flyingsliverfin on 2009-05-23
im reinstalling ubuntu becuz i messed it up quite badly. I can still use recovery mode. I would like to know where the firefox history and bookmarks are saved so I can copy and back up the file and paste it back in the newly installed ubuntu.

I also need the same thing for pidgin, where does it save the buddies? I have about 100 and I don't think I have the time to add each one all over again seperatly.

---

### Post by zhhansen on 2009-05-23
Not sure about history, but bookmarks are saved in /home/[user]/.mozilla/firefox

then there should be a file with (what seems like) random characters.default, open it up, and there you go

EDIT: sorry I didn't see the pidgin question also, ill look into it because I am unsure
EDIT: maybe this link can help? I can't find too much info on backing up pidgin buddies. [http://developer.pidgin.im/ticket/3581](http://developer.pidgin.im/ticket/3581)

---

### Post by mlissner on 2009-05-23
For firefox, there is a folder in your home directory that is called .mozilla. If you grab that, and put it in your home directory in the new install, you should be all good, I'd say. 

For pidgin contacts, I'm fairly sure they're saved in the cloud, but you can save your settings/logs/etc. by keeping the .purple folder in your home directory.

This is generally true for a lot of apps. You might find success by just copying all of the folders over when you do your new install. It might save you A LOT of time reconfiguring things.

---

### Post by mlissner on 2009-05-23
PS, I think history is saved in a database called places.sqlite. I'm not sure though if that's the right name, or if you can move only it. Your best bet would be the whole directory, probably.

---

### Post by flyingsliverfin on 2009-05-23
ok thx

the firefox bookmarks were the most important (had over 200) so that worked

---

