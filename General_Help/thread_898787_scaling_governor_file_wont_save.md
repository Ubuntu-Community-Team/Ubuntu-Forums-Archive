---
title: "scaling_governor file wont save"
date: 2008-08-23
forum: General Help
---

### Post by daggerx on 2008-08-23
im trying to put the word powersave in the scaling_governor file but it wont let me save it, I understand that I have to do it for all the cores that I have. The file won't save at all, please help

the error code that im getting is this:

```
gedit could not backup the old copy of the file before saving the new one. You can ignore this warning and save the file anyway, but if an error occurs while saving, you could lose the old copy of the file. Save anyway?
```

I am sudoing to do this and im getting nothing, plase help and thanks.

---

### Post by nitro_n2o on 2008-08-23
look into the directory for gedit backup files and delete them. I rarely use gedit, but I think it uses a tilde after the filename to denote that this is a back up copy

or try another editor.. my vim! 
sudo vim /path/to/file

I have never heard of a problem in editing a text file, it is probably that gedit is acting weird

---

### Post by daggerx on 2008-08-25
When i opened it up in the editor that you suggested, it shows the word "powersave" was already there...weird...dunno what to make of that...

---

### Post by sdennie on 2008-08-25
You can't generally "edit" files in /proc as they are not true files but, you can echo values to them.  Also, changing the scaling governor to powersave generally doesn't save power for modern CPUs and it's best to leave it at ondemand.

---

