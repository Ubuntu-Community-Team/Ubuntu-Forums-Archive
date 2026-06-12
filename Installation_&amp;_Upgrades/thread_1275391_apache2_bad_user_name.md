---
title: "apache2: bad user name"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by fleury29 on 2009-09-25
So I am trying to set up an apache server and I need multiple instances.  I have the instances set up but I keep running into problems with then envvars file.  Mine looks like this: 
```

export USER=vinny
export GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

#User vinny
#Group www-data

```

I have searched the interwebs profusely and the community keeps telling me that i need to change the user and group to 'www-data' which I have done with no success.  Anyone have any advice?

PS: I am a CS major with moderate Linux experience.

---

### Post by rreese6 on 2009-09-25
Are your users names also users of the linux box?
The way I have done it is the addusers to the box then run the httpd instances per user...it almost sounds like you may want to set up virtual servers...

If you just want to check it out then the generic install configuration
will show you if it works.
Also you need to make sure your users are part of the Apache group.

---

### Post by fleury29 on 2009-09-30
Ya the users are part of the group www-data and apache but still no aval.  I reinstalled it, but no success any suggestions?

I got the latest Apache2 and Latest Ubuntu (9.04)

---

