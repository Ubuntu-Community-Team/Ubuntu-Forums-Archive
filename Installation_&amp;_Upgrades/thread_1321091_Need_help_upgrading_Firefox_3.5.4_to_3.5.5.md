---
title: "Need help upgrading Firefox 3.5.4 to 3.5.5"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by jwnorbury on 2009-11-09
Hey. I'm using 9.10 on my laptop and the default browser is Firefox. This is fine, but I do not know how to upgrade from 3.5.4 to 3.5.5.

I have download the file provided from the website which is "firefox-3.5.5.tar.bz2" However I do not know how to use these file.

Can someone please guide me through installing Firefox 3.5.5. (I am not to good with the command line so could you tell me what I need to enter, not just telling me to do things without explaining.)

Thanks very much!

(Also if anyone knows of a good place to get better at using the command line please say, I assume it will just be with practice and experience)

---

### Post by winotree on 2009-11-09
> (Also if anyone knows of a good place to get better at using the command line please say, I assume it will just be with practice and experience)                                                       Saw this [http://www.stat.tamu.edu/~dahl/teaching/605/1.21/shell-tutorial/html/index.html]("http://www.stat.tamu.edu/%7Edahl/teaching/605/1.21/shell-tutorial/html/index.html") just last night while reading these forum -- think it'll work??

---

### Post by witeshark17 on 2009-11-09
If you use ubuntuzilla, this is the command. It's a reinstall, but the update command appears not to work, and this is just as easy really. No sudo  !!! You will be prompted later as the installation nears completion.

```
ubuntuzilla.py -a install -p firefox
```

More [ Terminal commands]("http://ss64.com/bash/")

---

### Post by wojox on 2009-11-09
Open a terminal and go to your home directory or where ever you downloaded it.

```
tar xjf firefox-*.tar.bz2
```

```
sudo mv firefox /usr/share/
```

---

### Post by karatedog on 2009-11-10
make sure you don't start the newer Firefox while the older version is open. It will just open a new window with the older version.

---

### Post by LarryMi on 2009-11-11
It's best to wait for the update manager to upgrade to 3.5.5.  It usually takes a few days to appear; however, I don't know what is taking so long this time.  This upgrade was [announced on 11/5]("http://www.mozilla.com/en-US/firefox/3.5.5/releasenotes/").

---

