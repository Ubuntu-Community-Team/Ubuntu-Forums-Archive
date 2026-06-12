---
title: "Simple noob question, can close after its answered"
date: 2008-10-05
forum: General Help
---

### Post by tlovaj on 2008-10-05
whats the terminal command to delete a file that looks like this


"file.txt~"



I'm a noob i know . . . 


Thanks!

---

### Post by ad_267 on 2008-10-05
rm file.txt~

If you want to delete all files that end in ~ in a directory:
rm *~

To find all of them in your home directory and delete them:
find ~ -name *.*~ -type f -exec rm '{}' \;

Or just move them to the trash:
find ~ -name *.*~ -type f -exec mv '{}' ~/.local/share/Trash/files \;

In the previous two examples the first ~ is referring to your home directory.

---

### Post by monkeyking on 2008-10-05
be carefull using rm *~,
a simple typo and you end up deleting all files in you ~/ not dirs though

---

### Post by Neo_The_User on 2008-10-05
Yeah make sure you are not in the root of your hard drive / filesystem when doing any of the "rm" commands and if you are, make sure you type in the file name / directory EXACTLY how its supposed to be otherwise your system might be a really big mess.

---

### Post by jerome1232 on 2008-10-06
I generally keep those around though, they are backups that vim, gedit and perhaps other text editors automatically make every time you make a change to a file. That way you can go back one save ago if it turns out you didn't want that change after all.

---

