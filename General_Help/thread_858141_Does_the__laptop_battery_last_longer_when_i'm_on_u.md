---
title: "Does the  laptop battery last longer when i'm on ubuntu than when i'm on vista?"
date: 2008-07-13
forum: General Help
---

### Post by g2bandrew on 2008-07-13
I thought it would cause it shouldn't use as much power since it's going quicker but it doesn't seem to be too much if a difference. So, does the laptop battery last longer on ubuntu than it would if i was on vista (ultimate)?

---

### Post by cyclobs on 2008-07-13
well it depends on many factors.

my 'guess' would be yes totally due to the fact that your laptop would be using a hell of a lot less resorces to run the system (unlike in vista) (less cpu / hard drive writes / GPU usage etc)

but thats my guess.

you could set up a little experiment and test both systems to see

---

### Post by sdennie on 2008-07-13
Vista will probably have better battery life by default because it comes tuned by your vendor to extend the battery life.  Fortunately, it's possible to tune Ubuntu to save a lot more power for some laptops.  First, you'll need powertop:

```

sudo apt-get install powertop

```

To run it:

```

sudo powertop

```

Then, there are few places you can look to help setup your power savings (not all of these will be valid for your laptop but, it gives you an idea of what you can do):

[http://www.lesswatts.org/](http://www.lesswatts.org/)
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)
[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by Verbeck on 2010-11-15
> **Laptop Battery said:**
> snip
nice user name ;)

---

### Post by Goldfissh on 2010-11-15
I'd have thought that the battery life would be a little longer, due to less running in the background and the system as a whole running more efficiently.

---

### Post by mister_playboy on 2010-11-15
> **Verbeck said:**
> nice user name ;)

Actually, I think "Thread Necromancer" would be more appropriate. :lolflag: From what I have learned of the board staff here, I'm sure they'll agree.

---

### Post by Iowan on 2010-11-22
How about "Spam Banned"?

Closed.

---

