---
title: "[SOLVED] Restart/shutdown options missing?"
date: 2008-08-16
forum: General Help
---

### Post by nasamuffin on 2008-08-16
I've had this problem for a month or so, but have been too busy making other things work to worry about it too much.... now that I've got just about everything else working, I want to get this issue fixed for good.

In my logout/change user menu screen, I don't have icons to shut down or restart my machine.  I couldn't take a screenshot of the situation, but I did take a picture that gets the point across. :)

[IMG]http://i33.tinypic.com/2di2104.jpg[/IMG]

If this can't be fixed, I would be content to know the shell commands for shutting down or restarting, if there are any.

---

### Post by Naatan on 2008-08-16
I think it happens when other users with administration privileges are logged in or when you don't have administration privileges..

Open System > Administration > Users and Groups

Click Unlock, enter your password, select your user and click properties. Go to the "User Privileges" tab and make sure "Administer the System" is checked.

Also check what other users are logged in by typing the following in terminal:

$ users

And check if there are any other users logged on.

---

### Post by nasamuffin on 2008-08-16
I checked, and I am the only user logged in.  I also have administrate the system checked.  Thanks for the suggestion though :)

---

### Post by Sinkingships7 on 2008-08-16
Command to shutdown:```
sudo shutdown -h now
```
Command to restart: ```
sudo reboot
```

---

### Post by Naatan on 2008-08-16
Try checking the following post

[http://ubuntuforums.org/showpost.php?p=1426703&postcount=5](http://ubuntuforums.org/showpost.php?p=1426703&postcount=5)

---

### Post by Yuki_Nagato on 2008-08-16
Right-Click on a panel (I have only used GNOME and XFCE; I know squat about KDE) and create a launcher.  You can enter the terminal commands above into a launcher, and then put them next to the Red Button in the upper-right hand corner of the screen.

---

### Post by nasamuffin on 2008-08-16
> **Sinkingships7 said:**
> Command to shutdown:```
sudo shutdown -h now
```
Command to restart: ```
sudo reboot
```

Whee, thanks!

> **Naatan said:**
> Try checking the following post

[http://ubuntuforums.org/showpost.php?p=1426703&postcount=5](http://ubuntuforums.org/showpost.php?p=1426703&postcount=5)

That fixed me up.  Thanks muchly, and my apologies for not making my search more thorough.

Thanks oodles, both of you! :D

---

