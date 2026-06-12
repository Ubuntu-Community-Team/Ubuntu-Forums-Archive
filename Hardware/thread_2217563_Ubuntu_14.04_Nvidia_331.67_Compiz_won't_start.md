---
title: "Ubuntu 14.04 Nvidia 331.67 Compiz won't start"
date: 2014-04-17
forum: Hardware
---

### Post by BaridBelMedar on 2014-04-17
I have tried installing the nvidia 331.67 and 331.62 drivers using the .run installers provided by nvidia, and both of them cause compiz and/or unity to not start when I log in. I get a background image a mouse cursor and nothing else.
The 331 driver from the repos works fine, but it gives me an error when trying to run code compiled with the cuda 6 toolkit.

---

### Post by sammykur on 2014-05-02
To install the run file you have to log out and press f1+alt+ctrl  ```
sudo service lightdm stop
``` then go to the file and run it ,then ```
sudo service lightdm start
``` exit the terminal

---

### Post by BaridBelMedar on 2014-05-02
I know how to install the drivers, I was able to install them fine, they just don't work with compiz/unity.

---

### Post by sammykur on 2014-05-03
I think this thread may hold your answer,

[http://askubuntu.com/questions/215016/unity-doesnt-appear-after-installing-nvidia-drivers](http://askubuntu.com/questions/215016/unity-doesnt-appear-after-installing-nvidia-drivers)


Never can tell what someone has done or not done ,the skill level of users varies so much.

---

