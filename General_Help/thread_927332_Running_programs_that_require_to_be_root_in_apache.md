---
title: "Running programs that require to be root in apache2"
date: 2008-09-22
forum: General Help
---

### Post by hurdevan on 2008-09-22
I have a apache server that needs to run a program as root.............
The program needs to access the parerall port witch requires root privileges.
Is there away of making the program automaticly run as root? s

Thanks

---

### Post by hurdevan on 2008-09-22
I need anyway to make my apache server run a file as root.

---

### Post by ashmew2 on 2008-09-23
What command do u use to run the program ? Have you tried using sudo just before the command ? as in :
```

sudo <command here>
```

?

---

### Post by hurdevan on 2008-09-23
What I want is....when I visit my website it will run a cgi file on my server. any commands in the cgi files will not run as root so.......... I need my program as root without entering a password.


Cheers

---

