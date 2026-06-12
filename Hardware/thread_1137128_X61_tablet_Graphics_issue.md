---
title: "X61 tablet Graphics issue"
date: 2009-04-25
forum: Hardware
---

### Post by AKnightintheDesert on 2009-04-25
Just installed 9.04 on my Lenovo x61 Tablet.  Really happy about the out of box tablet support but now the advanced graphics settings don't work.  When I try to enable them threw the System > Preferences > Appearance, Visual affects tab it looks for a driver then says that the display settings can't be applied.  I have attached my Xorg.conf file in hopes that it will help.  Please let me know if there is anything I need to do to get more diagnostic information.  The error listed in the Auth.log error report is as follows:

```
Apr 25 10:37:08 andrew-tablet dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=3400 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.56" (uid=1000 pid=4416 comm="/usr/bin/python /usr/bin/jockey-gtk --check-compos"))
Apr 25 10:37:08 andrew-tablet dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=3400 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.57" (uid=109 pid=4421 comm="/usr/lib/policykit/polkitd "))
```

---

### Post by AKnightintheDesert on 2009-04-25
Sorry here is my Xorg.conf

---

### Post by AKnightintheDesert on 2009-04-25
Found the solution: 
[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

Apparently the Graphics driver has an issue hope they fix it soon

---

### Post by Sexy Volcano on 2009-04-25
did you find the fix aknight I have a lenovo x61tablet also and have the same problem

---

### Post by AKnightintheDesert on 2009-04-25
As I mentioned in post three the link has a solutions that worked for me. you simply enter this in a Terminal:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by Shwan.c on 2009-04-26
> **AKnightintheDesert said:**
> As I mentioned in post three the link has a solutions that worked for me. you simply enter this in a Terminal:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

It works fine for me, but I had a crash last night , a bad one, so bye bye compiz for now until the bug is gone

---

### Post by AKnightintheDesert on 2009-04-27
Still more stable than Vista.  Anyone know how we can contribute to the further development of this driver??

---

### Post by descent1 on 2009-10-18
I have x61 tablet (MODEL# 7764-CTO) and I am having exactly the same issue as you guys... 
I am recieving the following message after I try to enable desktop effects :
** (nautilus:5342): WARNING **: Unable to add monitor: Operation not supported

Also message popups sayings 'Desktop effects could not be enabled'

I tried running the above code in my terminal but it comes with that error ''** (nautilus:5342): WARNING **: Unable to add monitor: Operation not supported
''

Can anyone help?

---

