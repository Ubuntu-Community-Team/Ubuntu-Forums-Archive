---
title: "Installing Bin File, not working..."
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by The_Real_Anna on 2009-01-28
I have a .bin file on my desktop. (It's a pirate game!)

I opened the terminal and typed in:

anna@anna-desktop:~$ sh yohoho-115-42-install.bin

And this is what it said:

sh: Can't open yohoho-115-42-install.bin


Am I stooooopid? Thanks in advance! :popcorn:

EDIT: More on my futile attempt.....

anna@anna-desktop:~$ chmod 755 yohoho-115-42.bin

chmod: cannot access `yohoho-115-42.bin': No such file or directory
anna@anna-desktop:~$ cd desktop

bash: cd: desktop: No such file or directory

anna@anna-desktop:~$ ls

42804-domino-0.4.tar.bz2  amsn_received  Documents  Incomplete         Music   Pictures  Templates       Videos
AllDayLong.xml            Desktop        FrostWire  marker_bottom.gif  Photos  Public    Video Projects  wp-config.php

anna@anna-desktop:~$ SUDO CHMOD +X yohoho-115-42.bin

bash: SUDO: command not found

anna@anna-desktop:~$ SUDO CHMOD +X yohoho-115-42-install.bin

bash: SUDO: command not found

anna@anna-desktop:~$ sudo chmod yohoho-115-42-install.bin

chmod: missing operand after `yohoho-115-42-install.bin'
Try `chmod --help' for more information.

anna@anna-desktop:~$   -------------ARRRRG MATEYS! I NEED HELP!

---

### Post by Partyboi2 on 2009-01-28
anna@anna-desktop is your /home folder, to get to your Desktop type
```
cd ~/Desktop
```
then try installing the game.

---

### Post by The_Real_Anna on 2009-01-28
WORKED!

Thanks.

Sorry I get confused with Terminal....

Thanks again. Stay gorgeous!

---

### Post by jerome1232 on 2009-01-28
I think you need to remember that Linux is case sensitive.

So Desktop is different from desktop and DESKTOP. Gotta watch capitals.

---

