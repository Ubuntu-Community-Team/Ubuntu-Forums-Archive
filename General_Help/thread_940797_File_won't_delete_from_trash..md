---
title: "File won't delete from trash."
date: 2008-10-07
forum: General Help
---

### Post by TriggerIsHappy on 2008-10-07
I was reading some articles on howtogeek.com and was interested in a music ID3 tag editor Picard. I downloaded and installed Picard and then was going to delete what I thought was the useless install folder on the desktop. I moved it to the trash and then tried to delete it but it wouldn't delete.

I received the following errors:

There was an error deleting lib.linux-i686-2.5. Error removing file: Permission denied

There was an error deleting temp.linux-i686-2.5. Error removing file: Permission denied

Now I can't put the folder back on the desktop because of these two files. I used "sudo apt-get remove picard" and it showed successful removal, but the folder is still in the trash.

---

### Post by tuxxy on 2008-10-07
You could navigate to the trash as admin using nautilus which should then allow you permission, open a terminal and enter this command

```
sudo nautilus ~/.local/share/Trash
```

Also sometimes you may have trouble deleting files, if so you could run this command but be sure you dont need anything in your trash first! 

```
sudo rm -rf ~/.local/share/Trash

```

---

### Post by Titan8990 on 2008-10-07
I assume you put it in your own trash? 

These commands should take care of it:


cd ~/.Trash

sudo rm -r *


Make extra certain that you are in fact in the trash directory when you execute the second command. If it were it be executed in the wrong place it can really cause some problems.

---

### Post by jerome1232 on 2008-10-07
> **Titan8990 said:**
> I assume you put it in your own trash? 

These commands should take care of it:


cd ~/.Trash

sudo rm -r *


Make extra certain that you are in fact in the trash directory when you execute the second command. If it were it be executed in the wrong place it can really cause some problems.

edit: I made a typo, local, not locale lol

very bad command actually, it's not under .Trash, it's ~/.local/share/Trash/

When you run nautilus as root and delete things, it generally just get's moved to root's trash. So be sure to hold shift then press delete so that it actually get's deleted instead of moved to another trash.

---

### Post by tuxxy on 2008-10-07
> **Titan8990 said:**
> I assume you put it in your own trash? 

These commands should take care of it:


cd ~/.Trash

sudo rm -r *


Make extra certain that you are in fact in the trash directory when you execute the second command. If it were it be executed in the wrong place it can really cause some problems.

The location of trash is ~/.local/share/Trash

If you want to check your root trash you could use these two commands just as you did before

```
sudo nautilus /root/.local/share/Trash
```


```
rm -rf /root/.local/share/Trash
```

---

### Post by TriggerIsHappy on 2008-10-07
Thanks, that did the trick.

---

