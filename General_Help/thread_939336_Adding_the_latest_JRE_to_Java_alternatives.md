---
title: "Adding the latest JRE to Java alternatives"
date: 2008-10-05
forum: General Help
---

### Post by TheFuzzy0ne on 2008-10-05
Hi everyone. I have a relatively simple question.

I've downloaded the latest Java, extracted it, and moved it to /usr/lib/jvm/ but I've no idea how to get that in to my Java alternatives so I it's available via update-java-alternatives.

I'd like to avoid manually updating each Java alternative if possible. Any help would be appreciated.

Many thanks in advance. 

Daz.

---

### Post by drubin on 2008-10-05
Take a look at the java link in my sig. :)

**Edit:**
Rather install via  package management then by downloading unless you "need" the latest version

---

### Post by TheFuzzy0ne on 2008-10-06
> **rubinboy said:**
> Take a look at the java link in my sig. :)

**Edit:**
Rather install via  package management then by downloading unless you "need" the latest version

I do "need" the latest version. I play a game called Runescape, and the latest version fixes a bug that allows me to use Open GL with the Java applet, which means the game will no longer crash randomly like it usually does.

Thanks for your reply.

---

### Post by drubin on 2008-10-06
> **TheFuzzy0ne said:**
> I do "need" the latest version. I play a game called Runescape, and the latest version fixes a bug that allows me to use Open GL with the Java applet, which means the game will no longer crash randomly like it usually does.

Thanks for your reply.

Good reason for wanting the latest version :P 

Here try this
```
 sudo  update-alternatives --config java
```

Or follow this tutorial 
[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

---

### Post by TheFuzzy0ne on 2008-10-06
Fantastic! The guide was exactly what I was looking for, thanks.

Just out of interest, how did you find it? I've spent hours googling, and never came across it. The problem was that it wasn't showing when I ran:
```

update-java-alternatives -l

```

I ended up renaming /usr/lib/jvm/java-6-sun-1.6.0.06 to /usr/lib/java-6-sun-1.6.0.06.old, and creating a symlink to the new installation named java-6-sun-1.6.0.06.

It's some ugly hackery, and I know it's not recommended to mess with system installed packages, but I was desperate. Thanks again for the assistance!

---

### Post by drubin on 2008-10-06
Pleasure just remember to mark the thread as solved. (Under thread tools above your first post).

Any thing to help out a person wanting to use java :)

---

### Post by ric.hayman on 2009-12-10
> **drubin said:**
> Good reason for wanting the latest version :P 

Here try this
```
 sudo  update-alternatives --config java
```Or follow this tutorial 
[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

Well it's sometime later, but it was just as helpful ... thanks!

---

