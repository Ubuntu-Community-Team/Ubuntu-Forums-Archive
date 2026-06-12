---
title: "Terminal Gibrish"
date: 2008-11-29
forum: General Help
---

### Post by redserpent7 on 2008-11-29
Hi I'm having a problem with my ubuntu terminal. Whenever I open the terminal I get some weird gibberish text. The terminal is working fine and all but this is annoying me. As they say a picture can replace a thousand words. 

[IMG]http://i149.photobucket.com/albums/s55/redserpent7/Zaid.jpg[/IMG] 

Thanks for helping in advance. :)

---

### Post by iponeverything on 2008-11-29
This will fix your problem:

```
sudo mv /etc/bash_completion.d/inkscape /root
```

what that will do is move that bash completion to root's home directory, in case you want to look at it later or put it back into place.

---

