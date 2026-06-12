---
title: "Problem installing software"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by mao_dze_dun on 2009-06-23
Hello,
I'm obviously a new Ubuntu user (exactly one week). I like this OS a lot but there are still things I can hardly get the hang of. On few occasions I had the problem of trying to install a program and Ubuntu denying me access to the particular folder. Just today I tried to install the game Alpha Centauri (linux version) in the default folder the game is set to install itself and - access denied (or something similar). Same problem when trying to add new plug-ins or scripts to GIMP - the system just won't let me do it (although the folder is already full of the scripts and plu-ins GIMP has in it's base package). And there is now way Ubuntu would let me change xorg.conf manually (let alone via the nvidia pannel) so I have to reset my screen resolution every time I log on. I have an administrator account (it is the only account really because I'm the only user of the PC). I was used to being able to do whatever I please in Windows and it is kind of annying to have my new OS limit me in this way. I'm sure the solution is probably something ridiculously simple to an old linux/ubuntu user but for me it is like rock climbing with my hands tied behind my back. Thanks in advance for the help.

---

### Post by Doval on 2009-06-23
I'm relatively new to Ubuntu and also found this to be fairly aggravating at first. The reason, as far as my understanding goes, is that Linux has a permission system in place, both for protecting important system files and to allow users to restrict other users' access to certain files and folders.

Pretty much everything outside of your home folder is "owned" by the "root" account, the account which has complete access to everything in the system. The solution is to "borrow" the root account to run Nautilus by typing "gksu nautilus" (no quotes) at the command line. That instance of Nautilus will be operating as root, you won't have any restrictions when making/deleting/etc files or folders.

I recommend you read the [Ubuntu Pocket Guide and Handbook](http://www.ubuntupocketguide.com/index_main.html). It explains users, groups, and permissions, as well as many other things about Linux/Ubuntu that I found somewhat confusing or intimidating.

---

### Post by The-Don on 2009-06-23
Open terminal and type:
```
sudo nautilus
```
That will give you access to all the files on your system (think of it as Windows Explorer with admin rights).

Here is a guide on precisely this topic...[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

After reading that guide I felt like a pro lol.

P.S.
I'm one week old too :D

---

### Post by mao_dze_dun on 2009-06-24
Ahh a completely different experience - just what I don't need during an exam session :P.
Thanks a lot mates - your help was invaluable. Now I'm free to screw with my OS as if it were Windows :D

---

### Post by dsavi on 2009-06-24
Haha, I screw with my OS as if it were *not* Windows- Unix (And therefore Linux) gives you the rope, and allows you to hang yourself if you like. sudo [command] will let you basically do anything, but still be careful.

Also, never try to log in to Ubuntu as root. It's a common mistake we all have made, I think. Sure, type in su every once in a while if you can't be bothered to sudo multiple commands, but logging in as root can be suicide.

---

### Post by mao_dze_dun on 2009-06-24
Well last week I sort of unlocked root from user groups and after that things got so bad I had to format and re-install Ubuntu, so I guess I got my lesson about that one. Thank you for the tip nevertheless.

---

