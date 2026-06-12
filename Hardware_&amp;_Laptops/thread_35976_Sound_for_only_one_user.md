---
title: "Sound for only one user"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by rodneyorpheus on 2005-05-21
On my laptop I was getting heavily distorted sound, so I followed the instructions at

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

which got it working perfectly.

However now sound only works for me, the admin account. When someone else logs in to their account they get a "Cannot create pipeline" error message. I assume this is some kind of permissions problem? Anyone have any ideas how to solve it?

Rodney

---

### Post by lovebug356 on 2005-05-21
This is the way how I made every user use the audio:

- System -> Administration -> Users and groups
Click on the user you want - properties
    - User privileges tab
      select "use audio devices"

---

