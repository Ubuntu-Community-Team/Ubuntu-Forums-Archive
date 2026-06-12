---
title: "Google earth .bin"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by corpsehacker on 2009-04-09
Hello everyone. I tried installing google earth on my computer that is now running on only kubuntu (before I was running both ubuntu and kubuntu) and it came in a .bin file. I googled it and google said it is usually the same as a .iso file. I dont really want to waste a cd so I decided to ask the forum whether I should mount it like an iso or if there was a terminal command I could use to install it. Thanks.

---

### Post by finer recliner on 2009-04-09
you need to give the downloaded file execute permissions (this is a security feature)

```
chmod u+x googleearth.bin
``` (edit if i got the filename wrong)


then double click :)

---

### Post by corpsehacker on 2009-04-09
Yeah the file name is "GoogleEarthLinux.bin" and it is on the desktop registry so I assume I have to type "cd Desktop" before doing that.

---

### Post by taurus on 2009-04-09
```
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by corpsehacker on 2009-04-09
Thank you sir. It works perfectly.:)

---

### Post by beameup on 2009-04-20
Easy how-to here:

[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)

---

