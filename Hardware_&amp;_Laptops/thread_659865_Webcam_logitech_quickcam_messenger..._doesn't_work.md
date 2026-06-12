---
title: "Webcam logitech quickcam messenger... doesn't work fine..."
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by PauGNU on 2008-01-06
Hi, 

I've just bought a webcam "logitech quickcam messenger". First I've tested with my own user and it works fine (with cheese, for example). Then I've tried with another user and... it doesn't work. When I run cheese, program says that "Could not detect device". Ekiga could not detect too the webcam.

I've tried to change permissions for that user and create new user too. But didn't work...

Any ideas?

Thanks!

---

### Post by BushiLINUX on 2008-01-06
hey i have a logitech quickcam stx and i am using ubuntu 7.10....mine works with ..kopete messenger when i am using the hotmail protocol.I dunno if that would help u but happy new year

---

### Post by AlesUbu123 on 2008-01-06
Have you tried camorama package?

Regards!

---

### Post by Galban on 2008-01-06
I have exactly the same problem as pauGNU has , but only after upgrading to Gusty :confused:. The web cam works just fine but only on the administrator account. Camorama, aMSN all of them are working with web cam on the administrator account, but NOT on the secondary accounts. The device is simply not detected on those accounts. I guess it's should be matter of change something on dev/conf. Please, any help will be appreciated. Thanks.

---

### Post by bwtranch on 2008-01-06
Man, I'm sorry, but I've nothing but bad luck with Camorama and that quick Cam Messenger. That thing screwed up my USB driver package and I won't go there again!

---

### Post by PauGNU on 2008-01-07
Yeah... same problem with camorama. Could not connect to video device!!

---

### Post by PauGNU on 2008-01-07
Hi

Finally I solved the problem. Problem was the usergroups, it seems admin user (when you install ubuntu) has different permissions than users you can create later. 

First, we have to test our admin permissions:
```
sudo USER groups
```

In my case:
```
cari@mare:~$ sudo groups pau
pau : pau adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin
```

Then, if we test other users permissions, result will not be the same. We have to add groups that are in our admin user to the other users with:
```
sudo adduser USER video
``` (for example)

Where USER is your "other user" who is not admin. I think adding the USER to video group is sufficient.

Then, you have to restart.

---

