---
title: "ssh freezes after login"
date: 2008-07-24
forum: General Help
---

### Post by saquibrazak on 2008-07-24
Hello,

I am trying to ssh into my university computers. The servers are working fine because other people can login without a problem. Once I enter my password I don't get any response from the shell (seems like everything is frozen, CTRL-C also does not work but the cursor is blinking). After about 10 minutes, the shell prints a message that the connection timed out.

Here is my output

> sr:~$ ssh [email]xxxx@xxxx.xx.xxxxxxx.edu[/email]
> Password:
> Read from remote host xxxx.xx.xxxxxx.edu: Connection timed out
> Connection to xxxx.xx.xxxxxx.edu closed.
> sr:~$ 

There is about a 10 minute gap between my entering the password and the shell printing the message "Read from remo...".

If I enter the wrong password, ssh prompts me with another password command so I know that password is not the problem.

Thanks
Saquib

---

### Post by saquibrazak on 2008-07-24
Here is a little bit more info from SSH_GUI.

After I entered the password, is shows that the authentication was sucessful but then its stuck at the last line

----start of output from SSH-GUI-----
Password: 
debug1: Authentication succeeded (keyboard-interactive).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8


Thanks
Saquib

---

### Post by saquibrazak on 2008-07-24
Okay.. Seems like this is the same problem as

[http://ubuntuforums.org/showthread.php?t=838873](http://ubuntuforums.org/showthread.php?t=838873)

-Saquib

---

