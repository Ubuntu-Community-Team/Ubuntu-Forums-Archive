---
title: "Customize .desktop file to launch using optirun"
date: 2013-03-17
forum: Hardware
---

### Post by zer010 on 2013-03-17
I recently got this laptop and found out that I indeed had the infamous Optimus chip.  I installed Bumblebee and all seems to work pretty good.  Now I want to be able to launch games using the optirun withoutusing the terminal. I figure the .desktop file could be changed to do this, but I'm not exactly sure how I need to edit the .desktop file to this. 
I'm sure this won't work...or will it?
```
Exec=optirun ~/Games/1.1.0.4/./assaultcube.sh

```
I've found a couple of answers that point to the "fact" that it's possible, but no information on exactly how. Then it goes on to suggest using alacarte, which I don't want to install.  One such answer was [this one]("http://askubuntu.com/questions/166144/run-a-program-with-optirun-by-default-bumblebee").

Any help is much appreciated.  Hopefully it will also help others as well.

---

### Post by zer010 on 2013-03-17
Well, I guess it is just that simple. I'm not exactly sure it's really using the optirun command, but AC does start up and run like it's supposed to.

```
Exec=optirun /home/zer0/Games/1.1.0.4/assaultcube.sh
```

I guess I can mark this thread as "SOLVED". Isn't it nice when you answer your own question?:P

---

