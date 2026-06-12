---
title: "Do you have to use a password?"
date: 2008-08-01
forum: General Help
---

### Post by mikelmahoo on 2008-08-01
In Ubuntu do you have to log on with a password? or can you go straight to the desktop without one? And also with administrative things?

---

### Post by iaculallad on 2008-08-01
By default, Ubuntu wants it's users to login using their password. You can bypass this option and automatically login if you want though. Navigate to System->Administration->Login Window, under the "Security" tab, check "Automatic Login" and select your user name. Click on close then logout of your account then log back in to test the changes.

---

### Post by jocko on 2008-08-02
> **mikelmahoo said:**
> ... And also with administrative things?
It may be possible, but very insecure to set sudo to not ask for a password.
You may get some help [here]("https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo"). But read the warnings and think at least twice before you decide to do it.

---

