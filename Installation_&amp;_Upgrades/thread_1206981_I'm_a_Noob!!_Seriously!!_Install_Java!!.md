---
title: "I'm a Noob!! Seriously!! Install Java!!"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by gohawk08 on 2009-07-07
ok. i've been seraching and trying things for like 3 hours now and i just can't figure out how to get firefox to work with java...
i'm trying to get runescape(the only thing i use java for) to work!

I downloaded both the .bin and the rpm.bin files directly from the java website...

now does anyone have really noobish and very meticulous instructions as to what the heck i have to do to get runescape working???


when i'ev been looking at other forums, people have other people doing sooo many different terminal codes....
I'm Going mad!!!

so basically i just need beginners instructions on how to get java installed....

It would be GREATLY appreciated!!!

---

### Post by sedawk on 2009-07-07
In my user directory I have a directory .mozilla/plugins and it
contains this:

libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun-1.6.0.10/jre/plugin/i386/ns7/libjavaplugin_oji.so

I do not know where you installed java, but find your file
libjavaplugin_oji.so. Run a terminal and do this so it points
to your libjavaplugin_oji.so:
```

cd .mozilla/plugins
ln -sfn /usr/lib/jvm/java-6-sun-1.6.0.10/jre/plugin/i386/ns7/libjavaplugin_oji.so .

```

Now if you restart firefox java should work. Try the browser test from sun:
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

---

### Post by pricetech on 2009-07-07
As far as installing Java, here's the easiest method I know of, and frankly the method I use.

Applications - Add / Remove   Where it says  Show  change that to All Available Applications.  Type  Java  in the search box.  Install Java that way.

As far as making runescape work, I'm afraid I'm no help there.  I'm not a gamer.

But hey, maybe it'll "just work" once Java is intalled.

---

### Post by sdlynx on 2009-07-07
> **pricetech said:**
> As far as installing Java, here's the easiest method I know of, and frankly the method I use.

Applications - Add / Remove   Where it says  Show  change that to All Available Applications.  Type  Java  in the search box.  Install Java that way.

As far as making runescape work, I'm afraid I'm no help there.  I'm not a gamer.

But hey, maybe it'll "just work" once Java is intalled.

Runescape is built in java.  If you can get java to work, Runescape'll work.

try ```
sudo apt-get install sun-java6-jre
```

---

### Post by gohawk08 on 2009-07-07
> **sedawk said:**
> In my user directory I have a directory .mozilla/plugins and it
contains this:

libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun-1.6.0.10/jre/plugin/i386/ns7/libjavaplugin_oji.so

I do not know where you installed java, but find your file
libjavaplugin_oji.so. Run a terminal and do this so it points
to your libjavaplugin_oji.so:
```

cd .mozilla/plugins
ln -sfn /usr/lib/jvm/java-6-sun-1.6.0.10/jre/plugin/i386/ns7/libjavaplugin_oji.so .

```Now if you restart firefox java should work. Try the browser test from sun:
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

k. i can do most of that...

I've used the file browser to eventually find the libjavaplugin_oji.so...
it is located in File System/opt/jre1.6.0_14/plugin/i386/ns7-gvv29

so what do i do exacly now??
i don't have java in the mozilla/plugins directory...
it's just in my File System.. how do you 'cd' to your file system???

---

### Post by gohawk08 on 2009-07-07
by the way.. Thanks for all the replies people... do i sound dumb??

I have been a windows user for all my life...

---

### Post by sdlynx on 2009-07-07
```
cd /
``` will get you to the file system in a terminal if thats what you want

and don't worry you just need to get used to linux commands and you'll be fine

---

### Post by gohawk08 on 2009-07-07
> **sdlynx said:**
> ```
cd /
``` will get you to the file system in a terminal if thats what you want

and don't worry you just need to get used to linux commands and you'll be fine


k.. so can i double check with you just to be sure...
cause when i go to 'cd' where the mozilla/plugins 'directory' is, ( first i go to cd /usr/lib/, then i try to go to cd /mozilla and my target is cd /plugins.. right?
but when i click enter the terminal says 'no such file or directory'
 but i know its there!! 
i can see it in my file system!!

do you know why that is??
Thx

---

### Post by Separ on 2009-07-08
```
sudo apt-get install sun-java6-bin sun-java6-jre
```

Try that, that's always how I've done it in the past.

---

### Post by steveneddy on 2009-07-08
I prefer icedtea:

```
sudo apt-get install icedtea-gcjwebplugin
```

Runs great from browser to browser and on FF 3.0 and 3.5

Been running iced tea since Gutsy

---

### Post by Sef on 2009-07-08
> ok. i've been seraching and trying things for like 3 hours now and i just can't figure out how to get firefox to work with java...
i'm trying to get runescape(the only thing i use java for) to work!Easy way to install Java in 5 minutes:

Applications > Add/Remove > Show: All Available Applications > Search: Sun Java 6 > Tic both boxes > click apply changes > click apply > close

---

### Post by gohawk08 on 2009-07-08
> **Separ said:**
> ```
sudo apt-get install sun-java6-bin sun-java6-jre
```Try that, that's always how I've done it in the past.

ok i copied and ran that code... so now what?

don't i have to do something? cause java still won't work.. 
isn't there something about getting firefox to recognized it??? 
thanks

---

