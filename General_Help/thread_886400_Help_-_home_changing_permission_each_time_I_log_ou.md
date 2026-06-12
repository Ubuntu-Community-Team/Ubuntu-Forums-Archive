---
title: "Help - /home changing permission each time I log out"
date: 2008-08-11
forum: General Help
---

### Post by alex-uk on 2008-08-11
Hello,

I hope someone can help me...

Each time I log in to Ubuntu, I get an error saying that my .ICEauthority file can not be written to and I get sent back to the log in screen.

If I log in as root, then I find that my /home directory permissions have changed to root, so obviously as a user I have no access to them when I log in as a user. If I change them back to me, then I can log in as me, but the next time I log in I have to go through the process of logging in as root, changing the permissions back and logging in as me again!

I'm not aware of anything happening that could have caused this and it is starting to get a bit annoying!

Anyone got any ideas what could be causing this and how to solve it?

Thanks

Alex

---

### Post by queBurro on 2008-08-30
> **alex-uk said:**
> Hello,

I hope someone can help me...

Each time I log in to Ubuntu, I get an error saying that my .ICEauthority file can not be written to and I get sent back to the log in screen.

If I log in as root, then I find that my /home directory permissions have changed to root, so obviously as a user I have no access to them when I log in as a user. If I change them back to me, then I can log in as me, but the next time I log in I have to go through the process of logging in as root, changing the permissions back and logging in as me again!

I'm not aware of anything happening that could have caused this and it is starting to get a bit annoying!

Anyone got any ideas what could be causing this and how to solve it?

Thanks

Alex

login via the console and rename the file in your home directory to something else, i.e.
mv .ICEauthority .ICEauthority_old

worked for me, not sure what was going on tho'

---

