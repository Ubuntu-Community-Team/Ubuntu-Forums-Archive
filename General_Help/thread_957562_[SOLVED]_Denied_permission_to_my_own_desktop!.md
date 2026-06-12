---
title: "[SOLVED] Denied permission to my own desktop!"
date: 2008-10-24
forum: General Help
---

### Post by bunny_basher on 2008-10-24
I have somehow managed to deny access to moving anything to my desktop! I think it's after I accidently moved the folder "Ubuntu" off the LiveCd to my desktop. I also cannot delete this folder!

If i try to save something to my desktop it says you do not have permission and if i try to sreate a folder it does the same!

Also i cannot delete this "Ubuntu" folder. It says its contents is "unreadable" and that it's a link to a folder.

Cheers,
Marcus

---

### Post by geirha on 2008-10-24
Well, what's the permissions on the Desktop folder? Places -> Homefolder, right click Desktop, select properties and then look at the permissions tab. What does it say?

---

### Post by bunny_basher on 2008-10-24
That fixed the folder problem :D I feel stupid now!

Any ideas about removing this annoying folder?

Thanks :D

Marcus

---

### Post by jerome1232 on 2008-10-24
Well my guess is since you draged it off a live cd it's read only, so check it's permissions the same way.

If your unsure post this output for us

```
ls -l path/to/annoying-folder
```

---

### Post by iKonaK on 2008-10-24
Shift+Del
or
from a terminal < sudo rm -r /path/to/file/folder > to understand what you're doing look at  < man rm >
or
from a terminal < gksudo nautillus >  opens the nautilus as root so be careful

---

### Post by bunny_basher on 2008-10-24
When i try to edit it, find the permissions for it or anything, it tells me that there is no such file or directory :S

Thanks for all the help...

Marcus

---

### Post by jerome1232 on 2008-10-24
Well as iKonak mentioned try this method:

press alt+f2, type 'gksu nautilus', navigate to your annoying folder, select it, **hold shift** and press delete, if that doesn't work right click it and goto properties, permissions tab, and make sure you have write access to it. Post a screenshot of that tab you need us to look at it.

---

### Post by Yellow Pasque on 2008-10-24
Go to a terminal.
```
sudo -i
cd /home/<your_user's_name>/Desktop/
rm -rf Ubuntu/*
rmdir Ubuntu
exit
```

---

### Post by bunny_basher on 2008-10-24
Thanks everyone for all the help :D much apreciated :)

I managed to remove it with the "gksu nautilus"

Thanks alot,
Marcus

---

