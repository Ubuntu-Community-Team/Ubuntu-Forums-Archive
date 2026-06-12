---
title: "Home directory already exists. Please enter another home directory path."
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2009-02-15
I just installed Intrepid 64bit to a new partition in order to try it out before switching over from hardy. 

When installing, I told it to import my settings from both chaz and jami, the user accounts from my hardy install. However, when logging into the new system, jami does not exist and cannot log in. I go to system->users and groups and add a user, but when I enter "jami" as the new user, it gives me this popup that says 'home directory already exists. Please enter another home directory'.

I don't want a new user with a new home directory, I want to enable my wife to have her own user account and use her existing home directory like in my old install. I had thought that the 'import settings' wizard in the installer would have done that already, so I'm confused. What should I do?

---

### Post by BetterSense on 2009-02-15
I'm about ready to create a fresh user with a different name, and then copy everything from /home/jami over to the new /home/jami2. I don't want to break any of her settings though, and creating a new jami user that uses /home/jami as the home directory should be straightforeward. What am I missing here?

---

### Post by unixeducation on 2009-02-15
Be sure to copy dotfiles and dotdirs along with the rest of the old user directory contents. I'm a bit lost as to the root cause of the whole issue... it should have been taken care of with the user migration.

---

### Post by BetterSense on 2009-02-15
I was able to fix the issue by running 
```

sudo useradd -d /home/jami/ jami

```

---

### Post by shaft350x on 2009-02-28
Thanks for this, I had the same issue, and I just now decided to get around to fixing it.

---

### Post by SILLAT on 2009-07-05
> **BetterSense said:**
> I was able to fix the issue by running 
```

sudo useradd -d /home/jami/ jami

```

Thanks for this fix BetterSense, was facing the same problems here :lolflag:

---

