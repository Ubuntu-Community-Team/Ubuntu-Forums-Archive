---
title: "Java Help"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by red_spyder on 2009-09-27
Hello, I've installed java on earlier ubuntu OS's before, but I can't quite tell what is wrong now.
I've installed java on my current operating system (9.04) so when I type
```

java -version

```
it gives me 1.6.0_0
And i have java enabled under firefox preferences, but I still can't seem to run it on programs online (i.e. Runescape)
Has anyone had this problem?

- Thanks

---

### Post by stlsaint on 2009-09-27
have you tried installing via synap package manager?

---

### Post by red_spyder on 2009-09-27
Yes, I downloaded the .deb package from the java website and installed it that way

---

### Post by tuxxy on 2009-09-27
Java is included with the package ubuntu-restricted-extras along with Flash, codecs etc its a gereat package to install on a clean system :D

```
sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by red_spyder on 2009-09-27
I'm still getting an error for Java. It tells me that it seems like Java is not installed on my computer.

---

### Post by red_spyder on 2009-09-27
Actaully it was NOT a .deb file, it was a .bin file.

---

### Post by grturner on 2009-09-27
sometimes you have to actually tell ubuntu what java to use, since typically you have more than one type of java installed.

see [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by red_spyder on 2009-09-27
I've followed those steps before, that was what I used after I installed the .bin file.

---

### Post by grturner on 2009-09-27
then i would look for command line arguments to pass a variable to the runescape client pointing to the directory of the java bin folder

---

### Post by red_spyder on 2009-09-27
Well I will keep tinkering with it. Thank You all

---

