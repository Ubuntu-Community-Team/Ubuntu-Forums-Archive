---
title: "Permission denied?"
date: 2008-07-18
forum: General Help
---

### Post by sugarplumfairy on 2008-07-18
i opened a terminal in the system log to delete the log files, for today, (do i need to specify something to make sure it only deletes today's files?) 
but when i type in the folder name i get permission denied?
Perhaps i should be typing this in the absolute beginner forum but my question is pretty specific. Why is permission denied when i'm the administrator?

---

### Post by Potatoj316 on 2008-07-18
Linux, unlike Windows, does not let people use their computer as a Administrator.  They have the ability to temporaraily become root (the admin) by using sudo.  Sudo lets you do things that usually result in a permission denied for regular users.  So when typing your command in the terminal put a sudo infront of it then enter your password when it asks.

---

### Post by TeoBigusGeekus on 2008-07-18
You are not an administrator by default in Ubuntu - you're just a user.
In order to delete something as an administrator you can do 2 things:

1)Open a terminal and type
```
sudo rm /path/to/unwantedfiles/*
```

[COLOR="Red"]Be extremely careful with that command.[/COLOR]

2)Open a terminal and type
```
gksudo nautilus
```
Nautilus will open with you having admin rights and you can do whatever you want.

---

### Post by Potatoj316 on 2008-07-18
Be careful in nautilus with admin rights, theres a reson you usually dont get them.

---

### Post by sugarplumfairy on 2008-07-18
Should i be careful using the first command or the second command?
???
what could go wrong?

---

### Post by Potatoj316 on 2008-07-18
If you use sudo nautilus (which will solve your problem by the way) you then can delete whatever you want.  You are not the superuser by default because you could accidentaly delete some files that are necessary for the computer to boot or run.  Im not saying don't do that, Im just saying be careful.

---

### Post by rune0077 on 2008-07-18
I think the first post meant be careful with the first command, 'coz once you use "rm" and hit return, the file is gone, so doublecheck that you typed in the right path before executing the command.

---

