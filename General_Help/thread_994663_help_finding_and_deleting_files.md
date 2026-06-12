---
title: "help finding and deleting files"
date: 2008-11-27
forum: General Help
---

### Post by newojade on 2008-11-27
I am a brand new ubuntu user and in trying to figure out i've downloaded useless stuff that I want to delete but I don't know how to or where to find it.  I know this is a pretty vague question but if anyone could shed some possible light it would be greatly appreciated.

For example, I did some terminal command to try and dL AIM.  It told me that it was using so and so amount of space and then it stopped saying it was deferring to me i think. I found out about pidgin immediately after and I am content with that but I want to delete whatever was installed.

---

### Post by HereInOz on 2008-11-27
First a question to your question.  Did you download AIM as a .tar.gz file, or did you download it as a .deb file, or did you use apt-get / Synaptic Package Manager.

The reason I ask this is that the uninstall process is different depending on the install method.

---

### Post by Tamlynmac on 2008-11-27
You may wish to read this: I hope it helps.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by newojade on 2008-11-27
I used an apt-get

---

### Post by tedius on 2008-11-27
To uninstall a program just type.
```

sudo apt-get remove <program name>

```

---

### Post by newojade on 2008-11-28
Okay I tried > sudo apt-get remove <aim> and it didnt work...

> bash: syntax error near unexpected token 'newline'

---

### Post by YoG%*@ on 2008-11-29
hi, 

> **newojade said:**
> Okay I tried  and it didnt work...


leave out the '<>'s. so in your case, if the program's name that you 
want to remove is 'aim', type:
```
 sudo apt-get remove aim
```hth, 
mux

---

