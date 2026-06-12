---
title: "Administrator can not log in through this screen"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by Porkchop_4 on 2008-12-28
I keep getting this message after I upgraded to 8.04 LTS yesterday.  I have been running 7.10 from my laptop with no problems for almost a year.  Which screen do I need to log in as root?  Is there a different one for root?

Greg Smith

---

### Post by pytheas22 on 2008-12-28
Do you mean that you're trying to log in to a graphical desktop session as root?  Ubuntu won't let you do this anymore, because it's a security hazard and shouldn't be necessary.  If you tell us what you're trying to do that requires you to log in to Gnome as root, we can tell you how to do it as a normal user instead.

You could probably also hack your system in order to force it to allow root logins, but that's not really a good solution...

---

### Post by Porkchop_4 on 2008-12-28
I don't appear to have permissions to do a lot of things.  I am trying to log on to the internet, but now I have a new message.  I forget the exact wording but something like "Your last session only lasted 10 seconds, if you did not logout you have a configuration problem or you are out of disk space"  Then  it takes me back to the login screen.  I know I am not out of disk space!

I had no idea upgrading would be this much of a struggle.  I want to log on as root to look around at permissions and such.  I have no idea how to check out the system using the command line.

Greg

---

### Post by pytheas22 on 2008-12-28
The message about your session lasting less than ten seconds usually is the result of permission issues with your home folder, which is probably a result of the upgrade.

In order to be able to log in again, please follow these steps, which will create a new account for you that should permit logins.  From that new account, you'll be better able to fix your real account:

1. at the login screen, press control-alt-F2.  This will bring you to a command prompt.  Log in there.

2. once logged in, type:
```

sudo adduser testuser
```

Then follow the instructions for creating a new user account.  Most of the items can be left blank with the exception of the password.

3. with the new account created, press control-alt-F7 to get back to the graphical login screen.  Log in there using the username 'testuser' and the password that you just set for the new account.

This should get you logged in.  Once you're logged in, you can open up a file browser as root by typing:
```

sudo nautilus
```

if that makes it easier for you to figure things out.

I'm happy to try to help you straighten out the permissions issues as well if you can't do it on your own.  Basically you need to make sure that your real user's home folder is owned by him, and that he has read and write permissions to it.  But I can give more specific instructions once we make sure that the steps above allow you to get logged into the desktop again.

---

### Post by Porkchop_4 on 2008-12-28
Thanks for the speedy reply.  I did what you said and created a new user 'testuser' and logged in, then I did the sudo nautilus thing from a terminal and it said:

testuser is not in the sudoers file.  This incident will be reported.

(That last part sounds scary!)

Greg

---

### Post by pytheas22 on 2008-12-28
Oh, sorry, that makes sense because the user 'testuser' doesn't have super-user privileges, because I didn't tell you to create it as such--my mistake.

Another way to run the file browser as root, however, would be to log into Gnome as testuser, then open a terminal and type:
```

su your-old-username
sudo nautilus
```

where 'your-old-username' is the name associated with your real user account, of course.  This should work and allow you to open up the file browser with root privileges.

Also, in order to get a better sense of what's wrong with the permissions on your home folder, it would be useful to see the output of this command:
```

ls -al /home
```

Also I know the bit about 'this incident being reported' sounds scary, but don't worry, it didn't actually do anything besides generate some warning message deep inside your system that no one will ever actually read.

---

### Post by Porkchop_4 on 2008-12-28
I figured it out finally!  I compared permissions on the testuser account to my account 'greg' and saw several things that were different.

I had to dust off my Linux manual and look up all that chmod, chown stuff.

I'm logging in okay now.   Thanks for your help, Pytheas22!  You pointed me in the right direction.

Greg
:D

---

### Post by jmoyet on 2009-04-24
I get that same "Administrator can not log in through this screen". 

I'm trying to installed the newest ATI drivers from ATI. It is a .run file and it says I need to run the installing as a "super-user" so I tried logging on to root to install it but cant login.

It would also great if you could tell me how to enable "super-user".

---

### Post by pytheas22 on 2009-04-24
jmoyet: for your purposes, it should be sufficient to open a terminal and log in there as root by typing:
```

sudo -s
```

Then run the installer for the ATI drivers.

You should not need to log into the graphical session itself as root, just the terminal.

---

