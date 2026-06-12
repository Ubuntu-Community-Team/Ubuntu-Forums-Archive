---
title: "What to do if you get a &quot;su returned with an error&quot;"
date: 2008-08-13
forum: General Help
---

### Post by JC Casiano on 2008-08-13
I'm experimenting with scripts on my Toshiba M400 tablet.  In the process I edited the /etc/sudoers file.  In order to edit it, I had to change the permissions.  However, upon restoring the permissions and rebooting, whenever I tried to run something using kdesu I would get a:

  "su returned with an error"

message. After reviewing much of the available dialog online for fixing this error without finding a success, I tried running my app from the command line.  What I found is that the system expects the permissions to be 0440. Any other combo (0444 in my recent case) will cause a failure.

To fix this, you will need to log in as su at a command window.  From the command line, run "chmod 0440 /etc/sudoers". It might also help to insure that root owns this file: "chown root:root /etc/sudoers". I hope that this helps some of you, I know I was extremely frustrated with the lack of useful information out there...

---

### Post by caljohnsmith on 2008-08-13
Is there some reason you didn't use "visudo" to modify sudoers? Then you don't have to worry about messing up your sudoers permissions nor worry about incorrect syntax in sudoers, as visudo takes care of both. Normally visudo uses the vi editor to modify sudoers, but you can also use nano if you do something like:
```
EDITOR=nano sudo -E visudo
```

---

### Post by JC Casiano on 2008-08-17
Because I was being clever...  Another post I read gave some insight on how to kill the xvkbd post login, I wanted to open the file in kwrite instead of a console editor.  So I modified the permissions and edited the file, forgetting that some system files have to have very specific permissions.  Gotta be a bit more careful...

---

