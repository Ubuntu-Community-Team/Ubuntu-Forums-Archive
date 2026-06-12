---
title: "Java did not install correctly?"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by Evil Ninja on 2008-12-23
So I just installed Java from the Add/Remove Program menu and it does not seem to be working. I've been going to the [this page]("http://www.runescape.com/game.ws?m=0&j=1") to see if it is working, but I still get the message "It seems like Java is not installed on your computer. Blah blah blah."

Ideas?

---

### Post by 2hot6ft2 on 2008-12-23
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by taurus on 2008-12-23
When you install java, there would be a window asking you to accept the license from Sun.  If you don't accept that, it will not be installed.  So what happens when you run this command from a terminal?

```

sudo apt-get update

```

---

### Post by Evil Ninja on 2008-12-23
> **2hot6ft2 said:**
> [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Thanks. :) That fixed it all up.

> **taurus said:**
> When you install java, there would be a window asking you to accept the license from Sun.  If you don't accept that, it will not be installed.  So what happens when you run this command from a terminal?

```

sudo apt-get update

```

I did get the license and accepted it.

---

