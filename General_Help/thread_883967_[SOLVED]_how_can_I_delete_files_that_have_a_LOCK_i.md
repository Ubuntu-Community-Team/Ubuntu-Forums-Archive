---
title: "[SOLVED] how can I delete files that have a *LOCK icon ??"
date: 2008-08-08
forum: General Help
---

### Post by sendblink23 on 2008-08-08
I want to erase files with the *LOCK* icon, but it always gives me errors when trying to send it to the Trash

here my Print Screen of what i want to delete:
[IMG]http://i29.photobucket.com/albums/c272/sendblink23/Screenshot-1.png[/IMG]

---

### Post by damoxc on 2008-08-08
From terminal:
```
sudo rm -r "~/Desktop/Adobe Photoshop Pro CS2 v9.0 Full ISO + WORKING Keygen"
```

---

### Post by GreenN00b on 2008-08-08
Or ```
gksudo nautilus
``` to run nautilus in super user mode and you can delete anything then. Please be careful when using this.

---

### Post by sendblink23 on 2008-08-08
> **damoxc said:**
> From terminal:
```
sudo rm -r "~/Desktop/Adobe Photoshop Pro CS2 v9.0 Full ISO + WORKING Keygen"
```

it gives me this:

```
rm: cannot remove `~/Desktop/Adobe Photoshop Pro CS2 v9.0 Full ISO + WORKING Keygen': No such file or directory

```

> **GreenN00b said:**
> Or ```
gksudo nautilus
``` to run nautilus in super user mode and you can delete anything then. Please be careful when using this.

I can't manage to find the Actual Desktop i have.. i did use that Command before

---

### Post by sendblink23 on 2008-08-08
i still need the help  :P, sure don't want it there forever LOL

---

### Post by Tim Sharitt on 2008-08-08
> **damoxc said:**
> 
```
sudo rm -r "~/Desktop/Adobe Photoshop Pro CS2 v9.0 Full ISO + WORKING Keygen"
```

This should be 
```
sudo rm -r ~/Desktop/"Adobe Photoshop Pro CS2 v9.0 Full ISO + WORKING Keygen"
```

with quotes only around the file name.

---

### Post by sendblink23 on 2008-08-08
sure i'll give it a try

---

### Post by sendblink23 on 2008-08-08
> **Tim Sharitt said:**
> This should be 
```
sudo rm -r ~/Desktop/"Adobe Photoshop Pro CS2 v9.0 Full ISO + WORKING Keygen"
```

with quotes only around the file name.


That definately got it to work THNX

---

