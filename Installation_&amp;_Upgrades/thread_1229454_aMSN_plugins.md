---
title: "aMSN plugins"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by blastbar on 2009-08-02
hi just a quick question i've downloaded and installed some plugins for aMSN but i dont know how to activate them any help??? thanks =]

---

### Post by realzippy on 2009-08-02
[http://www.amsn-project.net/wiki/Installing_Plugins_and_Skins](http://www.amsn-project.net/wiki/Installing_Plugins_and_Skins)

"The plugin should appear in the plugins selector dialog. You don't need to restart aMSN. "

---

### Post by blastbar on 2009-08-02
oooooh thank you =]

---

### Post by blastbar on 2009-08-02
sorry for being so daft but i cant find either of these 
 c:\Program Files\Amsn\scripts\Plugins
 c:\Document and Settings\YOUR_USER_NAME\Amsn\scripts\Plugins

where should i look?

---

### Post by SuperSonic4 on 2009-08-02
> **blastbar said:**
> sorry for being so daft but i cant find either of these 
 c:\Program Files\Amsn\scripts\Plugins
 c:\Document and Settings\YOUR_USER_NAME\Amsn\scripts\Plugins

where should i look?

You won't because you're not on windows

See the Linux section beneath windows ;)
You can put them (as full directories) in the following

~/.amsn/plugins

---

### Post by blastbar on 2009-08-02
i knew there was something wrong :p  back to the drawing board =]   thanks for your help

---

### Post by blastbar on 2009-08-02
this is what i see now :s

---

### Post by neu2buntu on 2009-08-02
you are in the wrong directory .. amsn is in your home folder as a hidden directory.... 
goto >places>home>view (at top of window)>and tick show hidden files.  now look for .amsn  (dot amsn)

---

### Post by blastbar on 2009-08-02
thank you =]        this is as far as i have got now

---

### Post by SuperSonic4 on 2009-08-02
Open a terminal (System -> Accessories -> Terminal) and type

```
mkdir -v ~/.amsn/plugins
``` - to create a directory called plugins.

You can then copy and paste your plugin into this folder either using cp via terminal or ctrl+c, ctrl_v

---

### Post by blastbar on 2009-08-02
ahhhhh thank you =]

---

### Post by blastbar on 2009-08-02
hmmmmm it says directory exists???? now my computers hiding frm me :s

---

### Post by SuperSonic4 on 2009-08-02
What is the output of ```
ls -A ~/.amsn
```

---

