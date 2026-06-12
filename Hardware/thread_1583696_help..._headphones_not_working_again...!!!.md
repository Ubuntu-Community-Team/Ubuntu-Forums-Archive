---
title: "help... headphones not working again...!!!"
date: 2010-09-28
forum: Hardware
---

### Post by Rahuljaiswal on 2010-09-28
I have sony vaio M series netbook. when i installed ubuntu 10.04 its headphones was not working (this was the only problem i faced).. then i did this process from ubuntu forums 
1. sudo apt-get install build-essential
2. wget [ftp://ftp.alsa-project.org/pub/drive...1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.23.tar.bz2)
3. tar -xjf alsa-driver-1.0.23.tar.bz2
4. cd alsa-driver-1.0.23/
5. ./configure
6. make
7. sudo make install
8. alsamixer (don't know if this step was necessary since my volume was already enabled)
9. reboot

and my headphones started working... 

here is the problem now... last night i updated my software n all using update. and after that don't know why my headphones again, they are not working... without headphones my laptop internal speakers working perfectly fine. my headphones have no problem... please any one suggest what should  i do. 
ubuntu is detecting my sound card etc. and i have checked all options in alsamixer as well.  please somebody help... :(

---

### Post by Rahuljaiswal on 2010-09-28
oh i got the solution... 
follow this link...

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

