---
title: "change permissions"
date: 2008-08-20
forum: General Help
---

### Post by ledererster on 2008-08-20
does anybody know how to change permissions for a folder with the console? i'm using 7.10

---

### Post by LowSky on 2008-08-20
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

it may look confusing but if a folder need read/write access for anyone who uses it the command would be
```
sudo chmod 777 -R */path/to/someDirectory*
```

---

### Post by toemos on 2008-08-20
```
sudo chmod 777 /path/to/disk
```

will give permissions to everyone

---

### Post by ledererster on 2008-08-20
Thanks!

---

### Post by ledererster on 2008-08-20
sorry. i'm kind of a noob to ubuntu. what does the /path/to/someDirectory or /path/to/disk mean?

---

### Post by sameerds on 2008-08-20
> **LowSky said:**
> [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

it may look confusing but if a folder need read/write access for anyone who uses it the command would be
```
sudo chmod 777 -R */path/to/someDirectory*
```

Actually this does a little more than intended. It also give execute permissions to all files. If the intention is to give read write access to all files and directories, this is the ideal way to do it:

```
sudo chmod -R +rwX */path/to/someDirectory*
```

The uppercase "X" means: give execute permissions to directories (without which, you can't do anything to the contents of a directory), but retain whatever is the execute permission for each file. Fine-grained control is possible using "u" for file owner, "g" for file group and "o" for others. The above command is equivalent to:

```
sudo chmod -R ugo+rwX */path/to/someDirectory*
```

---

### Post by LowSky on 2008-08-20
> **ledererster said:**
> sorry. i'm kind of a noob to ubuntu. what does the /path/to/someDirectory or /path/to/disk mean?

it means type the actuall path to the file you need to change ownership to 

for example

```
sudo chmod -R +rwX /home
```

would change ownership of your /home folder

---

### Post by ilrudie on 2008-08-21
chmod 777 is a bad idea unless you know what you are doing and know its needed.  If you have to ask how to change permissions chmod 777 especially with a -R flag is not what you should be doing.

---

