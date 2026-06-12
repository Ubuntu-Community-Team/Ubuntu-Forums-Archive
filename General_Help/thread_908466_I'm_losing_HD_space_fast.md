---
title: "I'm losing HD space fast"
date: 2008-09-02
forum: General Help
---

### Post by Ramthebuffs on 2008-09-02
I've got some cron wgets running and I'm assuming its them.  Does wget store what it receives?  If so could you maybe help me out and tell me where.

---

### Post by Xiong Chiamiov on 2008-09-02
That's what wget does - it downloads things.  Where it stores files is dependent on where it's run from.

What kind of cron script are you running?

---

### Post by Nathan_M on 2008-09-02
It'll store them in the directory it's run from. Unless you've done anything fancy, it'll be in your home directory. If you are running it as root, it'll be in the /root directory.

---

### Post by Ramthebuffs on 2008-09-02
Thanks, I just found about 20k files in the root home folder.  Is there a better way to avoid this sort of thing?

Also, I've deleted all these files and my HD size hasn't improved.

---

### Post by mb_webguy on 2008-09-02
This might be a dumb question, but have you emptied your trash lately?

You could install kdirstat to help you find out what's using up your drive space.

---

### Post by Ramthebuffs on 2008-09-02
I hit the delete button on the files instead of sending them to the trash.  So they never went into the can.

In fact, I've just deleted some other files that wgets put in there and if I try and send them to the trash they just disappear.  According to my file manager, the disk space is never replentished.

---

