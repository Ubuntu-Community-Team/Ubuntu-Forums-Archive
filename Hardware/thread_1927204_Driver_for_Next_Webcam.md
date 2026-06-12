---
title: "Driver for Next Webcam"
date: 2012-02-17
forum: Hardware
---

### Post by Aqil on 2012-02-17
I got a "Next" webcam for free. Nothing happens when I plug it in. So I suppose I need a driver? Where do I find that and how do I install it?

---

### Post by winh8r on 2012-02-17
This should get you started:


[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

Any issues, just post back here.

---

### Post by Aqil on 2012-02-17
Indeed, it did. Thank you!

I tried with Cheese and it worked. But the image is upside down and so blurry that I could barely see that it was upside down. Sure its an old webcam but it's not that bad.

So I read the webcam troubleshooting...
[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)
...and tried tip no.6, guvcview and luvcview but just ended up with errors with both. So what now?

---

### Post by winh8r on 2012-02-17
can you open a terminal and enter


```
hwinfo --camera
```


and copy and paste the result in your next post please

---

### Post by Aqil on 2012-02-17
After being prompted to install it, yes. But I get an error.

> > hal.1: read hal dataprocess 5092: arguments to dbus_move_error() were incorrect

...and it goes on

---

### Post by winh8r on 2012-02-17
sorry i misread your reply, reposted above now!

---

### Post by winh8r on 2012-02-17
ok, dont know what is going on there for now,


try

```
lsusb
```


you can past the entire result, and use the # code tags


****quick and dirty fix for now is open Cheese> Effects> and do a vertical flip of the image.*****

but post the output of the above command anyway

---

### Post by Aqil on 2012-02-17
hwinfo --camera gives

#
> hal.1: read hal dataprocess 5092: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
#

lsusb gives

#
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0c45:602c Microdia Clas Ohlson TWC-30XOP Webcam
#

edit: hmm... # tags? I had trouble just coping the output, took I while to realize I had to use the mouse :)

---

### Post by winh8r on 2012-02-17
Ok, do you get any output from this command?



```
sudo lsusb -d  0c45:602c  -v | grep "14 Video"
```


please post it if you do.

---

### Post by Aqil on 2012-02-17
No, nothing actually. It prompts my password but then nothing.

---

### Post by winh8r on 2012-02-17
Looks like it doesn't have the uvc capability then.



Enter name of Camera into search engine and you "might" find some way to get the image to flip , but some of the cheaper cameras just do not want to play!

Sorry I cannot be of much more help to you, there maybe someone else who has this issue with that brand of camera who might have a solution.

You can post again tomorrow to bump the thread again if there are no other replies.

(I have to go soon as I have to be at the airport in three hours!!!)

Good luck

---

### Post by Aqil on 2012-02-17
Thank you so much for helping as much as you could!

---

