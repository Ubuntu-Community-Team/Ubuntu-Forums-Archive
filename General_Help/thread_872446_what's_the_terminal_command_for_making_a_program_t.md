---
title: "what's the terminal command for making a program the default?"
date: 2008-07-28
forum: General Help
---

### Post by adn258 on 2008-07-28
I remember seeing it some place with java because it wasn't working in firefox.  Anyway there was a command that made java the default for reading java applications online or whatever.  It looks like a hand command something like sudo application-set --application name or something like that anyway does anyone know what it is?

---

### Post by y-lee on 2008-07-28
for java you mean

```
sudo update-alternatives --config java
```

see [Java]("https://help.ubuntu.com/community/Java#Choosing%20the%20default%20Java%20to%20use")

I also have used 

```
sudo update-alternatives --config x-www-browser
```

See [Using the Debian alternatives system]("http://www.debian-administration.org/articles/91")

or 
```
man update-alternatives
```

---

