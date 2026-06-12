---
title: "[SOLVED] User and group problems"
date: 2008-08-28
forum: General Help
---

### Post by Arcnsparc on 2008-08-28
So I am trying to make different accounts to show off ubuntu and hopefully turn my friends into linux users.  

First I wanted a guest account, and I started this thread:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=903066](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=903066)
which aloshbennett was kind enough to point me here:
[http://ubuntuforums.org/showthread.php?t=819198](http://ubuntuforums.org/showthread.php?t=819198)
I ran those commands in the link above and it worked great!

But now I am trying to add two more users, one for a special high speed config for when I want to run Virtualbox and some other high demand programs.  And the other is going to be dressed up like a Mac to turn those book users to ubuntu...

But here is the problem, when I add a new user via the hardy 'users and groups' GUI the group gets added but the user doesnt...  

for example:  I add the user 'apple' with password apple1 and set it to desktop user without admin.  The group 'apple' appears in the 'Manage Groups' list but now 'apple' user is created, and no 'apple' folder is made in /home.

I tried:
jake@MultiVAC-2:~$ sudo adduser apple
adduser: The group `apple' already exists.

I also tried to delete the 'apple' group and then try making it again, still with no user or folder generated...

If anyone has any ideas please let me know.

---

### Post by aysiu on 2008-08-29
Perhaps the folder gets created when you actually log in as that user?

---

### Post by Arcnsparc on 2008-08-29
I tried logging out and then logging in as a different user but that didn't work.  No new users are being created.  I am betting that it has something to do with these commands:
```
sudo sed -i 's/#PasswordRequired=false/PasswordRequired=false/' /etc/gdm/gdm.conf
```
and
```
sudo sed -i 's/nullok_secure/nullok/' /etc/pam.d/common-auth
```

I am going to try and undo these commands, create the users I want, and then redo these to remove the password prompt.  If that fails I am going to try and re-install the user & group package via synaptic....  Ideas are still welcome, thanks.

---

### Post by Tux+ on 2008-08-29
Did you try logging in via X or the terminal? If you logged in via GUI does it give you an error message?

Try creating the home directory using the terminal:

Create the home directory for the user
```
sudo mkdir /home/apple
```
Change the permissions to allow user apple
```
chown apple:apple /home/apple
```
Set the home directory of apple
```
sudo apple -d /home/apple/
```

---

### Post by Arcnsparc on 2008-08-29
I tried making the folder manually and got this result

```
jake@MultiVAC-2:~$ sudo mkdir /home/apple
[sudo] password for jake: 
jake@MultiVAC-2:~$ chown apple:apple /home/apple
chown: invalid user: `apple:apple'
jake@MultiVAC-2:~$ sudo adduser apple
adduser: The group `apple' already exists.
jake@MultiVAC-2:~$ sudo apple -d /home/apple/
sudo: apple: command not foun
```

I am trying to find away to reinstall the "Users and Groups" module via synaptics, but I cant figure out what it is called... Thanks.

---

### Post by Tux+ on 2008-08-29
> **Arcnsparc said:**
> I tried making the folder manually and got this result

```
jake@MultiVAC-2:~$ sudo mkdir /home/apple
[sudo] password for jake: 
jake@MultiVAC-2:~$ chown apple:apple /home/apple
chown: invalid user: `apple:apple'
jake@MultiVAC-2:~$ sudo adduser apple
adduser: The group `apple' already exists.
jake@MultiVAC-2:~$ sudo apple -d /home/apple/
sudo: apple: command not foun
```

I am trying to find away to reinstall the "Users and Groups" module via synaptics, but I cant figure out what it is called... Thanks.

Sorry the last command was wrong its:

```
sudo usermod apple -d /home/apple/
```

forgot the 'usermod' command.

What do you get when you list the users on the box? I can't remember the command exactly but I'm sure google will tell you (sorry).

---

### Post by aysiu on 2008-08-29
I'm at a loss here. Clearly something has malfunctioned, but I don't know how to diagnose or fix it.

---

### Post by Arcnsparc on 2008-08-29
TUX+
```
jake@MultiVAC-2:~$ sudo usermod apple -d /home/apple/
[sudo] password for jake: 
usermod: user /home/apple/ does not exist

```

Thanks for the help on the command line, you too aysiu.  I am sending a message to Bluefrog in hopes the he/she can help me undo these "Passwordless guest account" commands, I think that is where the trouble is stemming from...

---

### Post by bodhi.zazen on 2008-08-29
```
sudo useradd apple -g apple
```(or you could delete the group apple if you wish and start again)

then you must manually finish the config :

```
sudo cp /etc/skel/.* /home/apple
#You will get an error message, ignore it

mkdir /home/apple/Desktop

sudo chown -R apple.apple /home/apple
sudo chsh apple
# -> Enter /bin/bash
```done :)

---

### Post by Arcnsparc on 2008-08-30
Holy Goddamnit that worked.  For real this is why I love ubuntu.  For the record:
```
jake@MultiVAC-2:~$ sudo useradd apple -g apple
[sudo] password for jake: 
jake@MultiVAC-2:~$ sudo cp /etc/skel/.* /home/apple
cp: target `/home/apple' is not a directory
jake@MultiVAC-2:~$ sudo chown -R apple.apple /home/apple
chown: cannot access `/home/apple': No such file or directory
jake@MultiVAC-2:~$ sudo chsh apple
Changing the login shell for apple
Enter the new value, or press ENTER for the default
	Login Shell [/bin/sh]: /bin/bash
jake@MultiVAC-2:~$ 
```

Then all i had to do was add the account's name and password in the user & groups GUI.

*edit:  no home folder was there so I made one and redid this part:

```

jake@MultiVAC-2:~$ sudo cp /etc/skel/.* /home/apple
cp: omitting directory `/etc/skel/.'
cp: omitting directory `/etc/skel/..'
jake@MultiVAC-2:~$ sudo chown -R apple.apple /home/apple

```

those looked like the executed correctly, I am going to try and log in now....

Thanks a lot!  No I can deck out a "mac" account to turn my apple friends into ubuntu junkies, they already hate windows so they are halfway already :P

---

### Post by Arcnsparc on 2008-08-30
Looks like I am not out of the woods yet.  The changes I made to the 'apple' account (password and user name) with the GUI didn't stick and I tried to log into the new account using both a blank password and the one I selected.  .bash_logout, .bashrc, and .profile all made it into the apple home folder.  I did this again for good measure:
```
jake@MultiVAC-2:~$ sudo chsh apple
Changing the login shell for apple
Enter the new value, or press ENTER for the default
	Login Shell [/bin/bash]: /bin/bash

```

and it still wont accept any sort of password....

but i got it now!!!  I just deleted the account's password like I did with the guest account:

```
jake@MultiVAC-2:~$ sudo passwd -d apple
Password changed.

```

So here is my question:
Since I definitely broke the hell out of my 'Users and Groups' GUI how can I can change settings that would normally be done in the GUI with the command line instead?  Account name, password, and privileges are the main concern...

again, thanks for all of the help guys and girls!

---

### Post by bodhi.zazen on 2008-08-30
You set a password with 

sudo passwd <user>

You make a new user with :

sudo adduser <user>

You add the new user to a group with either of the two following commands :

sudo adduser <username> <group>
sudo usermod -G <group> -a <user>

You manage ownership and permissions with :

chown and chmod

---

