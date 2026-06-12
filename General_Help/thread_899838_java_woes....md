---
title: "java woes..."
date: 2008-08-24
forum: General Help
---

### Post by radtek on 2008-08-24
Screwed up Firefox pretty bad with a series of blunders that I don't have the skill/knowledge to correct.

Tried to install Java plugin via creating a symbolic link:

```
sudo ln -s /usr/java/jre1.6.0_07/plugin/i386/[COLOR="Red"]ns7[/COLOR]/libjavaplugin_oji.so
```

Didn't work so I tried:```
sudo ln -s /usr/java/jre1.6.0_07/plugin/i386/[COLOR="Red"]ns7-gcc29[/COLOR]/libjavaplugin_oji.so
```

In retrospect this was probably a serious mistake. Any web-page with Java crashes FF!

My main question is: [COLOR="Sienna"]How to I remove both symbolic links so I can start over?[/COLOR]


I've also installed Java through apt-get.

---

### Post by txcrackers on 2008-08-25
Change to whatever directory you executed the "ln" commands in. If you do "ls -l" you should see just *one* libjavaplugin_oji.so file. It should look something like this:
```
lrwxrwxrwx 1 root root     39 2007-11-03 12:06 libjavaplugin.so -> /usr/java/jre1.6.0_07/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
```
You can simply *sudo rm -f libjavaplugin.so* and it'll be gone.

After that, I would strongly recommend uninstalling the _07 JRE and using the one provided by the current repository (_06) and installing the *plugin* package to handle Java-enabled websites.

---

### Post by radtek on 2008-08-29
Thanks!

rm removes files and symbolic links? The man page hints at this but why the -f command then?

---

### Post by txcrackers on 2008-08-30
-f is to *force* the deletion (by-passes warning messages, among other things). It's pretty much a very large hammer that's probably not going to be needed in this situation, but wouldn't hurt anyway.

---

