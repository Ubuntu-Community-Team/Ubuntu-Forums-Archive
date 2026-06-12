---
title: "Allow command &quot;shutdown&quot; to run without sudo"
date: 2008-09-11
forum: General Help
---

### Post by niccholaspage on 2008-09-11
I hate having to use sudo to shutdown the system,So is there a way to make it so it will be executed as root? And I also want to do this for some other programs.

---

### Post by Vivaldi Gloria on 2008-09-11
You need to edit /etc/sudoers using visudo.

**Part 1.** Make changes so that visudo starts with nano rather than vi. You can pass this part if you want.

Edit ~/.bashrc and add this line somewhere:

```
export EDITOR=/usr/bin/nano
```

so that visudo opens with nano rather than vi (i hate vi). Now in terminal:

```
source ~/.bashrc
```

so that the change in .bashrc takes place. All we did upto know is to start visudo with

```
sudo -E visudo
```

in nano rather than vi.


**Part 2.** Changing /etc/sudoers using visudo

Start 

```
sudo -E visudo
```

Under the line "# User alias specification" add a list of users as follows:

```
# User alias specification
User_Alias USERS = user1, user2, user3
```

Write the name of the users sepatated by a comma and a space. These users will close the computer without a pswd asked. Write as many users as you want.

Now below the line "# Cmnd alias specification" add a command list as follows:

```
# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt
```

Now below the line "%admin ALL=(ALL) ALL" add the command which will let USERS give SHUTDOWN_CMDS without a pswd:

```
%admin ALL=(ALL) ALL
USERS ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS
```

Now "sudo shutdown", "sudo halt", and "sudo reboot" won't ask passwd. If you want, you can put an alias for halt='sudo halt' etc.

---

### Post by cszikszoy on 2008-09-11
I don't exactly know what you need to do to make this possible, but I know what you need to change.

You need to edit the "sudoers" file.  This is the file that determines which programs require which permissions etc etc.

If you edit this file correctly you should be able to specify commands that can be run without a password.

Lots more information here:
[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

Sorry I can't completely answer your question, but hopefully I've pointed you in the right direction.

---

