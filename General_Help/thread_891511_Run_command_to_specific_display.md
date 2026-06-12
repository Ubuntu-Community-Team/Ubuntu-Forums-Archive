---
title: "Run command to specific display"
date: 2008-08-16
forum: General Help
---

### Post by pooppoop on 2008-08-16
Can i start programs or run commands to a specific display and desktop?

For example, can i start FireFox from tty to be seen on the desktop?

---

### Post by kirsis on 2008-08-16
```

DISPLAY=:0 firefox

```

There you go. You probably get the gist of it :)

---

### Post by pooppoop on 2008-08-17
Great that really helps.
Can i moved a process i started to another tty or gui
and if i can or cannot, can i make it start under a specific tty and user?

---

### Post by kirsis on 2008-08-17
```

chvt

```

This will switch to a specific tty (sudo chvt 1 => tty1)

You can pair it with another command to launch an application on a diff tty (sudo chvt 1 && sleep 2 && some_cli_app)

And I think you can use sudo to run apps as a different user, though not sure how, since I've only used it to run something as root. If you want to both run apps as a diff user and in a diff tty, you'll may want to set permissions to /dev/ttyN file so it can be accessed by a specific user, not just root.

---

### Post by bingoUV on 2008-08-17
> **pooppoop said:**
> Great that really helps.
Can i moved a process i started to another tty or gui
and if i can or cannot, can i make it start under a specific tty and user?

To make it start under a specific tty (e.g. /dev/pts/1), do
```

firefox < /dev/pts/1

```

It is not exactly "under" a tty, but now ps will show this tty against the firefox process so maybe this is what you want.

To make it start as another user, you have to use su, or sudo
su: It will ask for a password unless the user initiating this is root.
```

su  <target_user> -c "firefox"

```

sudo: You will have to configure /etc/sudoers file to allow this. You can allow this with, or without password. You will need to call "sudo -u <target_user>". Read the man page of sudoers.
```

man sudoers

```

Read [http://ubuntuforums.org/showpost.php?p=3768173&postcount=7](http://ubuntuforums.org/showpost.php?p=3768173&postcount=7) for an example of password-less sudo setup.

---

### Post by pooppoop on 2008-08-17
Thanks for all the info, but i still have an unanswered question.

I want to bring a process gui and ownarship into my own tty and desktop after it is already running.

lets say i have firefox open and i go to another pc, use nxServer to connect to mine and then i bring firefox to the new nxServer session.

is it possible?

---

### Post by bingoUV on 2008-08-17
tty? You keep using that word. I don't think it means what you think it means.

How does tty matter to you?

The situation you describe is not possible in current X server design. Maybe in future.

But you can always enable "remote desktop" from System -> Preferences. This way you will connect to the session that is running on your computer screen.

---

### Post by pooppoop on 2008-08-17
this won't help me if i have 2 logins on the same pc

---

