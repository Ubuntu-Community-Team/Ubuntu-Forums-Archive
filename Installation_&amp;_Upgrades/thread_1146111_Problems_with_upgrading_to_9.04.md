---
title: "Problems with upgrading to 9.04"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2009-05-02
I tried upgrading to 9.04 from 8.10 using the alternate CD.
I get not dialogue for upgrading like [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) suggests.
So i entered the command they have given in case the dialogue doesn't appear. After I entered this command in Konsole the installation proceeds and I am asked if I want to get more updated via internet. I clicked the "no" button and went on. A  little later a box  pops up and says "impossible to find package kde-desktop". 

Now, i've screwed up my PC before so I was terrified of doing the same thing again and quit the installation :(.  What can I do now?

---

### Post by taurus on 2009-05-02
Did you use the Gnome alternate CD to upgrade a Kubuntu machine?

---

### Post by mahela007 on 2009-05-02
I downloaded an iso file called "kubuntu 9.04". I assumed it was KDE because it was kubuntu. The md5sums also match up with the kubuntu alternate version.

---

### Post by taurus on 2009-05-02
Did you add any extra ppa.launchpad.net's repos in /etc/apt/sources.list for your Intrepid?

```
cat /etc/apt/sources.list
```

---

### Post by mahela007 on 2009-05-02
I don't know about  /etc/apt/sources.list but Yes, I did add some repositories  when I installed open office  3.0
Is that what's causing the problem?

---

### Post by taurus on 2009-05-02
It's probably best to comment out those 3rd party repos whenever you do an upgrade from one release to the next.

---

### Post by mahela007 on 2009-05-02
how do I do that? and during the little bit of the installation that went through a message popped up saying some 3rd party repos had been disabled.

---

