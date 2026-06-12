---
title: "[SOLVED] Issue with folders in /home/username"
date: 2008-11-08
forum: General Help
---

### Post by Selphy on 2008-11-08
Hi,

I've got a bit of an issue with folders I make in my home directory. I created a folder called .game to add into /home/username/ and after doing it It won't appear. I tried to make it again to see if it worked and it said the file existed already. Why is it that the '.' in front made the folders stealth, how do I delete this folder and how can I view them in the future. 

Thanks!

---

### Post by ju2wheels on 2008-11-08
Any folder that starts with a '.' is a hidden folder. They are typically used to store program settings and user configurations.

They are visible on the command line by running ls with the all option:
```

ls -la

```

If you use the graphical file browser (Nautilus), then select View-> Show Hidden Files on the menu.

---

### Post by Steve1961 on 2008-11-08
You ccan also see hidden files in nautilus by just selecting the 'show hidden files' option from the view menu.

Just for information, configuration files and folders are generally hidden by default, and the way that's done in linux is by putting a . in front.

---

### Post by FrostyFlames on 2008-11-08
The folder is there, you can type this at a terminal:```
cd .game
``` and it will take you to that folder.

If you want to remove it, you can do so with rmdir or rm -r.

---

### Post by Selphy on 2008-11-08
Ahhh that did it , thank you for the information. Semi related note I tried to change the permissions in the properties of my home folder thinking it had something to do with the access. It gave me an error telling me it couldn't change the permissions of :z and ::d but the access changed from read only to read and write and stayed that way. Is this going to cause problems?

---

