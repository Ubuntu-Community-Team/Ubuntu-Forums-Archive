---
title: "Why am i still usung firefox 3 Beta?"
date: 2008-11-27
forum: General Help
---

### Post by notsteve on 2008-11-27
I recently started using ubuntu again, and i'm just curious to why i seem to be unable to download firefox 3 from the package manager?

---

### Post by gjoellee on 2008-11-27
Firefox comes with the normal updates for your system, update it :)

Code if you want that...just copy and paste in to the Terminal
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by notsteve on 2008-11-27
well thats the thing, it just won't update. i also jsut typed in that code, and no updates were installed, which is kind of odd because it's been over 6 months since i used Ubuntu.
(I'm still running beta 5)

---

### Post by philinux on 2008-11-27
Check your software sources. Make sure backports are enabled under updates.

---

### Post by PatrickVogeli on 2008-11-27
You could try switching mirrors, use the global ones. Instead of XX.archive.. use archive...

---

### Post by notsteve on 2008-11-27
> **philinux said:**
> Check your software sources. Make sure backports are enabled under updates.

Ya think this might have work, I'm updating now as we speak

---

