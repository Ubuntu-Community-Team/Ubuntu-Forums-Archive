---
title: "Can't choose my Thrust WB3400T-Webcam with gstreamer-properties..."
date: 2008-05-01
forum: Hardware
---

### Post by BurgerKing on 2008-05-01
Hi @ All!
I have the following Problem: If I want to choose my Webcam (it's a Thrust WB3400T-Webcam) via Gstreamer-Properties so that Cheese and Camorama do use it, I get the following output in the konsole:
```
$ sudo apt-get install v4lmjpegsrc qcamsrc esdmon
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Reading state information... Fertig
E: Konnte Paket v4lmjpegsrc nicht finden
$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2359): gst_base_src_start (): /pipeline2/v4l2src4:
Check your filtered caps, if any]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2359): gst_base_src_start (): /pipeline3/v4l2src5:
Check your filtered caps, if any]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2359): gst_base_src_start (): /pipeline4/v4l2src7:
Check your filtered caps, if any] 
```
The strange thing with this is that aMSN can use the cam without any Problems...
In the german-Ubuntu-forum (ubuntuusers.de) nobody know to solv this, too.
I would be very happy if anybody here know how to fix this Error...
Best regards and Have a nice day!
BurgerKing

---

### Post by BurgerKing on 2008-05-02
*push*

---

### Post by BurgerKing on 2008-05-06
nobody can help? =*(

---

### Post by BurgerKing on 2008-05-09
seems like nobody can help this makes me very sad =(
So I'll give it up

---

