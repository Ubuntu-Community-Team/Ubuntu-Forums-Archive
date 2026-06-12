---
title: "[SOLVED] Premission Denied When Emptying Files from Recycling bin"
date: 2008-07-11
forum: General Help
---

### Post by dethredic on 2008-07-11
So, I downloaded the photoshop trial to see if it would run in wine and work nicely. It did I no longer had need for the instillation files so I moved to them the recycling bin. I tried to empty it but I get the error:
> error removing file: permission denied
I can delete other files, just not the photoshop ones. Any ideas on how I can get rid of them?

---

### Post by dracayr on 2008-07-11
do it from the terminal:

in hardy:
```
cd ~/.local/share/Trash/files
```
before hardy:
```
cd ~/.Trash
```
and then:
```
sudo rm *insert file names here*
```
or to just delete all files in trash:
```
sudo rm ~/.local/share/Trash/files/*
```
dracayr

---

### Post by dethredic on 2008-07-11
Here is what I did:
> 
phil@phil:~$ cd ~/.local/share/Trash/files
[email]phil@phil:~/.loca[/email]l/share/Trash/files$ sudo rm ~/.local/share/Trash/files/*
rm: cannot remove `/home/phil/.local/share/Trash/files/Photoshop CS2': Is a directory


---

### Post by dracayr on 2008-07-11
do:

sudo rm -r ~/.local/share/Trash/files/Photoshop\ CS2

This will delete the Photoshop folder

dracayr

---

### Post by dethredic on 2008-07-11
> **dracayr said:**
> do:

sudo rm -r ~/.local/share/Trash/files/Photoshop\ CS2

This will delete the Photoshop folder

dracayr

Great. Thanks man.

---

