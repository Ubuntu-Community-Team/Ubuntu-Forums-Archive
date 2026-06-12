---
title: "problem with sli and 9600gt"
date: 2009-02-22
forum: Hardware
---

### Post by crazyone on 2009-02-22
hi i am trying to get my new video cards working in linux i jsut did a fresh install and if i install with  both video cards in after it finishes installing 8.10 64bit it boots to a black screen. i tried install with jsut one of them becuase i had only one for a while and it works jsut fine but as soon as i add the second card i get the black screen, even after removing the second card i still get a black screen. any help here would be nice.

---

### Post by komputes on 2009-02-24
I don't know if this card is supported by the nvidia driver yet. You can try your luck by going to System > Admin > Hardware Drivers

If activating a driver though there and rebooting does not work, you may want to try getting the driver from nvidia directly using envyng

Just open a terminal and install then run the program:
$ sudo apt-get install envyng-gtk
$ envyng-gtk

---

