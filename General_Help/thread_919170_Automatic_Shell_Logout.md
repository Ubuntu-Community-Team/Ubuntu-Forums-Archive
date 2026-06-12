---
title: "Automatic Shell Logout"
date: 2008-09-13
forum: General Help
---

### Post by thinkdez on 2008-09-13
I think this is possible but I am not sure how to do it.  I hope someone knows how.

I want to run a command when a user logs in.  When the command is done executing I want the system to log the user out so they cannot run and shell commands.  I cannot figure out how to terminate the user's session.

Anyone got any hints on how to do this? 

Thanks

---

### Post by Pro-reason on 2008-09-13
You can't stop a user using the shell.  I mean, even if you made it shut down, they could just open another one.

---

### Post by thinkdez on 2008-09-13
I think I wasn't clear when I stated my issue but when the user logs in the program would load up automatically via .bashrc file.  That way the user would only be allowed to use that application.  The problem I have is that when the program is terminated the user is left at a shell prompt. I want them to be logged out of the system after they are finished with the specified program.

I hope that clarifies what I would like to do.

---

### Post by Pro-reason on 2008-09-13
We're talking about a session purely in a text terminal, right?  No X?

---

### Post by thinkdez on 2008-09-13
Correct.  Purely text session in the terminal.  User connects via SSH

---

### Post by Pro-reason on 2008-09-13
I've just created a new user with “sudo adduser test”, and then done “sudo nano /home/test/.bashrc”.

I added this to the end of the file:

```

cone
sleep 1
echo "Thank you for using the thinkdez server.  Come again soon."
sleep 2
exit

```

Then I did “su test” to log on.

The “cone” e-mail client started up, and when I exited it, I got the “thank you” message, and was then logged out.

I think that's what you want.

---

### Post by thinkdez on 2008-09-13
I feel stupid...... I was running the commands in a separate script and the system wasn't recognizing the exit command as it was exiting the shell of the script. doh!!!  

Thanks for your help.

---

### Post by Pro-reason on 2008-09-13
> **thinkdez said:**
> I feel stupid...... I was running the commands in a separate script and the system wasn't recognizing the exit command as it was exiting the shell of the script. doh!!!  

Thanks for your help.

If you want the commands to be in a separate file, but be treated as part of the same file, then try *including* it rather than *running* it.

For example, put this at the bottom of the .bashrc file:

```

*# Checks to see if the file exists, and includes it if it does.*
if [ -f ~/.session-script ]; then
**    . ~/.session-script**
fi

```

And then put all the commands, including the “*exit*”, in *.session-script*.  There's no need to put “*#!/bin/bash*” at the top.

Hope that helps.

---

### Post by bodhi.zazen on 2008-09-13
You can do this kind of thing very easily with ssh keys as well ...

As an example, I blogged on to ssh+svn, look at what I did with rbash and the keys.

[http://bodhizazen.net/bzblog/?p=5](http://bodhizazen.net/bzblog/?p=5)

---

### Post by Pro-reason on 2008-09-13
> **bodhi.zazen said:**
> You can do this kind of thing very easily with ssh keys as well ...

As an example, I blogged on to ssh+svn, look at what I did with rbash and the keys.

[http://bodhizazen.net/bzblog/?p=5](http://bodhizazen.net/bzblog/?p=5)

There's a problem with your tutorial.  You have used typographically-correct quotation marks like this:

```

echo “PATH=’/home/svn/usr/bin’” > .bashrc

```

...instead of the straight quotation marks required for computing:

```

echo "PATH='/home/svn/usr/bin'" > .bashrc

```

If a user copies and pastes this, it will cause an error.

---

