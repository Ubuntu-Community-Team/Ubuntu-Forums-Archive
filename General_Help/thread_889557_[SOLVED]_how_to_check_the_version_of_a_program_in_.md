---
title: "[SOLVED] how to check the version of a program in the repository"
date: 2008-08-14
forum: General Help
---

### Post by Spalatum on 2008-08-14
Hello.

Is there a command I could use in the terminal to check which version of the application is available in the repositories? :confused:

---

### Post by kpkeerthi on 2008-08-14
```
aptitude show <package-name>
```

---

### Post by decoherence on 2008-08-14
```
dpkg-query --show firefox
```

---

### Post by sayakb on 2008-08-14
```
dpkg -l packagename
```
Though this applies for installed packages only.

---

### Post by Spalatum on 2008-08-14
Thanks for the information. Cheers :)

---

### Post by decoherence on 2008-08-14
> **LinuxIsInnovation said:**
> Though this applies for installed packages only.

Good point -- the same for the command i posted.

The above aptitude command will search the complete database, alternately
```

apt-cache showpkg firefox
```

will do the same

---

