---
title: "I Can't find MY TRASH?"
date: 2008-07-22
forum: General Help
---

### Post by adn258 on 2008-07-22
I can't find my trash can anywhere?  I have tried going to the home folder and hitting control+h to view hidden files and there is no .Trash I have tried other locations to like local/Share.  I cannot navigate to the trash with the terminal.  The only way I can get to the trash if clicking it's icon in the lower right hand corner on the GNOME desktop.  Unfortunately there are a bunch of files in there I can't delete either by emptying the trash unless I can get there with the terminal which as you know i have already tried hard to do.  What should I do?

---

### Post by scragar on 2008-07-22
Gutsy and earlier:```
nautilus ~/.Trash
```
Hardy and later:```
nautilus ~/.local/share/Trash
```

---

### Post by iaculallad on 2008-07-22
> **adn258 said:**
> I can't find my trash can anywhere?  I have tried going to the home folder and hitting control+h to view hidden files and there is no .Trash I have tried other locations to like local/Share.  I cannot navigate to the trash with the terminal.  The only way I can get to the trash if clicking it's icon in the lower right hand corner on the GNOME desktop.  Unfortunately there are a bunch of files in there I can't delete either by emptying the trash unless I can get there with the terminal which as you know i have already tried hard to do.  What should I do?

For User's Trash, try to browse:

> /home/user_name/.local/share/Trash

For Root's Trash, try to browse:

> ~/.local/share/Trash/files

And, to clean your Trash:

```
sudo rm -rf ~/.local/share/Trash/*
```

---

### Post by Separ on 2008-07-22
EDIT: Actually disregard that, it gives an error saying /home/user/trash wasn't found :p

Do what iaculallad said.

---

### Post by Dr Small on 2008-07-22
Does anyone know why the Trash directory got moved on the Hardy release? I think it just seems odd, after having it in ~/.Trash all those years.

---

### Post by scragar on 2008-07-22
I'm sure there's a logical explination for why it had to be moved, I just can't think of one. I know they must expect it to be pretty perminant though, picking an LTS to make the change rather than a normal release.

---

### Post by adn258 on 2008-07-23
> **iaculallad said:**
> For User's Trash, try to browse:



For Root's Trash, try to browse:



And, to clean your Trash:

```
sudo rm -rf ~/.local/share/Trash/*
```

All I know is that sudo rm -rf ~/.local/share/Trash/* worked GREAT FOR ME.  Thank you so much.  I was able to browse to the trash too in the terminal with ~/.local/share/Trash/*

Thanks

---

### Post by drs305 on 2008-07-23
There is also root trash at /root/.local/share/Trash

You can find all your partition's trash folders by running this:
```
sudo find / -type d -iname Trash
```

---

