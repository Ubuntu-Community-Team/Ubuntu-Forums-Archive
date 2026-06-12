---
title: "is there anything like gotomypc for ubuntu?"
date: 2008-07-29
forum: General Help
---

### Post by brnetonboy on 2008-07-29
I'd like to connect to a different computer the way that gotomypc and logmein let you do. But they aren't compatible wiht linux, looks like...

---

### Post by ibutho on 2008-07-29
You can use ssh or something like VNC to connect to a remote machine.

---

### Post by mannheim on 2008-07-29
Another alternative is nx, from nomachine.com.

---

### Post by steveneddy on 2008-07-29
And Remote Desktop is a pre-installed version of VNC.

Works like a charm.

System --> Preferences --> Remote Desktop

---

### Post by brnetonboy on 2008-07-29
Thanks.

Does this only work if both computers are on the same network?

What if I want to do it over the internet?

---

### Post by steveneddy on 2008-07-29
> **brnetonboy said:**
> Thanks.

Does this only work if both computers are on the same network?

What if I want to do it over the internet?

the looker will have to know the lookie's IP address.

Say you want your friend to see your PC screen at his house on his PC.

Go to

[www.ipchicken.com](www.ipchicken.com)

and get your IP address.

If he has Ubuntu, he would type in terminal

```
vncviewer xxx.xxx.xxx.xxx:0 
```

where the xxx.xxx.xxx.xxx is the IP address you found on the ipchicken web site.

Now, Windows can use a free VNC viewer and type in your IP and get the same results.

Look here for Windows free VNC viewers.

[http://www.realvnc.com/products/free/3.3.7/winvncviewer.html](http://www.realvnc.com/products/free/3.3.7/winvncviewer.html)

Cool part about this is that if your machine has more than one user on it, that person can VNC into the machine locally or remotely and see their desktop and work while someone is doing the same thing locally.

Just use the :1 or :2 commands at the end of the line to get another desktop.

(ie xxx.xxx.xxx.xxx:1) gets you a different desktop than the one you see locally.

the :0 looks at your screen that you see locally.

cool - huh?


sorry if this is too much.

---

### Post by tashmooclam on 2008-07-29
I think that if the *target* computer is not Ubuntu, you can put something called "Logmein" onto the other (PC or Mac). This little program is supposed to let you use a browser to get to the computer with Logmeinfree on it. If both computers are Ubuntu, then the other answers mentioned here will apply. If you are using the VNC that is in Ubuntu to access a Mac, it's necessary to change the default program for some reason to something called "xtightvnc". 

[https://secure.logmein.com/products/free/](https://secure.logmein.com/products/free/)
[https://help.ubuntu.com/community/AppleRemoteDesktop](https://help.ubuntu.com/community/AppleRemoteDesktop)

---

### Post by tashmooclam on 2008-07-30
The method that is most like "gotomypc" is logmeinfree, because it goes through a web browser.

I researched this because I want to put a Mac with a webcam at my mother's house and be able to turn it on, start the program, etc. remotely.

Turns out because it's a Mac, I don't have to. I can preference her Mac to startup and shutdown on a schedule (like a clock radio), startup iChat on automatic login, and set iChat to answer my iChat video call automatically also. But, I will definitely put that Logmeinfree program on it. Let us know your results, I am curious.

---

### Post by hyper_ch on 2008-07-30
If you are on the same subnet then you just use the IP of the other computer.
If you are not, you may way to install something like no-ip or dyndns and if you are behind a router also port-forward the according port to the computer behind it (port 22 for ssh)

---

