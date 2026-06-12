---
title: "NetBeans problem."
date: 2008-08-13
forum: General Help
---

### Post by Crafty Kisses on 2008-08-13
For the past couple of days I've been having a lot of problems with Java programs such as Eclipse which I haven't been able to get to work in 4 days, but still working on it, now when I ran NetBeans today, it stopped working for some reason, now when I open NetBeans I get this:
```
java.net.UnknownHostException: codename: codename
at java.net.InetAddress.getLocalHost(InetAddress.java :1315)
at org.netbeans.CLIHandler.initialize(CLIHandler.java :487)
at org.netbeans.CLIHandler.initialize(CLIHandler.java :291)
at org.netbeans.Main.execute(Main.java:161)
at org.netbeans.Main.main(Main.java:4

```
So I read up on this issue, and I need to add a couple of lines to this configuration file, so I did:
```
sudo gedit /etc/hosts
```
I added what I needed too, but now when I boot into NetBeans I get this:
```
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: lexical error or unexpected token, expected valid token
```
It's almost acting like I'm trying to install it, very weird.

Supposedly if I was running Java 1.5 I'd be getting this error, but I tried this:
```
./netbeans-6.5_m1-php-linux.sh --javahome /usr/lib/jvm/java-6-sun
```
To direct it to **java-6-sun** so it possibly could work, but still getting these errors.

It's almost like I'm cursed with Eclipse and NetBeans, I'm kinda frustrated but I know I can resolve this sooner or later, just need some ideas and a little help. I've tried numerous things with both programs and still nothing. It's obviously something to do with Java but I'm not sure what. Thanks for your time.

---

### Post by tinny on 2008-08-15
Do you have to use a alpha version of NetBeans? (6.5m1)

Have you tried using NetBeans 6.1? Or NetBeans 6.0.1 from the Ubuntu repositories?

What is the output of the following...
```

java -version
javac -version

```

---

