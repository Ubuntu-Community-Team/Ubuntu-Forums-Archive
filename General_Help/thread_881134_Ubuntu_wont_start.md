---
title: "Ubuntu wont start"
date: 2008-08-05
forum: General Help
---

### Post by collinge on 2008-08-05
holy crap - i shut my Dell computer down and it was fine - i might have made some changes in the 'Advanced Desktop Effects'  Now when you turn on the computer after i type in my name and password the default Ubuntu background color shows and a white box at the top left of the screen shows up and nothing else. It wont let me do anything - i am kinda new to Ubuntu and Linix so -  - i dont want to have to lose all my stuff.

---

### Post by jimv on 2008-08-05
You may need to reset your Compiz settings.  Press control+alt+f1 and type

```
 mv ~/.gconf/apps/compiz ~/.gconf/apps/compiz.old
```

and press control+alt+f7 to get back to the gui.  Then press control+alt+backspace to restart the X server.

---

### Post by collinge on 2008-08-05
i tried 
```
 mv ~/.gconf/apps/compiz ~/.gconf/apps/compiz.old
``` but it said missing file or directory... are you sure this address would be the correct one? do i login as root user - "sudo su" ?

---

### Post by mfaust731 on 2008-08-05
just add sudo to the previous command

---

### Post by jimv on 2008-08-05
> **collinge said:**
> i tried 
```
 mv ~/.gconf/apps/compiz ~/.gconf/apps/compiz.old
``` but it said missing file or directory... are you sure this address would be the correct one? do i login as root user - "sudo su" ?

No, it's in your profile, you don't need sudo.  The other thing I can think of is try logging in with the Failsafe Gnome session.  There's a little button for Session on the logon screen that lets you choose that.

---

### Post by collinge on 2008-08-05
I tried the code again with only sudo and again with nothing.
It still says there is no such file or directory. 
There is a way to log in a gnome session, but it does the same thing. The screen turns a peach color with a white box in the upper left hand corner. It will not let me do anything. Any other suggestions?:confused:

---

### Post by PmDematagoda on 2008-08-05
At the login screen, go to Options>Sessions and then select Gnome Fail-Safe from the list, then try logging into your session.

---

### Post by collinge on 2008-08-05
when I log in as Gnome failsafe, nothing changes.
could we have deleted the .compiz somehow? It continues to say no such file or directory exists.

---

### Post by jimv on 2008-08-05
try this:

mv ~/.gnome2 ~/.gnome2.old

---

### Post by collinge on 2008-08-06
This code will not work either, it still says no such file or directory.
Nothing I have tried so far has made any difference. I really don't want to have to lose everything. Is there anything else I can do?

---

### Post by collinge on 2008-08-06
Please Help, I am out of ideas and really getting worried.

---

### Post by geirha on 2008-08-06
Boot into recovery mode and create a new user with the command
```
adduser *newusername*
adduser *newusername* admin

```
The second command adds this new user to the admin group so it can use sudo.

Boot back into your system normally and try to log in with this new user. Does that work? If it works, that means there is some problem with the configuration files of your old user. One option is to copy all the data you want to keep from the old user's home directory to your new user's directory, then remove your old user, and add it again to make a fresh start.

---

### Post by collinge on 2008-08-06
Code:
 mv ~/.gconf/apps/compiz ~/.gconf/apps/compiz.old

when I try this, I get this
mv .cannot stat '/root/.gnome2': No such file or directory.

---

### Post by geirha on 2008-08-06
> **collinge said:**
> Code:
 mv ~/.gconf/apps/compiz ~/.gconf/apps/compiz.old

when I try this, I get this
mv .cannot stat '/root/.gnome2': No such file or directory.

You are running that command as root. That's wrong. Type the following to switch to your user: ```
sudo -u *yourusername* -i
```
Then run the mv-command.

---

### Post by collinge on 2008-08-06
> **geirha said:**
> Boot into recovery mode and create a new user with the command
```
adduser *newusername*
adduser *newusername* admin

```
The second command adds this new user to the admin group so it can use sudo.

Boot back into your system normally and try to log in with this new user. Does that work? If it works, that means there is some problem with the configuration files of your old user. One option is to copy all the data you want to keep from the old user's home directory to your new user's directory, then remove your old user, and add it again to make a fresh start.


when I did this it worked, THANK YOU SOO MUCH.
all of my settings are back to default, but I can figure that out. THANKS AGAIN

---

