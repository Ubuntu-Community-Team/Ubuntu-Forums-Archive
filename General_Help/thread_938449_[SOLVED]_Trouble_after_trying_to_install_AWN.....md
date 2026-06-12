---
title: "[SOLVED] Trouble after trying to install AWN...."
date: 2008-10-04
forum: General Help
---

### Post by kwboom on 2008-10-04
Hi there I tried to install AWN the other night and something went really wrong.  I tried to install it and it did not show up in the Applications>Accessories, so I tried it again and now I can't get into much with the terminal and there is a error icon in the top menu bar that shows this when I click on it.......

[IMG]http://i43.photobucket.com/albums/e388/kwboom/Screenshot-update-manager.png[/IMG]


Can anybody help with this......:confused:

---

### Post by kwboom on 2008-10-05
Sorry for not waiting for the 24 hours but this is really messing me up and I can't install nothing else cause of the error in the package manager.....


sorry again for not waiting for the 24 hours.......

---

### Post by Amstell on 2008-10-05
open up 
sudo gedit /etc/apt/sources.list

On line 64 look for the word echo and delete it.  You should only have deb and deb-src.  Echo is used from the command line to copy it there but it is almost as easy to just edit your sources.list.

Example : 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

Not : 
echo deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

delete the echo and save.

Now just : sudo apt-get update

and you should be good to go.

Peace

---

### Post by Amstell on 2008-10-05
Great readme on installing AWN :

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by kwboom on 2008-10-05
thankyou for the help I got it fixed..... there was alot of junk in there.... I deleted one thing and another came up.. So I worked through all that and got it working again......

Thankyou again for the help and this forum is the best help for Linux out there.....:guitar:

---

