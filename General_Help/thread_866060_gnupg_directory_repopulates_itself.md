---
title: "gnupg directory repopulates itself"
date: 2008-07-21
forum: General Help
---

### Post by ktneely on 2008-07-21
I have a new Hardy installation, having just upgraded my laptop from
scratch.  I keep my home directory in subversion and am trying to
restore it.   However, when I delete the ~/.gnupg directory, it
automatically restores itself.  I am not sure what process is doing
this.  

How do I -permanently or just for one session- delete the ~/.gnupg
directory?

thanks,
Kevin

---

### Post by Potatoj316 on 2008-07-21
Why do you want to delete that directory?

---

### Post by ktneely on 2008-07-21
I keep my home directory in subversion (including the gnupg directory and files).  Since this is a new installation, I need t checkout my home directory, but it fails because of this auto-(re)creation of the gnupg directory.

I would like to know what process is doing this behind the scenes.  I really only need it to "pause" for about a minute or two.

I suppose temporary unstallation of gnupg might be a solution, although that appears a bit extreme.

---

### Post by Potatoj316 on 2008-07-21
Im not too familiar with how subversion works but could you transfer all the files except that directory then in the subversion enter that direcroty and transfer the files out and into the local directory?

---

### Post by ktneely on 2008-07-21
> **Potatoj316 said:**
> Im not too familiar with how subversion works but could you transfer all the files except that directory then in the subversion enter that direcroty and transfer the files out and into the local directory?

Subversion is a content versioning system.  If I try to do what you suggest (and I did) I get an error on checkout complaining that the directory ~/.gnupg already exists.

It *ought* to be easier to stop whatever is forcing the gnupg directory and keys to repopulate rather than hack around how svn works.  If only I knew what was causing it to behave this way.

Previous versions of Ubuntu did not behave this way.

---

### Post by ktneely on 2008-07-22
New idea:  I am thinking that the gnupg directory gets recreated by the update service.  How would I go about stopping that temporarily?

---

### Post by ktneely on 2008-07-25
I solved the issue.  Apparently, whatever is running that recreates and repopulates the ~/.gnupg directory (I think it is the update service, but not positive about this) does not run if you are not logged in to the GUI interface.  To checkout my directory, I did the following:

[LIST=1]
[*]Install OpenSSH server
[*]Log out of the session
[*]SSH into the computer
[*]Delete ~/.gnupg
[*]Checkout my home directory using Subversion
[*]Log back in and everything works
[/LIST]

Hope that helps someone.
K

---

