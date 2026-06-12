---
title: "Mobile Broadband"
date: 2009-11-23
forum: Hardware
---

### Post by 5349U11 on 2009-11-23
I was using my mobile broadband connection (Three Prepaid, Australia) using Ubuntu Karmic Koala and this was working fine. 

However recently (within the past three days) it has been connecting, yet the rest of the system has been acting as though i am not connected (firefox won't load any pages, i cannot update my system).

I can however still use this modem on the same computer when I run Vista :'(


How do i go about resolving this?

---

### Post by garikaib on 2009-11-23
Maybe the default route is not being replaced.
Try running the command:
sudo route add default ppp0

After you are connected. Then ping yahoo.com

---

### Post by qwerty2009 on 2009-11-23
for me i have to connect then disconnect and then connect again for it to start displaying web pages

---

### Post by 5349U11 on 2009-11-24
I have tried both of these, both have failed. :( thanx anyways

---

### Post by alexfish on 2009-11-24
try this link here

[http://ubuntuforums.org/showthread.php?t=1333179](http://ubuntuforums.org/showthread.php?t=1333179)

   don't forget to come back here other members will also help

[solved] here 
[http://ubuntuforums.org/showthread.php?t=1336197](http://ubuntuforums.org/showthread.php?t=1336197)

---

### Post by _tom_ on 2009-11-24
Same here. After the last update (did update for about a week) my mobile connection is broken. The DNS Servers don't get resolved. After I added them to the nm-applet->Mobile Broadband->IPv4->DNS Server the mobile connection works fine.

---

### Post by dineshs on 2009-11-24
Try if this link can help
[http://ubuntuforums.org/showthread.php?t=1284844](http://ubuntuforums.org/showthread.php?t=1284844)

---

### Post by alexfish on 2009-11-24
just ran through upgrade / same problems / as mentioned 

  to note 

     each provider in a lot cases  use the    """"" same chip set """"""

       its worth a visit to this site to find the reasons why


  [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

  read carefully 
         
   this is one of the reasons I try to avoid naming  "named brands"

       if have problems     please continue to   " Quote the model or type "

      " and  the problem  "

       each type my have specific issues  

  so at the present I am connected without having to go out to buy a recomended dongle or what ever 

to find the name of the device plug it in

goto applications/accessories/terminal

type in

lsusb

KEEP POSTING

---

### Post by 5349U11 on 2009-11-25
> **_tom_ said:**
> Same here. After the last update (did update for about a week) my mobile connection is broken. The DNS Servers don't get resolved. After I added them to the nm-applet->Mobile Broadband->IPv4->DNS Server the mobile connection works fine.
nm-aplet?

---

### Post by Grenage on 2009-11-25
I had this what fixed it for me was going into FF settings and selecting "no proxy".  There seems to be an issue with the gnome network manager handling it properly.

---

### Post by alexfish on 2009-11-25
[solved here]


[http://ubuntuforums.org/showthread.php?t=1336197](http://ubuntuforums.org/showthread.php?t=1336197)

---

### Post by singhal.r on 2009-11-27
> **alexfish said:**
> [solved here]


[http://ubuntuforums.org/showthread.php?t=1336197](http://ubuntuforums.org/showthread.php?t=1336197)

How is this solved with this thread. This above mentioned thread if a problem with DSL. 

Strange enough that this problem is there with me for 9.04 and 9.10 version. I connect using mobile EDGE connection. The connection on PC and mobile (Windows mobile, HTC touch) remains active but there is no data transfer.

Only possibility is to re-connect on my windows mobile. Initially I thought this to be a problem with provider (But then it works on Windows) and then the mobile (But then I changed to latest mobile ROM multiple times and the issue remains the same.

Any help possible??

---

### Post by alexfish on 2009-12-01
> **singhal.r said:**
> How is this solved with this thread. This above mentioned thread if a problem with DSL. 

Strange enough that this problem is there with me for 9.04 and 9.10 version. I connect using mobile EDGE connection. The connection on PC and mobile (Windows mobile, HTC touch) remains active but there is no data transfer.

Only possibility is to re-connect on my windows mobile. Initially I thought this to be a problem with provider (But then it works on Windows) and then the mobile (But then I changed to latest mobile ROM multiple times and the issue remains the same.

Any help possible??
Hi 

the heading of the post is 

**Cannot connect to internet on Ubuntu 9.10**

  I am trying trace the the reasons why /  I will post the link soon

    Regards

   alexfish

---

### Post by 5349U11 on 2009-12-04
Internet has spontaneously started working again

thanx to those who helped

---

