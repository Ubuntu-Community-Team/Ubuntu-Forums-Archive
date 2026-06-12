---
title: "[SOLVED] Java in Flock (help me)"
date: 2008-07-25
forum: General Help
---

### Post by Stargazer989 on 2008-07-25
i just installed Flock (a web browser) and i tried to play Java on it and it says i have to manually install...

been following: [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80) as a guide

i need help with the *su* command

i'm getting:
*su: Authentication failure*

---

### Post by sandb on 2008-07-25
Hi Stargazer989

You can solve this by

1) make sure java works in firefox

2) linking flock (which is based on mozilla/firefox) to the plugins installed for firefox by doing the following (i'm assuming you installed flock in ~/flock):

```

cd ~/flock
mv plugins plugins-original
ln -s /usr/lib/firefox/plugins plugins

```

This will make all plugins installed in firefox available in flock the next time you start flock.

(Tested this on Gutsy Gibbon)

---

### Post by Stargazer989 on 2008-07-25
well actually i'm on 8.04 and i fixed it with:
```

sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/flock/plugins

```

after using 
```

 locate *java*.so

```
works fine now... though i'd love to have MidBrowser back (only web browser that i really like to use java applets on)

---

