---
title: "abaut java (again)"
date: 2008-10-26
forum: General Help
---

### Post by uldo on 2008-10-26
I'm kind of confused, there is so meny threads about this..... i'm running ubuntu 8.04 64bit on intel dual core and i need 100% java support.... so what should i do?? I'm a old times linux user (last time I used it was about 6 years ago), just got pist off (allmost throwed my PC out throught the window) by the windows and returned to linux....... so to which thread I should go or just post it down here..... thx........

---

### Post by jocko on 2008-10-26
For a firefox java plugin, install the package "icedtea-gcjwebplugin", and for other java needs install the package "sun-java6-jre". Or, to make it even easier, install the package "ubuntu-restricted-extras", which brings both of the above packages as well as a bunch of other restricted packages (mp3 support, flash, dvd codec, unrar, microsoft fonts...).
You'll find the packages in synaptic, or from a command line:
```
sudo apt-get install [COLOR=Red]*packagename*[/COLOR]
```

---

### Post by uldo on 2008-10-26
thx that package really worked (restricted one), but i still can't load most used java applet, what could be the problem?..... all other seems to work without problems.....

and I have another few stupid questions:
1. flash player plugin (firefox) - which should be the best (solved by me)
2. about fstab..... just cant get it. how it works....

---

### Post by Nepherte on 2008-10-26
2. [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by uldo on 2008-10-26
1. flash player plugin (firefox) - which should be the best (solved by me)
2. about fstab..... just cant get it. how it works.... (thx Nepherte)

so the last and most important problem still remains..... for example: "what you see is what you get" editor isnt starting, it just keeps showing loading and thats it...... "Start: applet not initialized" ......
At java console I get this:
Exception in thread "main" java.lang.NoClassDefFoundError: console
Caused by: java.lang.ClassNotFoundException: console
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: console. Program will exit.

is there any solution for this??

---

### Post by uldo on 2008-10-26
anyone??

---

