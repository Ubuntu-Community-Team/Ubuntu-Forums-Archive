---
title: "PostLogin - alternatives for a kiosk?"
date: 2008-10-11
forum: General Help
---

### Post by mythbuntuChris on 2008-10-11
Hello,

I'm on a quest to use ubuntu as the backbone as a kiosk (using 8.04 - gnome and the myriad of lockdown tools).  I am oh-so close to getting this project completed except for a few gotchas.  Currently, I have a tarball of the kiosk user account home directory with the plan being to replace the existing home directory (and any nasty modifications made by the user) with the tarballed clean version.  After login, I believe the PostLogin - Default section of the gdm (/etc/gdm/PostLogin/Default) gets to do its thing.  In that file, I set up the following
```

# note need to put in some code to check to do this only
# for the kiosk user - any ideas?
  cd /home
  rm -rf kiosk/*
  tar xvfz /home/restore_kiosk.tar.gz

```

I test out to see if this is working by going into kiosk mode and changing the desktop and firefox bookmarks and then hitting Ctrl Alt Backspace and logging back in as the Kiosk user.  Unfortunately, the changes are still there.  They are also there if, the timeoutd threshold and the kiosk account is logged out.

I have discovered that if I put the same code into /etc/rc.local and then restart the computer it will run the script. Am I missing something on getting the timeoutd to restart the session?  Any suggestions are greatly appreciated :)

Have a great day!

chris

---

