---
title: "Running X apps in separate virtual consoles"
date: 2008-11-09
forum: General Help
---

### Post by rocketman768 on 2008-11-09
Is it possible to run a single X application in a virtual terminal (like ctrl-alt-f2)? If not, is it possible to start up gnome in two or more virtual consoles at once (instead of only ctrl-alt-f7)? Thank you!

---

### Post by rocketman768 on 2008-11-09
bump

---

### Post by bodhi.zazen on 2008-11-09
You can either :

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

OR 

[http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

---

### Post by rocketman768 on 2008-11-09
So, by reading your script and experimenting, I found out that this will put gmplayer on ctrl-alt-f8. I executed this from ctrl-alt-f2.

```

xinit gmplayer -- :1

```

---

### Post by bodhi.zazen on 2008-11-09
Awesome, I hope you learned a little as well. IMO what I call "Virtual X" sessions are underutilized.

---

