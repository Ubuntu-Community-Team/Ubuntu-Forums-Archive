---
title: "Flock Doesn't Work"
date: 2008-10-07
forum: General Help
---

### Post by Unanimated on 2008-10-07
I've wanted to try Flock again recently, so I downloaded it. It doesn't work. This is what the Terminal says:
```
sam@sam-desktop:~$ cd Applications/flock
sam@sam-desktop:~/Applications/flock$ chmod +x flock
sam@sam-desktop:~/Applications/flock$ ./flock
./flock-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
sam@sam-desktop:~/Applications/flock$ ./run-mozilla
bash: ./run-mozilla: No such file or directory
sam@sam-desktop:~/Applications/flock$ ./run-mozilla.sh

run-mozilla.sh: Cannot execute .

sam@sam-desktop:~/Applications/flock$ 

```
/Applications is a folder I made myself to organize things that I download instead of putting them in Documents. Anyway, any help?

---

### Post by Soupcan on 2008-10-07
Have you tried installing it with a .deb? I have version 1.2.4, which I got [here.]("http://www.getdeb.net/search.php?keywords=flock")
I hope this is helpful.

---

### Post by Unanimated on 2008-10-08
Not only did you help me with my problem, you also gave me a link to a site that I've wanted forever. Thanks a lot!

---

