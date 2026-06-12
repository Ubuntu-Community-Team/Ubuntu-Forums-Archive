---
title: "compiling qosmic"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by 1oooop on 2009-05-20
I am not too sure about this error

```
brandon@ubuntu:~/Desktop/qosmic$ make
/usr/bin/uic-qt4 ui/mainwindow.ui -o .ui/ui_mainwindow.h
make: /usr/bin/uic-qt4: Command not found
make: *** [.ui/ui_mainwindow.h] Error 127
brandon@ubuntu:~/Desktop/qosmic$ 
```

can anyone explain this??

I've spent hours trying to configure. Kinda strange there isn't some guide floating around out there. I had to modify a configuration file's paths and set a package.

So, bottom line; is there anyone that can help with this? Anything will help. In fact, if you can give me a repository that has qosmic; I'll probably burst to tears of joy :D.

---

### Post by 1oooop on 2009-05-21
bump

---

### Post by spider_0k on 2009-05-22
The answer is already out there, you need to know the question.

[http://ubuntuforums.org/showthread.php?t=391342](http://ubuntuforums.org/showthread.php?t=391342)

Type uic-qt4 at the command line.

sudo aptitude install libqt4-dev

---

