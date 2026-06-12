---
title: "Logitech G15 M and G keys"
date: 2009-08-09
forum: Hardware
---

### Post by doomsayer97 on 2009-08-09
I know that this question has been asked dozens, if not hundreds of times. But I still can't manage to get them to work.


Does anyone know of a guide that'll do it? 
I've gotten the LCD to display a clock by installing G15stats, but that's it.

---

### Post by psmaster on 2009-08-11
This should help:
[http://ubuntuforums.org/showthread.php?t=267118&highlight=G15composer](http://ubuntuforums.org/showthread.php?t=267118&highlight=G15composer)

---

### Post by doomsayer97 on 2009-08-11
Thanks for the link... I'll have a go at it and see if it works :)


EDIT

I get stuck at this line:
```
sudo modprobe uinput
```
I get this output:
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release
```

Is anything supposed to popup during this?
And what is modprobe?

---

### Post by xenonR on 2009-08-12
It jst says **/etc/modprobe.d/ndiswrapper** will not be recognized in future releases and should be changed to **/etc/modprobe.d/ndiswrapper_.conf_**

Ther should no output at all. But you can use **lsmod | grep uinput** afterwards to check it. (No outpput = not loaded)

Read **man modprobe**

-xenonR

---

### Post by doomsayer97 on 2009-08-12
So.... It's fine? :)

Now I feel stupid ^_^

---

### Post by psmaster on 2009-08-12
> **doomsayer97 said:**
> So.... It's fine? :)

Now I feel stupid ^_^

Don't feel stupid man, it is all part of the learning process

---

### Post by doomsayer97 on 2009-08-12
> **psmaster said:**
> Don't feel stupid man, it is all part of the learning process


Yes yes of course it is...


Seems as if the guide was outdated, so I went to the one that he linked to (still very old though). It DID work... But uuuhh.... G and M keys still aren't working :confused:

---

### Post by psmaster on 2009-08-14
try using the app g15macro
Here is a good place on LinuxQuestions.org that includes the G keys:

[http://http://wiki.linuxquestions.org/wiki/Logitech_G15]("http://http://wiki.linuxquestions.org/wiki/Logitech_G15")

---

### Post by doomsayer97 on 2009-08-18
Still didn't work O.o


Everything ran perfectly fine. 


Added all the correct files, set everything to start when it was supposed to. G and M keys still don't work.

---

