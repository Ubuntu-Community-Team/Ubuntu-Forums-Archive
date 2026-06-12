---
title: "Installing ubuntu from usb stick"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by Pollore on 2008-12-22
Good afternoon,

I got a big problem trying to install ubuntu 8.10 from an usb stick on my netbook (samsung NC10). I have found different methods on how to try and get it to work for example this one:

[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)

But the problem first of all is that most tutorials are made to use on a computer that already runs linux. Since I have to do it with windows XP it's a bit harder. Second I tried a program called "Unetbootin", it makes the usb stick bootable alright but somehow I still can't install ubuntu just run it...

So my question really is. How do I make a 1GB usb-stick bootable and that I can install ubuntu 8.10 on my netbook. I want to make a dualboot with windows XP. Windows XP is already installed on my first partition and then I got a free second partition with the same size as the windows partition to install ubuntu on.

I hope somebody could help me cause I already tried various things this week but nothing seems to work.

Thanks in advance

---

### Post by knightrider37876 on 2008-12-22
I have not tried this yet (plan on it this weekend), but I found this link that seemed to be worth a try.

[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/) 

Hope this helps.

---

### Post by Pollore on 2008-12-22
thank you for your time.

I read the article and tried the automatically approach, but somehow it just keeps giving me errors on copying the files. I will try to work on the manually method tomorrow. Right now I am getting tired of all the work I put in and not getting out.

---

### Post by jaseanton on 2008-12-24
I did a fresh install yesterday on my NC10 of Ubuntu 8.10.  It was a breeze.  Fast, too.

'Create a USB startup disk' in Ubuntu, then:

Switch the NC10 off, stick the stick in the USB slot (there are security issues doing this), switch the machine on, hit F2 at the right moment, set the boot device priority to read off the stick first, and the rest was a pretty quick default install.

(I used the alternate release).  Very, very easy.

---

