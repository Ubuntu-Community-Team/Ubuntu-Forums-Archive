---
title: "Java plugin not working with Firefox 3 - Jaunty"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by paulcressbrook on 2009-05-19
I upgraded recently to Jaunty and then found the Java plugin failed to work with Firefox 3. I have Java 6 installed with Jaunty, so was surprised. 
Looking in the .mozilla/plugins directory I found I have a link called libjavaplugin.so which pointed to the correct place - so again it was surprising that the plugin failed to work.
After going all round the houses I finally discovered by using about:config in Firefox, that Firefox 3 expects the java plugin to have the name javaplugin.so - not libjavaplugin.so
Changing the name with the command:

mv libjavaplugin.so javaplugin.so

- in the directory /home/<username>/.mozilla/plugins solved the problem. This is probably a general problem with Ubuntu and Xubuntu Jaunty as well as Kubuntu

---

### Post by kajman on 2009-05-19
Thanks man!

It worked for me and I'm very happy you wrote this post :)
It's been annoying for a while for me.

---

### Post by Der Atlas on 2009-05-23
So Java plugins seem not be be working ... sites think I don't have Java installed, though I do.

I'm running Kubuntu Jaunty and I don't have this directory.  .mozilla/ is empty except for subdirectories 'firefox' and 'extensions', and about:config doesn't give any useful pointers here.

Is my system just configured differenly or have files been lost ?  In any case, what should I do ?

Thanks!

---

### Post by jamesstansell on 2009-05-25
Does about:plugins show a java plugin?  If so, which sites are not recognizing it?

---

### Post by kajman on 2009-05-25
Here's what I've done:

I've downloaded a binary installer from java.com:

[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

(I've chosen the second link from top, "Linux (self-extracting file)")

Then I've moved the binary file to (it doesn't matter much where you unpack it) /usr/local/java and unpacked it.

To do it, you should probably do this in terminal:

```

cd /usr/local/java
sudo chmod +x jre-6u13-linux-i586.bin
sudo ./jre-6u13-linux-i586.bin

```

Then proceed with installation.

After that you'll see a new directory /usr/local/java/jre.6.0_13,now do the following:
```

cd .mozilla/plugins
sudo ln -s /usr/local/java/jre1.6.0_13/plugin/i386/ns7/libjavaplugin_oji.so
mv libjavaplugin_oji.so javaplugin.so

```

And that should do it, just restart firefox and java will work.

---

### Post by jamesstansell on 2009-05-27
Just curious.  Is that last step (the mv) required?  I haven't used the oji version of the plugin for a while, but when I did I don't think I ever needed to rename the symbolic link.

---

### Post by kajman on 2009-05-28
Well, as paulcressbrook said it is required in 9.04.

---

### Post by jyxll on 2009-08-13
It was not necessary for me to change the name of libjavaplugin_oji.so.

---

### Post by siecoban on 2009-09-25
I have no plugins folder under .mozilla on a fresh Jaunty install.  How did you get it there?

---

### Post by nortexoid on 2010-02-22
This thread looks dead. But I'm using Kubuntu Karmic and I don't have the .mozilla/plugins folder either. And java doesn't work, though it does in Chrome. What's up with that? About:plugins doesn't show java, but it does show a bunch of other plugins (e.g. xine). So where's my plugins folder?

---

