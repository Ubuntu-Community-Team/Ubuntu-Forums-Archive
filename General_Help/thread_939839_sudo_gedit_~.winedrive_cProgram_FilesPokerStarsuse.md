---
title: "sudo gedit ~/.wine/drive_c/Program Files/PokerStars/user.ini"
date: 2008-10-06
forum: General Help
---

### Post by hjaeger on 2008-10-06
Cannot config sudo gedit ~/.wine/drive_c/Program Files/PokerStars/user.ini


gedit only displays a blank screen.

---

### Post by doug1212 on 2008-10-06
Hi
Do you require admin privileges to edit as its in your home directory?, anyway you will have to enclose the path in quotes as it has spaces in it.
Doug

---

### Post by jerome1232 on 2008-10-06
a: you don't need sudo to edit that

b: when A path has spaces in it there are two ways to type that path

```

# add a \ before the space
gedit ~/.wine/drive_c/Program\ Files/PokerStars/user.ini
# or as the above poster stated enclose it in quotes
gedit "~/.wine/drive_c/Program Files/PokerStars/user.ini"
```

As you work on the command line you'll come to appreciate tab completion, type out some of the name and hit tab once, it should auto complete the name, if it can't hit tab again it'll show a list of everything that matches what you've typed so far

---

### Post by Titan8990 on 2008-10-06
Yep, the command would be:

sudo gedit ~/.wine/drive_c/Program\ Files/PokerStars/user.ini

---

### Post by Tom--d on 2008-10-06
> **Titan8990 said:**
> Yep, the command would be:

sudo gedit ~/.wine/drive_c/Program\ Files/PokerStars/user.ini

but with sudo, it will look in the root home folder, not yours. So with Sudo you would need /home/yourusername/.wine/etc/etc/etc

But you dont need root to look at the file. All files under .wine is yours. Not roots.

---

### Post by Titan8990 on 2008-10-06
That was something I overlooked. My primary objective with that post was just to show that spaces need the nasty windows slash.

---

### Post by jerome1232 on 2008-10-06
actually no, when you use sudo, ~/ still points to the original users home directory, the environment doesn't change. 

You can run the following commands to show it.
```
sudo echo $USER
sudo cd ~/
echo $PWD
```

What will happen is the file will become owned by root and then possibly cause the program to not work because it can't write to it. In that case a simple chown will fix it
```
sudo chown $USER:$USER ~/.wine/drive_c/Program\ Files/PokerStars/user.ini
```

---

