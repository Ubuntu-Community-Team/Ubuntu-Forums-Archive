---
title: "Maverick and tx2100ed"
date: 2011-01-28
forum: Hardware
---

### Post by waspbr on 2011-01-28
Hello everyone, I have been trying to install maverick on a tx2000 lappy and I have been hitting a bump, the live CD seems to boot into a blankscreen (backlight on but blank), I can hear the login sounds and everything. 

I then tried the alternate CD, needless to say it worked, but when I boot up I still get the same blank screen with the back light on and the rest blank. 

I also tried the linux mint CD, also on compatibility mode. Same issue. 

any thoughts?

---

### Post by Favux on 2011-01-28
This thread may help:  [http://ubuntuforums.org/showthread.php?t=1654787](http://ubuntuforums.org/showthread.php?t=1654787)

---

### Post by gordintoronto on 2011-01-28
Look for bootoptions in the Community Documentation.

---

### Post by waspbr on 2011-01-29
hmm, thanks for the link but it's not quite that problem. I thought that maybe this was a kernel related problem so I tried to install lucid, actually linux mint 9.  When I tried to run it in compatibility mode it game me a clue, something along the lines of: 

```
vesa kernel modesetting driver in use refusing to load
```

After a quick search with that and adding "livecd" I got a few hits. 

As it turns out the problem is 'solved' by adding "nomodeset" to the bootline.  I don't have a lot of time to look into why this is going on but for now this patches things up. Thanks for the help anyway.

---

