---
title: "wireless driver noob issue"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by zerogt86 on 2005-05-07
Hi everyone, i just put ubuntu on my really old laptop and its great!  ive used all sorts of other distros before and i really like ubuntu. This is my first time using a debian based distro, and i need to install a pkg to get my internet working.  Ive downloaded the pkg, and put it on the laptop, but now where am i supposed to put it so that apt-get install will see it?

---

### Post by dave9191 on 2005-05-07
What sort of package is it? If its a .deb then you can install it using the  'dpkg -i package_name' command. 

apt-get wont see download files as it connects to repositories and downloads the files. Maybe putting a local directory into the repository list would make apt-get see downloaded files, but there isnt any point experimenting with that. Just use the other tools at hand.

---

