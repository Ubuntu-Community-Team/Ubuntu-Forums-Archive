---
title: "Cannot find out how to use my simple scan"
date: 2011-11-16
forum: Hardware
---

### Post by ec1955 on 2011-11-16
I had installed -AND USED- SIMPLE SCAN- but it isn't in my launcher anymore - and I cannot locate it to use it - how can I find it ans start it.
Linux novice
Thanks
Ernest

---

### Post by SteveDee on 2011-11-17
> **ec1955 said:**
> ...how can I find it ans start it...

The app name is: simple-scan
So if you open a terminal and type:-
```

whereis simple-scan

```
...the reply should show: /usr/bin/simple-scan

As /usr/bin is in the system path, you should be able to type in a terminal:-
```

simple-scan

```
and this app should run.

However, you might find the easiest way to sort out this mess is to open Synaptic Package Manager and search for: simple-scan

You can then first remove it, then reinstall it. This should ensure all related files are installed in the right place and your menu launcher should re-appear.

---

### Post by ec1955 on 2011-11-17
Thanks alot!
I am so used to Windows - it is easy to locate things there - with Linux - as much fun as I am having using it - I don't understand how things are arranged to find them.
Is there any place where some of this basic stuff is explained?
Thanks
Ernest

---

### Post by SteveDee on 2011-11-17
> **ec1955 said:**
> ...Is there any place where some of this basic stuff is explained?


Lots, but start with these:-
[http://ubuntuguide.org/wiki/Ubuntu:Oneiric](http://ubuntuguide.org/wiki/Ubuntu:Oneiric)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

