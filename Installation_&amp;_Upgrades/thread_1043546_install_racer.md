---
title: "install racer"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by fingerrish on 2009-01-18
i just downloaded the game racer from official site. but how can i run it or install it? in archive there is no info how to! 
WHY CAN'T UBUNTU MAKE SIMPLE INSTALLATION???!!

---

### Post by amauk on 2009-01-18
instructions are right there on the website

unpack to folder somewhere
run ./racer

:rolleyes:

---

### Post by taurus on 2009-01-18
WHY CAN'T GAME MAKER MAKE SIMPLE INSTALLATION???!!

What is the exact name of the game?  Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by fingerrish on 2009-01-18
> **amauk said:**
> instructions are right there on the website

unpack to folder somewhere
run ./racer

:rolleyes:

when i do that nothing happens

---

### Post by fingerrish on 2009-01-18
> **taurus said:**
> WHY CAN'T GAME MAKER MAKE SIMPLE INSTALLATION???!!

What is the exact name of the game?  Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

game is called RACER


total 25172
drwxr-xr-x  4 rich rich    12288 2009-01-18 23:48 .
drwxr-xr-x 58 rich rich    12288 2009-01-18 23:42 ..
drwxrwxrwx  6 rich rich     4096 2009-01-04 18:42 aija
drwxr-xr-x  2 rich rich     4096 2009-01-16 14:51 mvgfoto
-rw-r--r--  1 rich rich  1268839 2009-01-18 23:41 **racer053b6test.zip**
-rw-r--r--  1 rich rich 24439387 2009-01-18 23:24 **racer054b1.tgz**

---

### Post by taurus on 2009-01-18
```
cd ~/Desktop
tar xvzf racer054b1.tgz
ls -la
```
Post the output of the last command.

---

### Post by fingerrish on 2009-01-19
> **taurus said:**
> ```
cd ~/Desktop
tar xvzf racer054b1.tgz
ls -la
```
Post the output of the last command.

total 25176
drwxr-xr-x  5 rich rich    12288 2009-01-19 20:39 .
drwxr-xr-x 58 rich rich    12288 2009-01-19 20:31 ..
drwxrwxrwx  6 rich rich     4096 2009-01-04 18:42 aija
drwxr-xr-x  2 rich rich     4096 2009-01-16 14:51 mvgfoto
drwxr-xr-x  3 rich rich     4096 2008-02-20 22:36 **racer**
-rw-r--r--  1 rich rich  1268839 2009-01-18 23:41 **racer053b6test.zip**
-rw-r--r--  1 rich rich 24439387 2009-01-18 23:24 **racer054b1.tgz**

---

### Post by taurus on 2009-01-19
```
cd ~/Desktop/racer
./racer
```
If you get an error message from the second command, then post the output of this command here.

```
ls -la ~/Desktop/racer
```

---

### Post by fingerrish on 2009-01-19
> **taurus said:**
> ```
cd ~/Desktop/racer
./racer
```
If you get an error message from the second command, then post the output of this command here.

```
ls -la ~/Desktop/racer
```

jap. there was an eror

total 5032
drwxr-xr-x  3 rich rich    4096 2008-02-20 22:36 .
drwxr-xr-x  5 rich rich   12288 2009-01-19 21:58 ..
-rwxr--r--  1 rich rich      35 2008-02-20 22:36 carlab.ini
-rwxr--r--  1 rich rich   67982 2008-02-20 22:36 CHANGELOG.txt
drwxr-xr-x 17 rich rich    4096 2008-02-20 21:16 data
-rwxr-xr-x  1 rich rich  534212 2008-02-20 22:36 ini
-rwxr--r--  1 rich rich 1157068 2008-02-20 22:36 libfmodex.so
-rwxr-xr-x  1 rich rich  639785 2008-02-20 22:36 lowerize
-rwxr--r--  1 rich rich    1181 2008-02-20 22:36 modeler.ini
-rwxr--r--  1 rich rich     256 2008-02-20 22:36 pacejka.ini
-rw-r--r--  1 rich rich   43606 2008-02-20 22:34 QLOG.txt
-rwxr-xr-x  1 rich rich 2605410 2008-02-20 22:36 racer
-rwxr--r--  1 rich rich   31535 2008-02-20 22:36 racer.ini
-rwxr--r--  1 rich rich    1031 2008-02-20 22:36 tracked.ini

---

### Post by taurus on 2009-01-19
What is the error message when you try to run it?

```
cd ~/Desktop/racer
./racer
```

---

### Post by fingerrish on 2009-01-19
> **taurus said:**
> What is the error message when you try to run it?

```
cd ~/Desktop/racer
./racer
```

./racer: error while loading shared libraries: libfmodex.so: cannot open shared object file: No such file or directory

---

### Post by RJARRRPCGP on 2009-01-19
> **fingerrish said:**
> i just downloaded the game racer from official site. but how can i run it or install it? in archive there is no info how to! 
WHY CAN'T UBUNTU MAKE SIMPLE INSTALLATION???!!

I have the same issues, too. People usually have dependency issues. 

You can tell when you launch Racer from a terminal when installed.

---

### Post by s3kt0r on 2009-01-19
You have to install FMOD from [http://www.fmod.org]("http://www.fmod.org") for Racer to run. After, you just need to navigate to Racer's directory and run
```

./racer

```
Any more questions try the unnoficial [FAQ]("http://www.schuerkamp.de/zope/hoover/racing/racer_linux_faq") by Uwe Schuerkamp (it's old, but it could help solve some stuff). Ah, make sure you have latest beta, not stable, beta is in a more advance state.

---

### Post by fingerrish on 2009-01-20
> **s3kt0r said:**
> You have to install FMOD from [http://www.fmod.org]("http://www.fmod.org") for Racer to run. After, you just need to navigate to Racer's directory and run
```

./racer

```
Any more questions try the unnoficial [FAQ]("http://www.schuerkamp.de/zope/hoover/racing/racer_linux_faq") by Uwe Schuerkamp (it's old, but it could help solve some stuff). Ah, make sure you have latest beta, not stable, beta is in a more advance state.

ok. i downloaded fmod. how to install it???

---

### Post by s3kt0r on 2009-01-21
@ fingerrish:

I'm guessin' through the normal procedures...

```

./configure
make
make install

```

---

### Post by fingerrish on 2009-01-21
> **s3kt0r said:**
> @ fingerrish:

I'm guessin' through the normal procedures...

```

./configure
make
make install

```

still shows this:
./racer: error while loading shared libraries: libfmodex.so: cannot open shared object file: No such file or directory

---

### Post by fingerrish on 2009-01-22
ok everything now is working well
just coppied some files in liberies from fmod. thanks for help :)

---

### Post by windows-killer on 2009-01-22
is there a .deb package for this game?

---

### Post by yit on 2009-02-06
> **fingerrish said:**
> ok everything now is working well
just coppied some files in liberies from fmod. thanks for help :)

Could you be a little more specific as to what you did to make it work, what files you copied and to where? I am getting the same error trying to run this game. Thanks!

---

