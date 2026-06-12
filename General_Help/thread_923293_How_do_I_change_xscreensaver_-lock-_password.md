---
title: "How do I change xscreensaver -lock- password?"
date: 2008-09-18
forum: General Help
---

### Post by Alucard-sama on 2008-09-18
There's somebody in my house that really can't be trusted to use the computer while I'm not there so I decided I'd lock the screen using xscreensaver. The only problem is, the person in question knows my password so they can easily get rid of the lock if they want.
Is it possible to change the password xscreensaver requires, without changing the actual user password?

---

### Post by kpatz on 2008-09-18
Not that I know of.

Why can't you change your user password?  If there's someone untrustworthy who has access to the computer, why would you trust them with your password?

**EDIT:** Try this:  Create a new user account (for this example I'll call the user "lockuser").  Give lockuser the password you want the screensaver to have.  Then, to launch the screensaver, issue the command "sudo -u lockuser xscreensaver &", and then it should require "lockuser"'s password to unlock.

---

### Post by kpatz on 2008-09-18
Another idea:  use **xlock** instead of xscreensaver.  xlock lets you specify a password, either on the command line -cpasswd option, or in a .xlockrc file in your home directory.

Use **openssl passwd -crypt** to encrypt the password, and then put it in .xlockrc.

---

### Post by Alucard-sama on 2008-09-18
> **kpatz said:**
> 
**EDIT:** Try this:  Create a new user account (for this example I'll call the user "lockuser").  Give lockuser the password you want the screensaver to have.  Then, to launch the screensaver, issue the command "sudo -u lockuser xscreensaver &", and then it should require "lockuser"'s password to unlock.

"No protocol specified
xscreensaver: Can't open display: :0.0
xscreensaver: running as lockuser/lockuser (1001/1002)

xscreensaver: Errors at startup are usually authorization problems.
              But you're not logging in as root (good!) so something
              else must be wrong.  Did you read the manual and the FAQ?

              [http://www.jwz.org/xscreensaver/faq.html](http://www.jwz.org/xscreensaver/faq.html)
              [http://www.jwz.org/xscreensaver/man.html](http://www.jwz.org/xscreensaver/man.html)

[1] 10213
[1]+  Exit 1                  sudo -u lockuser xscreensaver"

---

### Post by Alucard-sama on 2008-09-18
> **kpatz said:**
> Another idea:  use **xlock** instead of xscreensaver.  xlock lets you specify a password...

xlock doesn't come up on idling without doing a bit of a workaround, which would be just as much trouble probably and less kind to my resources as well.

---

