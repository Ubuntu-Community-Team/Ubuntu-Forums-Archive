---
title: "&quot;Cannot start purple's D-bus&quot;"
date: 2008-08-11
forum: General Help
---

### Post by Heide264 on 2008-08-11
I am having issues with my D-bus interface. I'm pretty new to linux in general and do not know much about this. I used to get an error everytime I started up which went away, but I do not believe it is starting properly still. Little things such as plugins for amarok that update my pidgin status and other cross program processes don't seem to be running right.

Is there any place you can point me for some background information on the D-bus or where to start to see if its running properly?

Thanks.

---

### Post by Dr Small on 2008-08-11
Could you please post the error message? I think I have an idea of what is going on, only I can't remember the name of the command you need to run at present.


**EDIT**
I think I found it. Try running:
```
sudo dbus-uuidgen --ensure
```

---

### Post by Heide264 on 2008-08-12
Didn't get any feedback on it - just put in the su pw and then went to the next line.

Is there a place you can suggest just to read up on it or anything? I've looked around but everytime I find something its a bluetooth error haha.

---

### Post by Heide264 on 2008-08-17
I don't get any error messages anymore, just most things that use dbus don't seem to work too well honestly. Originally the error message just said that "Purple's D-bus failed to start".

I am just gonna try looking around and finding some more general information on it. I will let you guys know if I come up with anything.

---

### Post by ShelJ on 2008-08-17
> **Dr Small said:**
> Could you please post the error message? I think I have an idea of what is going on, only I can't remember the name of the command you need to run at present.


**EDIT**
I think I found it. Try running:
```
sudo dbus-uuidgen --ensure
```


Hi, 

I tried this,but it didn't appear to work.

The error that I keep getting is as follows: ```
Purple's D-BUS server is not running for the reason listed below

Failed to get connection: Failed to execute dbus-launch to autolaunch D-Bus session
```



NM!  I think I was just trying to start the wrong plugin. 

However, I'm glad that I could help Heide264 figure out what the error was, maybe it'll be easier for someone to help you.

---

### Post by Heide264 on 2008-08-18
Yup that is the one I got too. Thanks =).

---

