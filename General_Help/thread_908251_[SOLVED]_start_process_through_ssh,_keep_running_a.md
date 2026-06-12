---
title: "[SOLVED] start process through ssh, keep running after exit"
date: 2008-09-02
forum: General Help
---

### Post by Xiong Chiamiov on 2008-09-02
I've just started using rtorrent on my fileserver, which is fantastic, but I'd like to keep it running after I exit ssh (I don't want to keep my computer on all the time).  I also need to be able to see it when logged into ssh.

---

### Post by Vivaldi Gloria on 2008-09-02
The best way is to start a screen session:

```
screen
```

then do whatever you want. Then detach screen

```
Ctrl+a - d
```

Now you can exit ssh. If you ssh again you can continue the screen session with

```
screen -r
```

Sceen is a very powerful tool that you can also use to manage windows. See:

[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
[http://aperiodic.net/screen/quick_reference](http://aperiodic.net/screen/quick_reference)
[http://www.delorie.com/gnu/docs/screen/screen_toc.html](http://www.delorie.com/gnu/docs/screen/screen_toc.html)

---

