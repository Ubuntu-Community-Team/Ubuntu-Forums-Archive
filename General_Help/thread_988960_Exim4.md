---
title: "Exim4"
date: 2008-11-21
forum: General Help
---

### Post by pan69 on 2008-11-21
When I run this command

```
sudo aptitude install libapache2-svn subversion-tools
```

I get exim4 shoved down my throat. Why's that? What do these packages have to do with exim4????

---

### Post by adult swim on 2008-11-21
[http://ubuntuforums.org/archive/index.php/t-82468.html](http://ubuntuforums.org/archive/index.php/t-82468.html)

---

### Post by pan69 on 2008-11-21
That's completely ridiculous. Thanks anyway!

Oh. This is how to get rid of bloody exim4:
```

sudo apt-get remove exim4 exim4-base exim4-config exim4-daemon-light 

```

---

