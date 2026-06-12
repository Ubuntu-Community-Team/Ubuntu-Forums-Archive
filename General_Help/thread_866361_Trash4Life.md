---
title: "Trash4Life"
date: 2008-07-21
forum: General Help
---

### Post by dougdavidson on 2008-07-21
I am attempting to consolidate CD-ROM with image files to a DVD with folders. I copied the CD-ROM to my Home folder where I sorted the data to the folders and then made the DVD. When I moved the files to trash is when the problem occured, in that I was denied permission to Empty the Trash. I tried changing Permission to no avail, I tried using terminal sudo -i but was unable to determine where the Trash is located. It seems I am stuck with 418 mb in the Trash basket. Any one have a solution?

---

### Post by drs305 on 2008-07-21
You can probably find it with:
```
sudo find / -type d -iname Trash
```

Once you locate the folder:
```
gksu nautilus
```

Navigate to and delete the .Trash/files folder.

---

### Post by Tim Sharitt on 2008-07-21
The trash folder is now located at '/home/USERNAME/.local/share/Trash'.
There is a folder for the actual files and a folder for info about the files.

---

