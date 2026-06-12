---
title: "Ubuntu 8.10 kill webcam support?"
date: 2008-11-03
forum: Hardware
---

### Post by csseurg6 on 2008-11-03
Hello,

ubuntu 8.10 is very funny, it's the first version of ubuntu where my webcam is not supported :p

My webcam is ID 046d:0870 Logitech, Inc. QuickCam Express

So, under Debian Lenny (for example), she works great when i make ```
sudo m-a update && sudo m-a prepare && sudo m-a a-i qc-usb-source
```

Please, help me to use my webcam, i don't understand what is wrong.

Bye

---

### Post by eldragon on 2008-11-03
there are lots of things that could go wrong with the little ammount of info you have given.


first thing id want you to try is install cheese (repositories), and check if the webcam works there.

if it works there, id like to know in which program it doesnt work...

if its skype, check this thread [http://ubuntuforums.org/showthread.php?t=945803](http://ubuntuforums.org/showthread.php?t=945803)

---

### Post by csseurg6 on 2008-11-03
the webcam doesn't work with:

- amsn
- xawtv
- cheese
- camorama
- easycam

the only thing that can i have is a black screen when i chmod my /dev/video0 in 777.

---

### Post by csseurg6 on 2008-11-03
```
fred@fred-laptop:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-7-generic)
xinerama 0: 1280x800+0+0
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
libv4l2: error getting capabilities: Erreur inconnue 515
ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Erreur inconnue 515
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

```

---

### Post by csseurg6 on 2008-11-03
so, the quickcam module is loaded, but the webcam doesn't work.

---

### Post by dri123 on 2008-11-04
Same thing whit my cam
dri@dri-desktop:~$ lsusb
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 046d:08d7 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 054c:0243 Sony Corp. 
Bus 001 Device 001: ID 0000:0000  
she work in ubuntu 7.10 and in 8.04 but not in 8.10 so i think to stay whit hardy.

---

### Post by csseurg6 on 2008-11-04
a bug report is open: [https://bugs.launchpad.net/ubuntu/+bug/293176](https://bugs.launchpad.net/ubuntu/+bug/293176)  :)

---

### Post by csseurg6 on 2008-11-05
Hello,

there is a solution? i can't wait six months...

---

### Post by loell on 2008-11-05
try preloading

```
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so 
```
then start any of your webcam app.

---

### Post by csseurg6 on 2008-11-05
> **loell said:**
> try preloading

```
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so 
```
then start any of your webcam app.

the webcam always doesn't work

---

### Post by loell on 2008-11-05
maybe the particular webcam model has not yet been included in libv4l.

---

### Post by MrSootentai on 2008-11-05
I'm having the same problem. Webcam worked sometimes in 7.10, perfect in 8.04, and now won't work at all in 8.10.
When loading cheese the app just freezes and the light on my webcam stays lit until I kill the app from the system monitor.

---

### Post by MrSootentai on 2008-11-05
[Sorry Double Post]

---

### Post by Bill magee on 2008-11-05
Might be your webcam model, because my webcam works now under 8.10 and never worked before!

This Acer laptop has Crystal Eye webcam.

---

### Post by csseurg6 on 2008-11-05
i repeat
```

ubuntu 8.10 is very funny, it's the first version of ubuntu where my webcam is not supported 
```

[LIST]
[*]5.10 : great
[*]6.06: great
[*]6.10: great
[*]7.04: great
[*]7.10: great
[*]8.04: great
[*]8.10: doesn't work
[/LIST]

i don't really think that my webcam is a particular model... so it works under debian lenny too for example.

ubuntu 8.10 is the first gnu/linux distribution that doesn't recognize my webcam.

please do it something, or i can't stay on ubuntu :(

bye.

---

### Post by MrSootentai on 2008-11-05
> **csseurg6 said:**
> 
please do it something, or i can't stay on ubuntu :(

bye.

Sounds like you're giving them an ultimatum...

But really any help would be appreciated. I used my webcam all the time, and was so happy when 7.04 finally kind of got it working.

Anything I can do to help find a fix for this problem??

---

### Post by loell on 2008-11-05
> **csseurg6 said:**
> i repeat
```

ubuntu 8.10 is very funny, it's the first version of ubuntu where my webcam is not supported 
```

[LIST]
[*]5.10 : great
[*]6.06: great
[*]6.10: great
[*]7.04: great
[*]7.10: great
[*]8.04: great
[*]8.10: doesn't work
[/LIST]

i don't really think that my webcam is a particular model... so it works under debian lenny too for example.

ubuntu 8.10 is the first gnu/linux distribution that doesn't recognize my webcam.

please do it something, or i can't stay on ubuntu :(

bye.

pretty much every major distributions with their new versions is having this problem. you could either wait, or revert to older versions.

---

### Post by peacewithall on 2008-11-06
Try this post,

[http://ubuntuforums.org/showpost.php?p=6115686&postcount=30](http://ubuntuforums.org/showpost.php?p=6115686&postcount=30)

Try both commands (one at a time) from terminal, and obviously replace 'skype' if you're not using that, and replace it with the application you are trying to use with your web-cam.

---

### Post by coltrane on 2008-11-06
I got the same with a haupguage win-tv usb, doesn't work anymore in 8.10 but did in 8.04.

---

### Post by coltrane on 2008-11-07
Gone back to 8.04, 8.10 is awful, can't do much with it and it seems very unstable, it also freezes after a couple of days and the windows don't display properly from the beginning and that was a fresh install, reminds me more of windows 98.

---

### Post by Alajjana on 2008-11-21
> **coltrane said:**
> Gone back to 8.04, 8.10 is awful, can't do much with it and it seems very unstable, it also freezes after a couple of days and the windows don't display properly from the beginning and that was a fresh install, reminds me more of windows 98.

How does one do that?

---

### Post by Yezinki on 2008-11-21
> **csseurg6 said:**
> the webcam doesn't work with:

- amsn
- xawtv
- cheese
- camorama
- easycam

the only thing that can i have is a black screen when i chmod my /dev/video0 in 777.


For all those you would need a Logitech Quick Cam Pro 9000.

Read the thread webcam update 8.10.

I apologize that I wouldn't be of much help since I quit Ubuntu & am using windows again....

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-21
> **loell said:**
> maybe the particular webcam model has not yet been included in libv4l.

Correct!

---

### Post by Yezinki on 2008-11-21
> **csseurg6 said:**
> Hello,

there is a solution? i can't wait six months...

Worth investing 90 bucks in a awesome piece of hardware 100% Ubuntu 8.10 compatible...tried & tested.

---

### Post by seaq on 2008-12-23
Hi, i've put in the wiki a list for known bugs with webcam cameras.


[https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams](https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams)

---

