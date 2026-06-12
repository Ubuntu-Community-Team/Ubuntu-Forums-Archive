---
title: "[SOLVED] Username Change"
date: 2008-07-26
forum: General Help
---

### Post by uzzo2 on 2008-07-26
i've searched the forum for a thread on changing your username and haven't been successful. i've figured out how to change the password but not the username. can anyone enlighten me? thanks in advance.

---

### Post by Joeb454 on 2008-07-26
You can post in the Forum Feedback & Help forum, though there's very few cases of Username's being changed.

You're unlikely to get it changed except for privacy reasons

---

### Post by Oldsoldier2003 on 2008-07-26
> **Joeb454 said:**
> You can post in the Forum Feedback & Help forum, though there's very few cases of Username's being changed.

You're unlikely to get it changed except for privacy reasons

With only 69 posts, what I would do in your shoes is just create a new account, then post in the resolution center asking to permanently deactive the old one. (By doing this you show that you aren't trying to get around the rule against multiple accounts.)

---

### Post by gjoellee on 2008-07-26
if you don't want to enter your username you could change the login screen to "Human List" or enable automatic login, but this won't change the username

---

### Post by Oldsoldier2003 on 2008-07-26
moved to FF&H

---

### Post by kellemes on 2008-07-26
> **uzzo2 said:**
> i've searched the forum for a thread on changing your username and haven't been successful. i've figured out how to change the password but not the username. can anyone enlighten me? thanks in advance.

Little confused here..
What username? The username you have created on your Ubuntu install? Or the username you use on the this forum?

---

### Post by Joeb454 on 2008-07-26
> **kellemes said:**
> Little confused here..
What username? The username you have created on your Ubuntu install? Or the username you use on the this forum?

That's a good point, I assumed forum username (bizarrely)

---

### Post by uzzo2 on 2008-07-26
thanks, i was wanting to change my username to log in on my computer, not for the forum. sorry for the misunderstanding.

---

### Post by Oldsoldier2003 on 2008-07-26
> **uzzo2 said:**
> thanks, i was wanting to change my username to log in on my computer, not for the forum. sorry for the misunderstanding.

moved back to GH then.

The best thing to do is create another user account with the name you want and add it to the admin group.

---

### Post by p_quarles on 2008-07-26
> **uzzo2 said:**
> thanks, i was wanting to change my username to log in on my computer, not for the forum. sorry for the misunderstanding.
This isn't something that I would normally recommend, since it's easier and more certain to create a new user and transfer the settings. But, here's how you do that:
```
sudo usermod -l newname oldname
```
You would then need to manually change the name of the user's home directory to reflect the new name:
```
sudo mv /home/oldname /home/newname
```
This should work okay, but again, I think it's safer to create a new user.

---

### Post by Samuel-Sama on 2008-07-26
There's an easier way:
System -> Administration -> Users & Groups
There should be a button to unlock, enter pasword etc.
Click the "Add User" button, fill in the new details.
Delete the account you are currently using.
Done!

I haven't actually tested this so I'm not sure if it works.

---

### Post by uzzo2 on 2008-07-26
> **Oldsoldier2003 said:**
> moved back to GH then.

The best thing to do is create another user account with the name you want and add it to the admin group.
ok, added the new user account, but when i go to delete the old one, i get a pop up that says. are you sure you want to delete the account?
this will disable this users access to the system without deleting the users home directory.
this user is currently using this computer.
is this what i need to do?

---

### Post by CatKiller on 2008-07-26
It's probably a good idea to not be logged in as the user you're trying to delete.

Log in as the new user first.

---

### Post by uzzo2 on 2008-07-26
> **CatKiller said:**
> It's probably a good idea to not be logged in as the user you're trying to delete.

Log in as the new user first.
ok, got it done, but none of my files exist any more. i guess they need to be transferred over to the new user. how do i do this?

---

### Post by CatKiller on 2008-07-26
You can rename the old home folder (/home/olduser) for the new user (/home/newuser) in the GUI, or with ```
sudo mv /home/newuser /home/newuser.old
sudo mv /home/olduser /home/newuser
``` and then change the ownership of the folder and everything in it with ```
sudo chown -R newuser:newuser /home/newuser
```

---

### Post by uzzo2 on 2008-07-26
> **CatKiller said:**
> You can rename the old home folder (/home/olduser) for the new user (/home/newuser) in the GUI, or with ```
sudo mv /home/newuser /home/newuser.old
sudo mv /home/olduser /home/newuser
``` and then change the ownership of the folder and everything in it with ```
sudo chown -R newuser:newuser /home/newuser
```
ok, tried that and here's what i got

phil@phillip-desktop:~$ sudo chown -R phil:phil /home/phil
[sudo] password for phil: 
phil is not in the sudoers file.  This incident will be reported.

---

### Post by uzzo2 on 2008-07-26
man i wish i'd just left it alone, it seems like every thing is screwed up now

---

### Post by CatKiller on 2008-07-26
> **uzzo2 said:**
> phil is not in the sudoers file.

> **Oldsoldier2003 said:**
> The best thing to do is create another user account with the name you want and **add it to the admin group**.

Do you have another user on that computer with sudo privileges? If so, log in as that user to add **phil** to the **admin** group.

If not, read this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by uzzo2 on 2008-07-26
what a NIGHTMARE!!! i had to plug my old computer back in. i rebooted and now i can't log in under either username old or new. dead duck in the water now

---

### Post by uzzo2 on 2008-07-26
> **CatKiller said:**
> Do you have another user on that computer with sudo privileges? If so, log in as that user to add **phil** to the **admin** group.

If not, read this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
i was the only one with sudo priveliges that i know of. but i'm lost as hell right now, so who knows.

---

### Post by p_quarles on 2008-07-26
> **uzzo2 said:**
> i was the only one with sudo priveliges that i know of. but i'm lost as hell right now, so who knows.
If you had paid full attention  to the options and instructions given, this wouldn't have happened.

Anyway, to fix the problem, you'll need to select "recovery mode" from the initial boot menu (the screen right after the BIOS - if it's normally hidden, you'll have to press "escape" to see it). This will give you a root shell with which you can fix the problem.

Once your shell loads, run this:
```
adduser *username* admin
```
"username" is the name of user you just created.

Now, type "reboot" and hit enter to restart the computer. The newly created account will now have sudoer privileges.

---

### Post by uzzo2 on 2008-07-26
> **CatKiller said:**
> Do you have another user on that computer with sudo privileges? If so, log in as that user to add **phil** to the **admin** group.

If not, read this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
been to this web site and it's done me no good so far. anyone???

---

### Post by uzzo2 on 2008-07-26
> **p_quarles said:**
> If you had paid full attention  to the options and instructions given, this wouldn't have happened.

Anyway, to fix the problem, you'll need to select "recovery mode" from the initial boot menu (the screen right after the BIOS - if it's normally hidden, you'll have to press "escape" to see it). This will give you a root shell with which you can fix the problem.

Once your shell loads, run this:
```
adduser *username* admin
```
"username" is the name of user you just created.

Now, type "reboot" and hit enter to restart the computer. The newly created account will now have sudoer privileges.
i've followed all the instructions so far, i'm sorry but i'm completely new at all this. i just did this procedure and i still can't log in. i;m getting "your home directory is listed as: '/home/phil' but it does not appear to exist. do you want to log in with the / (root) directory as your home directory? it is unlikely anything will work unless you use a failsafe session."
i've tried running a failsafe session terminal and can't get it to do anything.

---

### Post by uzzo2 on 2008-07-26
how do i just wipe it clean and start over with the live cd?

---

### Post by p_quarles on 2008-07-26
> **uzzo2 said:**
> i just did this procedure and i still can't log in. i;m getting "your home directory is listed as: '/home/phil' but it does not appear to exist. do you want to log in with the / (root) directory as your home directory? it is unlikely anything will work unless you use a failsafe session."
Again, easy to fix: in recovery mode again:
```
mkdir /home/phil
```
Then:
```
chown phil:phil /home/phil
```
That should take care of everything. If not, post any error codes here. 

> i've tried running a failsafe session terminal and can't get it to do anything.
No, that won't do anything, because the failsafe session is for graphical problems, and this isn't a graphical problem. 

There is no need to reinstall. The problem here is that instead of asking how to do things you weren't sure about (adding the new user to the administrative group, making a home directory) you simply ignored those parts of people's instructions. That leads to things getting broken. 

The lesson: if the instructions aren't clear (to you), ask. :)

---

### Post by uzzo2 on 2008-07-26
> **p_quarles said:**
> Again, easy to fix: in recovery mode again:
```
mkdir /home/phil
```
Then:
```
chown phil:phil /home/phil
```
That should take care of everything. If not, post any error codes here. 


No, that won't do anything, because the failsafe session is for graphical problems, and this isn't a graphical problem. 

There is no need to reinstall. The problem here is that instead of asking how to do things you weren't sure about (adding the new user to the administrative group, making a home directory) you simply ignored those parts of people's instructions. That leads to things getting broken. 

The lesson: if the instructions aren't clear (to you), ask. :)

thanks, i'm pretty sure i followed all the instructions given, including these. i can now log on but i still have the other problem of my old files, i can't access them from my new login.

---

### Post by p_quarles on 2008-07-26
> **uzzo2 said:**
> thanks, i'm pretty sure i followed all the instructions given, including these. i can now log on but i still have the other problem of my old files, i can't access them from my new login.
Right, because they are in the old user's home directory. I did in fact mention that you would need to transfer or reassign these files.

In any case, now that you have a working administrative user, you can open a terminal and run:
```
sudo chown phil:phil /home/*oldusername*
```
Then you will be able use Nautilus to manage all the data and configuration files in that directory.

---

### Post by uzzo2 on 2008-07-26
> **CatKiller said:**
> You can rename the old home folder (/home/olduser) for the new user (/home/newuser) in the GUI, or with ```
sudo mv /home/newuser /home/newuser.old
sudo mv /home/olduser /home/newuser
``` and then change the ownership of the folder and everything in it with ```
sudo chown -R newuser:newuser /home/newuser
```

retried this and am still not doing right, here's the output.
phil@phillip-desktop:~$ sudo mv /home/phil /home/phil.old
[sudo] password for phil: 
phil@phillip-desktop:~$ sudo mv /home/phillip /home/phil
mv: cannot stat `/home/phillip': No such file or directory
phil@phillip-desktop:~$ sudo chown -rphil:phil /home/phil
chown: invalid option -- r
Try `chown --help' for more information.
phil@phillip-desktop:~$

---

### Post by p_quarles on 2008-07-26
> **uzzo2 said:**
> phil@phillip-desktop:~$ sudo chown -rphil:phil /home/phil
chown: invalid option -- r
Try `chown --help' for more information.
phil@phillip-desktop:~$
It's telling you what's wrong. Try:
```
sudo chown -R phil:phil /home/phil
```

---

### Post by uzzo2 on 2008-07-26
> **p_quarles said:**
> It's telling you what's wrong. Try:
```
sudo chown -R phil:phil /home/phil
```
ok, tried that and got this.

phil@phillip-desktop:~$ sudo chown -R phil:phil /home/phil
chown: cannot access `/home/phil/.gvfs': Permission denied
phil@phillip-desktop:~$

---

### Post by uzzo2 on 2008-07-26
> **p_quarles said:**
> Right, because they are in the old user's home directory. I did in fact mention that you would need to transfer or reassign these files.

In any case, now that you have a working administrative user, you can open a terminal and run:
```
sudo chown phil:phil /home/*oldusername*
```
Then you will be able use Nautilus to manage all the data and configuration files in that directory.
when i do this i get this.

phil@phillip-desktop:~$ sudo chown phil:phil /home/phillip
[sudo] password for phil: 
chown: cannot access `/home/phillip': No such file or directory

---

### Post by p_quarles on 2008-07-26
> **uzzo2 said:**
> when i do this i get this.

phil@phillip-desktop:~$ sudo chown phil:phil /home/phillip
[sudo] password for phil: 
chown: cannot access `/home/phillip': No such file or directory
What's the output of this?:
```
ls -lh /home
```

---

### Post by uzzo2 on 2008-07-26
> **p_quarles said:**
> What's the output of this?:
```
ls -lh /home
```

phil@phillip-desktop:~$ ls -lh /home
total 16K
drwxr-xr-x 37 chere   chere   4.0K 2008-07-26 19:20 chere
drwxr-xr-x 25 phil    phil    4.0K 2008-07-26 19:29 phil
drwxr-xr-x 24 phil    phil    4.0K 2008-07-26 19:11 phil.old
drwxr-xr-x 61 phillip phillip 4.0K 2008-07-26 14:45 phl
phil@phillip-desktop:~$

---

### Post by p_quarles on 2008-07-26
Right, so you renamed the directory that used to be called /home/phillip. I guess that would be the one that's now called "phil.old."

---

### Post by uzzo2 on 2008-07-26
> **p_quarles said:**
> Right, so you renamed the directory that used to be called /home/phillip. I guess that would be the one that's now called "phil.old."

well the old username was phillip, i was just wanting to shorten it up a bit to phil.

---

### Post by p_quarles on 2008-07-26
> **uzzo2 said:**
> well the old username was phillip, i was just wanting to shorten it up a bit to phil.
Beside the point. There is no longer a directory called /home/phillip, so you can't change the ownership of a directory called that. You'll have to fix the command to refer to whatever the directory is currently called.

---

### Post by uzzo2 on 2008-07-26
> **p_quarles said:**
> Beside the point. There is no longer a directory called /home/phillip, so you can't change the ownership of a directory called that. You'll have to fix the command to refer to whatever the directory is currently called.
ok, how do i do that?

---

### Post by Yannick Le Saint kyncani on 2008-07-26
Well, *next time* that someone wants to change his user name :

1- Go to a console: ctrl+alt+f1
2- Login as your current user
3- Become root: sudo -i
    Enter your password when prompted.
4- Go to /home: cd /home
5- Rename your login directory: mv olduser newuser
6- Edit relevant config files and replace *all occurences*
    of your old user name with the new user name, don't
    screw this up because these config files are very
    important :
    nano /etc/passwd
    nano /etc/shadow
    nano /etc/group
7- Go back to the graphical login screen: alt+f7
8- Login as your new user.
    If anything goes wrong at this point, repeat
    steps 1, 4, 5 and 6.

---

### Post by uzzo2 on 2008-07-26
> **Yannick Le Saint kyncani said:**
> Well, *next time* that someone wants to change his user name :

1- Go to a console: ctrl+alt+f1
2- Login as your current user
3- Become root: sudo -i
    Enter your password when prompted.
4- Go to /home: cd /home
5- Rename your login directory: mv olduser newuser
6- Edit relevant config files and replace *all occurences*
    of your old user name with the new user name, don't
    screw this up because these config files are very
    important :
    nano /etc/passwd
    nano /etc/shadow
    nano /etc/group
7- Go back to the graphical login screen: alt+f7
8- Login as your new user.
    If anything goes wrong at this point, repeat
    steps 1, 4, 5 and 6.

thanks, but i'll not be doing that again i can assure you.

---

### Post by Yannick Le Saint kyncani on 2008-07-26
> **uzzo2 said:**
> thanks, but i'll not be doing that again i can assure you.

Lol, I can understand that :))

( I meant if someone else want to do the same thing in the future and find this thread. )

---

### Post by uzzo2 on 2008-07-26
> **Yannick Le Saint kyncani said:**
> Well, *next time* that someone wants to change his user name :

1- Go to a console: ctrl+alt+f1
2- Login as your current user
3- Become root: sudo -i
    Enter your password when prompted.
4- Go to /home: cd /home
5- Rename your login directory: mv olduser newuser
6- Edit relevant config files and replace *all occurences*
    of your old user name with the new user name, don't
    screw this up because these config files are very
    important :
    nano /etc/passwd
    nano /etc/shadow
    nano /etc/group
7- Go back to the graphical login screen: alt+f7
8- Login as your new user.
    If anything goes wrong at this point, repeat
    steps 1, 4, 5 and 6.

is this the procedure i now need to do to transfer my old files over to the new username?

---

### Post by Yannick Le Saint kyncani on 2008-07-26
> **uzzo2 said:**
> is this the procedure i now need to do to transfer my old files over to the new username?

Nope, you've done so much **** that I don't know the situation you're in right now.

Do you have a working login the way you like, can sudo from it, can login in gnome and have a working desktop ?
I mean is it all working except that you want to get your files back ?

---

### Post by Yannick Le Saint kyncani on 2008-07-26
Hmm, I didn't put those four stars, but my word got rewritten automagically (not that it's bad).

---

### Post by uzzo2 on 2008-07-26
> **Yannick Le Saint kyncani said:**
> Nope, you've done so much **** that I don't know the situation you're in right now.

Do you have a working login the way you like, can sudo from it, can login in gnome and have a working desktop ?
I mean is it all working except that you want to get your files back ?

yes i have a working login now (keeping fingers crossed), just want to be able to access all my old files.

---

### Post by uzzo2 on 2008-07-26
> **Yannick Le Saint kyncani said:**
> Hmm, I didn't put those four stars, but my word got rewritten automagically (not that it's bad).
i kind of feel the same way, i'll be glad when one day (maybe) i can give some advice here instead of asking for it.

---

### Post by Yannick Le Saint kyncani on 2008-07-26
> **uzzo2 said:**
> yes i have a working login now (keeping fingers crossed), just want to be able to access all my old files.

All right, then :

1- Open a console (in accessories, named "terminal" or something like that).
2- Become root: sudo -i  (and enter your password).
3- Go to /home: cd /home
4- Make something to hold your files:
    mkdir newusername/Desktop/OLD/
5- move all your files to this directory :
    mv oldusername newusername/Desktop/OLD/
6- Make those files belong to the new user :
    chown -R newusername:newgroupname newusername/Desktop/OLD
    Chances are that newusername and newgroupname are the same (it's the default with graphical tools I think).
7- Your files should be in your graphical desktop, in a directory named OLD.

---

### Post by uzzo2 on 2008-07-26
> **Yannick Le Saint kyncani said:**
> All right, then :

1- Open a console (in accessories, named "terminal" or something like that).
2- Become root: sudo -i  (and enter your password).
3- Go to /home: cd /home
4- Make something to hold your files:
    mkdir newusername/Desktop/OLD/
5- move all your files to this directory :
    mv oldusername newusername/Desktop/OLD/
6- Make those files belong to the new user :
    chown -R newusername:newgroupname newusername/Desktop/OLD
    Chances are that newusername and newgroupname are the same (it's the default with graphical tools I think).
7- Your files should be in your graphical desktop, in a directory named OLD.
i must have some real bad curse on this thing or something, cause i didn't get very far here.
phil@phillip-desktop:~$ sudo -i
[sudo] password for phil: 
root@phillip-desktop:~# /home: cd /home
-bash: /home:: No such file or directory
root@phillip-desktop:~#

---

### Post by Yannick Le Saint kyncani on 2008-07-26
> **uzzo2 said:**
> root@phillip-desktop:~# /home: cd /home
-bash: /home:: No such file or directory
root@phillip-desktop:~#

The command is "cd /home", not "/home: cd /home".

---

### Post by uzzo2 on 2008-07-26
> **Yannick Le Saint kyncani said:**
> The command is "cd /home", not "/home: cd /home".
i figured it out right after my last post, now i'm getting this.

root@phillip-desktop:/home# mkdir phil/desktop/OLD
mkdir: cannot create directory `phil/desktop/OLD': No such file or directory
root@phillip-desktop:/home#

---

### Post by uzzo2 on 2008-07-26
i've made it a little farther along but now this.

mv: cannot stat `phillip': No such file or directory
phil@phillip-desktop:/home$

---

### Post by Yannick Le Saint kyncani on 2008-07-26
Well, once you're in /home, you can list the remaining directories with "ls".

---

### Post by uzzo2 on 2008-07-26
i have the file "old" on my desktop but there's not any of my old files there, guess i'll have to get back after it in the AM.

---

### Post by uzzo2 on 2008-07-26
> **Yannick Le Saint kyncani said:**
> Well, once you're in /home, you can list the remaining directories with "ls".
ok, finally figured it out with that command, the old files weren't listed under my old username. now the files are in the folder named OLD on my desktop. do i just reboot now and when i log back in everything will be straight?

---

### Post by CatKiller on 2008-07-26
> **p_quarles said:**
> Right, so you renamed the directory that used to be called /home/phillip. I guess that would be the one that's now called "phil.old."

Not if the OP's been following instructions. phil.old is the backup of the automatically-created new user's Home folder, in case it all went wrong and the OP couldn't log in.

The Home folder of the old user, from the ls output, appears to be currently called /home/phl, with 61 directories inside.

So the OP could open a root browser window with ```
gksudo nautilus
``` and copy all the files from /home/phl to /home/phil, followed by changing ownership of all the files in it with **chown** or he could just rename the /home/phl directory to /home/phil and change ownership in the same way. That was the way I'd suggested, but in-between the old user's Home folder seems to have changed from /home/phillip to /home/phl, which is why the directory didn't get renamed, and why the new user didn't have a Home folder for a while.

---

### Post by uzzo2 on 2008-07-26
> **CatKiller said:**
> Not if the OP's been following instructions. phil.old is the backup of the automatically-created new user's Home folder, in case it all went wrong and the OP couldn't log in.

The Home folder of the old user, from the ls output, appears to be currently called /home/phl, with 61 directories inside.

So the OP could open a root browser window with ```
gksudo nautilus
``` and copy all the files from /home/phl to /home/phil, followed by changing ownership of all the files in it with **chown** or he could just rename the /home/phl directory to /home/phil and change ownership in the same way. That was the way I'd suggested, but in-between the old user's Home folder seems to have changed from /home/phillip to /home/phl, which is why the directory didn't get renamed, and why the new user didn't have a Home folder for a while.
here is what i got from the ls command.

root@phillip-desktop:/home# ls
chere  phil  phil.old  phl

phl seems to have my old files

---

### Post by CatKiller on 2008-07-26
> **uzzo2 said:**
> ok, finally figured it out with that command, the old files weren't listed under my old username. now the files are in the folder named OLD on my desktop. do i just reboot now and when i log back in everything will be straight?

If all the files that you want are in a directory on your Desktop, you can copy them into your Home folder from there. Ctrl-h will show you the hidden files too.

If you've already changed ownership on those files so that they belong to your new user (Step 6 in Yannick Le Saint kyncani's instructions) then that's all you need to do. Overwrite the existing files in the new user's Home folder with those from the old user's Home folder and you'll have all the same configuration as you did as the old user. You might need to log out and log back in for some settings to take effect.

---

### Post by CatKiller on 2008-07-26
> **uzzo2 said:**
> phl seems to have my old files

So it's a copy of this that you have on your Desktop?

---

### Post by uzzo2 on 2008-07-26
> **CatKiller said:**
> So it's a copy of this that you have on your Desktop?
yes that's correct

---

### Post by CatKiller on 2008-07-26
> **uzzo2 said:**
> yes that's correct

And do they belong to the new user?

If so, there should be nothing stopping you from copying those files to your Home folder.

---

### Post by uzzo2 on 2008-07-27
> **CatKiller said:**
> And do they belong to the new user?

If so, there should be nothing stopping you from copying those files to your Home folder.

ok, had to quit last night due to a power outage. i was able to copy and paste the folder "phl" into my new home folder so it's there now. i rebooted and still not able to access my old files without clicking places>home folder>phl. is there a way to make it boot from the old file system?

---

### Post by CatKiller on 2008-07-27
> **uzzo2 said:**
> ok, had to quit last night due to a power outage. i was able to copy and paste the folder "phl" into my new home folder so it's there now. i rebooted and still not able to access my old files without clicking places>home folder>phl. is there a way to make it boot from the old file system?

So you've put the folder "phl" as a sub-directory of your Home folder?

What you want to do is put the **contents** of phl in your Home folder. Then all will be as it was.

---

### Post by uzzo2 on 2008-07-27
> **CatKiller said:**
> So you've put the folder "phl" as a sub-directory of your Home folder?

What you want to do is put the **contents** of phl in your Home folder. Then all will be as it was.
the entire phl folder i copied and pasted into the new "phil" home folder, so it's there.

---

### Post by uzzo2 on 2008-07-27
ok guys, looks like i've finally gotten everything back, sorry to be such a pain in the ****. thanks a lot for all the help.

---

