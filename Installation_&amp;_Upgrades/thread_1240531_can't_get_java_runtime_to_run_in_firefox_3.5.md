---
title: "can't get java runtime to run in firefox 3.5"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-08-14
I used ubuntuzilla to update to the latest firefox, and it even found all my plugins.  However, Java refuses to work.  I have manually placed the libnpjp2.so file in /opt/firefox/plugins as per the instructions I found on the about: plugins page, but my browser still does not detect the plugin at all.  I'd really appreciate a suggestion, I've been looking all over the place and I have no more ideas.

---

### Post by gradinaruvasile on 2009-08-14
The file u need is 
/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

Link it in /usr/lib/firefox/plugins/ folder with

```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
```

---

### Post by v1nsai on 2009-08-15
I don't have the i386 folder in /usr/lib/jvm/java-6-sun/jre/plugin.

I have the sun-java6-jre and sun-java6-jdk, I think those are the only ones though.

My plugins are stored in /opt/firefox/plugins, it's not the repo version its a mozilla binary that I installed using ubuntuzilla.  Actually, the plugins folder is a symlink to /usr/lib/xulrunner-addons/plugins .  I know xulrunner has to do with XUL and XPCOM but I don't know what it actually does.

---

### Post by v1nsai on 2009-08-23
still can't get it to run, I know the repo version of firefox works perfectly fine but it doesn't allow for private browsing on demand which is really nice to have for banking transactions and whatnot.  Makes me feel a lot better about doing business on the web.

Plus, this doesn't make any damn sense and I like figuring this stuff out.  I'm just out of ideas, I've tried everything I can find.

---

