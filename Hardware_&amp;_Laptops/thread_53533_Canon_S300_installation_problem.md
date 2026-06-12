---
title: "Canon S300 installation problem"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by blackant on 2005-08-01
Hopefully someone can help me on this.
Search around, only to find suggestion use alternative drivers.

I have found the original drivers from canon for this printer - S300.
But I am not sure what other files I should download.

[ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)

Also, I don't know how to install it as it is in .rpm

I am a newbie to linux, just managed to set up my first Ubuntu linux 2 days ago.
Please guide me in simple steps.

Thanks.

---

### Post by coolclassic on 2005-08-01
You can get drivers for your printer from: [http://www.turboprint.de/](http://www.turboprint.de/)
Just follow the instructions for .tgz, the installation is relatively easy.

---

### Post by kosmic on 2005-08-01
if the driver you have is in rpm format then in a console issue this comand :

alien -d filename.rpm

then you will have a .deb package, to install the .deb package issue this one :

dpkg -i filename.deb

and your driver should be instaled :) (hope it have no dependencies )


Ups, the easy way is -> alien -i filename.rpm it will install the rpm :)

---

### Post by blackant on 2005-08-01
[QUOTE=kosmic]if the driver you have is in rpm format then in a console issue this comand :

alien -d filename.rpm

then you will have a .deb package, to install the .deb package issue this one :

dpkg -i filename.deb

and your driver should be instaled :) (hope it have no dependencies )


Ups, the easy way is -> alien -i filename.rpm it will install the rpm :)[/QUOTE]
 I tried that, but still couldn't find the driver displayed in the driver list.

---

### Post by blackant on 2005-08-02
I need help and I still can't the S300 driver display on the list for me to choose when installing my printer.

Anyone has experience with installing this printer can help?
Thank you.

---

### Post by coolclassic on 2005-08-03
Here's a link that might help:
[http://www.linuxquestions.org/questions/archive/18/2005/02/4/165024](http://www.linuxquestions.org/questions/archive/18/2005/02/4/165024)

The problems with rpm's is that they can be distro pacific what that means is if the rpm was prepare for turbolinux then their may be some difficulty installing on another system. As canon is an Asian company then it is likely that the rpm was prepared using Turbolinux or Redhat.

If the above link does not help I would still give Turboprint a go. This is excellent soffware which will give you the full function of your printer.

[http://www.turboprint.de/](http://www.turboprint.de/)

---

### Post by blackant on 2005-08-03
[QUOTE=coolclassic]Here's a link that might help:
[http://www.linuxquestions.org/questions/archive/18/2005/02/4/165024](http://www.linuxquestions.org/questions/archive/18/2005/02/4/165024)

The problems with rpm's is that they can be distro pacific what that means is if the rpm was prepare for turbolinux then their may be some difficulty installing on another system. As canon is an Asian company then it is likely that the rpm was prepared using Turbolinux or Redhat.

If the above link does not help I would still give Turboprint a go. This is excellent soffware which will give you the full function of your printer.

[http://www.turboprint.de/](http://www.turboprint.de/)[/QUOTE]
 I am not sure about turboprint.. but they are not free. :(

---

