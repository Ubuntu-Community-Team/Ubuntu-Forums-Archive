---
title: "samsung nc10 netbook"
date: 2008-11-20
forum: Hardware
---

### Post by Choad on 2008-11-20
installed ubuntu on it and have a few problems

the wifi doesn't work, and none of the FN keys work

anyone got some tips on setting it up?

edit:
kay got wireless done by installing svn madwifi. still need help with the brightness keys (volume keys do actually work)

---

### Post by jesuspresley on 2008-11-20
There is a workaround solution, you can use meanwhile there are no proper drivers:
[http://nc10ubuntu.wordpress.com/2008/11/13/workaround-1/#comment-32](http://nc10ubuntu.wordpress.com/2008/11/13/workaround-1/#comment-32)

---

### Post by Choad on 2008-11-20
nice one buddy, that'll be a good blog to keep an eye on.

having some issues with wireless and suspend. wireless is provided by madwifi svn, and it works great, but once suspended and resumed it won't reconnect. it tries, then asks for the password again. tried restarting network services, no avail. only a cold boot will ressurect the wireless.

---

### Post by Jon Bradbury on 2008-11-21
That's odd - mine works perfectly on suspend / restart. Have you applied all the Hardy updates yet?

---

### Post by Choad on 2008-11-22
> **Jon Bradbury said:**
> That's odd - mine works perfectly on suspend / restart. Have you applied all the Hardy updates yet?
i am on intrepid as it happens, not hardy. maybe i'll install hardy on another partition see if it works better

---

### Post by Jon Bradbury on 2008-11-25
Sorry, I meant Intrepid. Install the updates as requeested by update manager and try again.

---

### Post by jesuspresley on 2008-12-27
Have you installed the Wireless driver using the outdated [backported] Atheros drivers?

 Quick tutorial here:
[https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros](https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros)

Worked flawlessly with my system.

---

