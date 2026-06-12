---
title: "Update Manager hanges on latest updates."
date: 2008-08-05
forum: General Help
---

### Post by nelsonm on 2008-08-05
Hi all,

I have two 8.04 systems and both cannot install the latest updates from Update Manager.

Update Manager just sits there spinning its wheels for hours and I can't close it. I have to reboot to kill the update manager.

Is the problem on my end?

---

### Post by ibuclaw on 2008-08-05
Have you tried upgrading your system in the console, to check for any error or required user input?

```
sudo apt-get update
sudo apt-get upgrade

```

Regards
Iain

---

### Post by nelsonm on 2008-08-05
That did the trick!

I wonder whats up with Update Manager?

Anyway, thanks.

---

### Post by nelsonm on 2008-08-05
The Add/Remove panel does not work either.

Is the program under Add/Remove and Update manager broken?

What can I do?

---

