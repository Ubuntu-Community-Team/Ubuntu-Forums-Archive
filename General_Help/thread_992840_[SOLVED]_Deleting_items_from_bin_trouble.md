---
title: "[SOLVED] Deleting items from bin trouble"
date: 2008-11-25
forum: General Help
---

### Post by Chamillionaire2 on 2008-11-25
Hello.

Ok basically i have some items in the trash bin that when i try to delete from it, it says Error permisson denied.

If it matters there files from the psp flash folders for those who know what that is. putting custom firmware on it.


Thanks bye.

---

### Post by sisco311 on 2008-11-25
Hi.

open a terminal (Applications -> Accessories -> Terminal)
and type:
```
sudo chown -R $USER: ~/.local/share/Trash/
```then try to empty the trash again.

---

### Post by Chamillionaire2 on 2008-11-25
> **sisco311 said:**
> Hi.

open a terminal (Applications -> Accessories -> Terminal)
and type:
```
sudo chown -R $USER: ~/.local/share/Trash/
```then try to empty the trash again.

Still access denied. could i boo into windows and delete the file from there? if so whats the dir to the trash folder? i coudent find it myself.


btw im completely new to ubuntu.

---

### Post by sisco311 on 2008-11-25
when you run the above command you are asked for your password.
type your password and press enter.

you can also try to open the file manager as root an delete the files:
```
gksu nautilus ~/.local/share/Trash/files
```

the trash is in a hidden folder in your home folder(.local/share/Trash).
you can press Ctrl+H to list the hidden files and folders in the file manager.

---

### Post by Chamillionaire2 on 2008-11-25
> **sisco311 said:**
> when you run the above command you are asked for your password.
type your password and press enter.

you can also try to open the file manager as root an delete the files:
```
gksu nautilus ~/.local/share/Trash/files
```

the trash is in a hidden folder in your home folder(.local/share/Trash).
you can press Ctrl+H to list the hidden files and folders in the file manager.

Cool the gksu nautilus ~/.local/share/Trash/files   did it for me. thanks alot sisco311 :).

---

### Post by sisco311 on 2008-11-25
you're welcome.

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by kpothi on 2008-12-11
Thank you dear friend,

I had the same issue and was able to solve after seeing your answer.

---

