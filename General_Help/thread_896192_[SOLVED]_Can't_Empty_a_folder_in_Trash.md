---
title: "[SOLVED] Can't Empty a folder in Trash"
date: 2008-08-20
forum: General Help
---

### Post by cybrsaylr on 2008-08-20
This foldler: madwifi-ng-r2756+ar5007 is in Trash.

It is an empty folder with no contents but when I try to delete or empty the trash it won't delete. I get this message: 

Error while deleting.
There was an error deleting ath_pci.mod.
Show more details
Error removing file: Permission denied

How can I get rid of this empty folder?

---

### Post by iaculallad on 2008-08-20
> **cybrsaylr said:**
> This foldler: madwifi-ng-r2756+ar5007 is in Trash.

It is an empty folder with no contents but when I try to delete or empty the trash it won't delete. I get this message: 

Error while deleting.
There was an error deleting ath_pci.mod.
Show more details
Error removing file: Permission denied

How can I get rid of this empty folder?

On your terminal:

```
sudo rm -rf /home/your_username/.local/share/Trash/*
```

OR

```
gksudo nautilus
```

and browse your Trash folder and delete the file.

---

### Post by cybrsaylr on 2008-08-20
iaculallad,

Tried both of them and nothing.

On the second choice it wouldn't let me in the Trash.

---

### Post by iaculallad on 2008-08-20
> **cybrsaylr said:**
> iaculallad,

Tried both of them and nothing.

On the second choice it wouldn't let me in the Trash.

Try:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by cybrsaylr on 2008-08-21
Got this from another thread.

> this code above will delete all in trash with one shot

sudo rm -rf ~/.local/share/Trash

I put it in and the file is gone.

Thanks for the help.

---

### Post by Marcel-X on 2008-09-26
I copied some files from a dvd and deleted them later. Now I'm stuck with some files in the Trash that are read only. They can not be found in ~/.local/share/Trash/files/ or /root/.local/share/Trash/files.

In Nautilus the path trash://// will show them. With "gksudo nautilus" the path trash:/// tells me "/home/<username>/trash: could not be found"

I'm running 8.10 alpha6. Any help will be appreciated.

---

