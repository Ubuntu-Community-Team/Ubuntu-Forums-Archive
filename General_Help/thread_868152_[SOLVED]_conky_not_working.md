---
title: "[SOLVED] conky not working"
date: 2008-07-23
forum: General Help
---

### Post by jimi_hendrix on 2008-07-23
hi

i installed conky yet i cannot find it in any of the catagories in my applications

any advise?

---

### Post by easybake on 2008-07-23
> **jimi_hendrix said:**
> hi

i installed conky yet i cannot find it in any of the catagories in my applications

any advise?

Just type Conky into terminal. 

If you just downloaded it you will probably want to copy someones conkyrc from [Here]("http://ubuntuforums.org/showthread.php?t=281865") 

In terminal type ```
gedit .conkyrc 
``` To edit the default conkyrc.

---

### Post by jimi_hendrix on 2008-07-23
```
Conky: missing text block in configuration; exiting

```

i get that

---

### Post by easybake on 2008-07-23
> **jimi_hendrix said:**
> ```
Conky: missing text block in configuration; exiting

```

i get that

You're probably just missing the conkyrc file and it doesn't have any info to read from. Pick one up from that forum link I provided. Then in terminal type ```
gedit .conkyrc
``` paste the conkyrc you found. Then type in terminal```
conky
``` it sould work.

If it still doesn't work, re-install it in terminal.
```

sudo apt-get remove --purge conky
sudo apt-get install conky

```

---

### Post by jimi_hendrix on 2008-07-23
ok

---

