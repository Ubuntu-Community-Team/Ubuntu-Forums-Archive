---
title: "Upgrading and User Home directory problem"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2009-09-27
Hello everyone :-)

I have upgraded from 8.10 to 9.04 by only installing /.
I have left the /home intact which is on another partition.

This computer is used by 5 people and they all had their own home directories in the previous version.  I tried to add the same users with the same passwords and user names so that I would not loose the settings for each one.

Although it allows me to add users, when I press the button it says that the home directory already exists and that I should use another one.  Which is of course NOT what I want.

I tried to rename the old home directories and then replaced the home directories created by 9.04 with the old ones.  Although it allowed me to do that (as a root) when I tried to log on as this user, it told me that the user must have permission for the $HOME directory.. etc...

I remember that when I upgraded from 8.04 to 8.10 I had no problem with this issue.  I think that it allowed me to use the same home directory and everything went smoothly.

What am I doing wrong?  Is there a way to do what I want?

Another idea that I am thinking is copying everything from the old directory to the new home directory created by 9.04.  Would that work?  If yes would a simple drag and drop work?  I am thinking of the hidden files.  Of course I would be doing this as root.

Thank you all in advance

---

### Post by wojox on 2009-09-27
Check this link out: [http://www.funnestra.org/ubuntu/jaunty/#switch-home](http://www.funnestra.org/ubuntu/jaunty/#switch-home)

---

### Post by Ifaistos on 2009-09-27
Ok I read it.

I must say that I got a bit lost, but if there is no other option I will try it.
Why didn't I have this problem when I migrated from 8.04 to 8.10?

Is there an easier way?  A way that would involve windows?
A way that would not involve typing commands?  I am using the gnome desktop environment.

edit :  I think that this is not what I want : **"Switch to an existing /home on another partition"**
I want to use the existing partition on the /home partition that is used by default by Ubuntu. I don't want to "Switch" on another partition.  My /homes are already there, I don't want to switch. 


I also have another issue now.

1. Created a user.
2. Deleted it's home directory.
3. Renamed the old home directory to replace the one created by 9.04
4. Ubuntu crashed and did not allow me to use that home directory.
5. Deleted the user.
6. Deleted the home directory.
7. Tried to create again the same user.

I am getting the error that this user already exists!!! although I don't see her on the list of users.

Any ideas?

---

### Post by Ifaistos on 2009-09-29
bump

---

### Post by slakkie on 2009-09-29
You didn't upgrade, you freshly re-installed a higher Ubuntu version. If you did an upgrade you would not have this particular problem.

Your problem is that the UID of the users is different between installations.

1) Set the same UID as on the old installation
2) Change the permissions of the old homedirs.

For 1)

Check the UID of the homedirs:

```

drwxr-xr-x  28    1001    1001  4096 2009-09-23 16:36 izzy

```

In this case the izzy user had uid 1001, to recreate the izzy user with UID 1001:

```

sudo useradd -u 1001 -c "The user named izzy" -s /bin/zsh izzy

```


Now the problem is solved.
```

drwxr-xr-x  28 izzy    izzy     4096 2009-09-23 16:36 izzy

```

Do this for all your users.

For 2)
Create the users not specifying the UID:
```

sudo useradd -c "The user named izzy" -s /bin/zsh izzy

```

```

drwxr-xr-x  28    1001    1001  4096 2009-09-23 16:36 izzy

```

Now set the owner and group to the old homedir:
```

sudo chown -R izzy:izzy /home/izzy

```

And fixed again
```

drwxr-xr-x  28 izzy    izzy     4096 2009-09-23 16:36 izzy

```

---

### Post by Ifaistos on 2009-10-03
Thank you for your detailed answer :-)

I will try it out immediately.

---

### Post by Umang on 2009-10-22
Hi,

Could you please post the results of your attempts to re-use a separate /home partition when upgrading from one version to another. I have searched the forums, and haven't found a similar thread. I'm afraid that I'll have the same problems when I try to upgrade by reinstalling on the / partition. (Although I don't have a separate /home partition, I plan to create one, so that I can use it on future re-installs.)

[I]If anyone else knows the answer to this very related query, please do answer:
[/I]
Is it possible to do what the OP is attempting to do? i.e: Have a /home partition with many users'(four in my case) running a particular version of Ubuntu and reinstall a new version of Ubuntu over the / partition. What will happen? Will all the users be restored as they were? If not, when I add users with the same usernames, will their "Home folders" be recovered from the old /home partition? Or will I encounter the same problems that the OP is facing?

Thanks

Umang

---

