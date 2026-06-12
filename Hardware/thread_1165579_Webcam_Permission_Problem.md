---
title: "Webcam Permission Problem"
date: 2009-05-20
forum: Hardware
---

### Post by giosico on 2009-05-20
So the reason my HP Pavilion DV6000 webcam does not work in Skpe is because of Linux webcam permissions.  I know this and will explain below.  What I do not know is how to fix it properly.

install skype from deb using sudo
install webcam driver using sudo

test webcam using sudo xawtv ... work ok
skype cant find webcam ... :(
run skype with gksu ... skype can find webcam

change /dev/video0 to 777 permissions skype can find webcam
when the computer reboots /dev/video0 reverts permissions

in the past adding the video group (newgrp video) to my user fixed this.  not anymore with Ubuntu 9

I want this to work without gksu because I start skype with pidgin and do not have the option to gksu skype that way ... and besides who want to put in the password each time

thank for any help and direction you can give.

---

