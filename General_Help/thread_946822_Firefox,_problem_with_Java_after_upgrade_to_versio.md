---
title: "Firefox, problem with Java after upgrade to version 1.6.0_07"
date: 2008-10-13
forum: General Help
---

### Post by mpolito1969 on 2008-10-13
Hello,

the upload manager told me to install the new java version, now I have

```

root@laptop:/etc# java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Server VM (build 10.0-b23, mixed mode)

```

Before this upgrade everything was working correctly now when I go to

[http://meter.mclink.it/applet.html](http://meter.mclink.it/applet.html)

I'm redirected to this:

[http://meter.mclink.it/nojava.html](http://meter.mclink.it/nojava.html)

which says JAVA Runtime Environment is not installed or not enabled. My /etc/jvm file is:


```
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

```

Can you helping understanding what went wrong with this upgrade?

These are some information about Java directories:

```
root@laptop:/etc# ls -alF /usr/lib/jvm/java-6-sun
lrwxrwxrwx 1 root root 19 2008-10-13 22:23 /usr/lib/jvm/java-6-sun -> java-6-sun-1.6.0.07/

```

```
root@laptop:/etc# ls -alF /usr/lib/jvm/java-6-sun-1.6.0.07/
total 24
drwxr-xr-x 6 root root 4096 2008-10-13 22:23 ./
drwxr-xr-x 3 root root 4096 2008-10-13 22:23 ../
drwxr-xr-x 3 root root 4096 2008-10-13 22:23 bin/
drwxr-xr-x 2 root root 4096 2008-08-07 17:24 ext/
drwxr-xr-x 7 root root 4096 2008-10-13 22:23 jre/
drwxr-xr-x 4 root root 4096 2008-10-13 22:23 man/
lrwxrwxrwx 1 root root   10 2008-10-13 22:23 .systemPrefs -> /etc/.java/

```

```
root@laptop:/etc# ls -alF /etc/.java
total 20
drwxr-xr-x   3 root root  4096 2008-09-21 18:19 ./
drwxr-xr-x 126 root root 12288 2008-10-13 22:52 ../
drwxr-xr-x   2 root root  4096 2008-09-21 18:19 .systemPrefs/

```

Ciao,
Max

---

### Post by geirha on 2008-10-13
What does about:plugins in Firefox say?

Also, try running ```
sudo update-java-alternatives --set java-6-sun
``` to make sure all the symlinks are set ok.

---

### Post by mpolito1969 on 2008-10-14
> **geirha said:**
> What does about:plugins in Firefox say?

Also, try running ```
sudo update-java-alternatives --set java-6-sun
``` to make sure all the symlinks are set ok.

Yesterday didn't work, now it's working, I don't know why. Probably a reboot was needed...

Thanks.

Ciao,
Max

---

### Post by geirha on 2008-10-14
Ah, you probably just needed to restart firefox. It's a common gotcha to only close the main window when restarting firefox, leaving another window, like the download window open.

---

