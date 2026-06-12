---
title: "geforce 6200 in kubuntu"
date: 2010-07-05
forum: Hardware
---

### Post by vioman on 2010-07-05
I know this issue has been beaten to death just from reading the forums but nothing I do is working. I have a new geforce 6200 and I am trying to get it to work with the driver in kubuntu 9.04. Every time I try to boot it goes to just a command line interface. I am totally stumped trying to install this video card. Can anyone point me to or post the latest instruction for installing this video card. BTW it is an old computer with a 800 FSB and the vid card is AGP port.  :(:(:(

---

### Post by ubusr on 2010-07-05
I don't know the latest instructions, but maybe this guy's experience will provide some insight;

[http://www.enavigo.com/2010/05/29/nvidia-intel-and-ubuntu-fail/](http://www.enavigo.com/2010/05/29/nvidia-intel-and-ubuntu-fail/)

---

### Post by vioman on 2010-07-05
Thank you for your post!!!! it helped alot and directed me to the answer. How I fixed the problem. I un-installed everything using this post [http://ubuntuforums.org/showthread.php?t=813931&page=4](http://ubuntuforums.org/showthread.php?t=813931&page=4) I did everything I could on this post from step 2 to step 7 to clean all my attempts. I even deleted the .conf file outlined in the steps. I then usde sudo apt-get nvida-glx. the terminal will give you a list of the nvida drivers to down load. I then decided to start with the oldest and work my way to the newest. Each time I used the newer version i did sudo ldconfig then i did sudo nvidia-xconfig and the rebooted. ny particular driver was the sudo apt-get nvidia-glx-96. It worked after i rebooted. One note I did not remove the previous version when installing the newer version on the list. Thank you for all the posts now on to harder problems like gettin mce working in my home!! One other note.. Envy did not work for me using this particular card

---

