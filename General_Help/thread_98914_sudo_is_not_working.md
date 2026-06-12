---
title: "sudo is not working"
date: 2005-12-04
forum: General Help
---

### Post by Comrade on 2005-12-04
For some odd reason, sudo is not working. For example, if I type in > sudo network-adminand type in the password, it says "authentication failed" or something of the sort. Also, graphical root login dialog boxes have authentication fail as well. The only way that I am able to accomplish these things is by manually going to Terminal and typing in the application name, like this.
> su -c 'network-admin'
Frankly, this is getting somewhat annoying. I am completely baffled as to what the problem may be. I know that I am entering the password correctly, because su -c works, but sudo does not. Assuming that graphical root logins require sudo to operate, the problems are related. It would save a lot of time if sudo started working.

---

### Post by atoponce on 2005-12-04
You are aware that when typing the password for 'sudo', it is not the root password, but your own password?  Root is disabled by default, and as such, diabled from logging in.

---

### Post by Comrade on 2005-12-04
Wow. I feel stupid for not realizing that. Now that I enter my own password, it says "username is not in the sudoers file - this incident will be reported."

Still, it's not working. How do I put myself into the sudoers file?

---

### Post by atoponce on 2005-12-04
What are the contents of you /etc/sudoers file?

---

### Post by Comrade on 2005-12-04
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults    !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

 Guess I have to visudo it then? How do I do that?

---

### Post by atoponce on 2005-12-04
[quote=Comrade]Guess I have to visudo it then? How do I do that?[/quote]

From a terminal (as root):

```
visudo
```

You will want to add the following to the file at the end:

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Just make sure your username is part of the admin group, and your set.  If needed, you can add your username (comrade, or whatever it is) to the admin group with (again, as root):

```
useradd -g admin comrade
```

You should now be able to run 'sudo' when logged in as comrade.

---

### Post by Comrade on 2005-12-04
My /etc/sudoers file looks like this now:
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults    !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL




But useradd -g admin comrade does not work. It returns:
> useradd: unknown group admin

---

### Post by atoponce on 2005-12-04
:oops:Ah hah!  Sorry.  Try (as root):

```
groupadd admin
``` I forgot we need to add the group also.  That should fix it.

---

### Post by Comrade on 2005-12-04
But now, since I, as a user, already exist, it denies the addition.

---

### Post by atoponce on 2005-12-04
It won't let you add yourself to the admin group?  What does it say?  Have you already been added, maybe?

---

### Post by Comrade on 2005-12-04
> root@ubuntu:/etc # useradd -g admin comrade
useradd: user saketh exists

It's not working. I don't want to annihilate my account!

---

### Post by atoponce on 2005-12-04
Nevermind.  I see you are already a user on your system.  The whole time, I was assuming you were just using the root account, and that your username was not setup.  If the user already exists, the command 'useradd' will throw an error saying so.  Rather, you need to execute the 'usermod' command.  So, in your case, you will need to execute (again, as root):

```
usermod -G admin comrade
```

This will add the already existing user 'comrade' to the admin group.  The example I gave above creates a new user and adds that user to the specified group.

---

### Post by Comrade on 2005-12-04
It says that comrade is not in the sudoers file, and that the incident will be reported.

---

### Post by atoponce on 2005-12-04
The user 'comrade' was the user I was using as an example, as it is your alias here on the forum.  The user you need to be actually typing is whatever you setup as your username.  I noticed earlier in an error that the user 'saketh' exists.  Is this your username?  Issue the 'usermod -G' command example I used above to whatever username you are trying to add.

---

### Post by Comrade on 2005-12-04
Foolish me. My username is actually saketh, not comrade. Either way, it still says I don't have the position in the sudoers file. Am I supposed to put my actual username in the sudoers file?

---

### Post by atoponce on 2005-12-04
Sure, if you want.  You could add the username 'saketh' in the sudoers file, give it unrestricted permissions, and never again need root.  However, with that said, this is highly NOT recommended.  The 'usermod -G admin saketh' command should work, and place the user 'saketh' in the admin group and make the admin group the primary group for the account

When you get the error saying the username is not part of the sudoers file, that means it is either specifically not in the file, like root is listed, or the account is not listed with any groups in the sudoers file.  Make sure everything is spelled correctly, both in the sudoers file, and in your command.

If the admin group was added with 'groupadd admin', and your are using the 'usermod -G admin saketh' command, all as root, it should work.  I see no reason why it shouldn't.  Maybe there is a permissions issue that I am not aware of, where someone else with a little more expertise could help.

If worst comes to worst, you could issue the 'userdel' to remove the account, then use 'useradd' to add it back.  However, with that said, I am not sure if you will lose any files or not.  I believe the switch '-r' must be issued to remove the user's files.

---

### Post by Comrade on 2005-12-04
I don't know what I did, but it's working now. I am most grateful for the assistance.

---

### Post by k0ontz on 2005-12-04
Glad to here you got it working.

---

### Post by jdong on 2005-12-05
Guys: For future reference, the Ubuntu/Debian sudo access group is called **sudoers** and is pre-created. Please don't create duplicate groups that accomplish the same thing.... The sudoers group is a standard, if you will, amongst Ubuntu/Debian users, and we'd like to keep it that way :)

Thanks!

---

### Post by atoponce on 2005-12-05
[quote=jdong]Guys: For future reference, the Ubuntu/Debian sudo access group is called **sudoers** and is pre-created. Please don't create duplicate groups that accomplish the same thing.... The sudoers group is a standard, if you will, amongst Ubuntu/Debian users, and we'd like to keep it that way :)

Thanks![/quote] What's the issue with duplicate group permissions?  Does it cause any issues with the OS?  Just curious.

---

### Post by jdong on 2005-12-05
[QUOTE=atoponce]What's the issue with duplicate group permissions?  Does it cause any issues with the OS?  Just curious.[/QUOTE]
No, it works just fine, but it'll be a PITA for the next person to help you out, since there is a natural assumption amongst Debian/Ubuntu users, experts, and developers that sudoers is holding sudoers :). It's a convention.

---

### Post by atoponce on 2005-12-05
[quote=jdong]No, it works just fine, but it'll be a PITA for the next person to help you out, since there is a natural assumption amongst Debian/Ubuntu users, experts, and developers that sudoers is holding sudoers :). It's a convention.[/quote] Cool.  :cool:

---

