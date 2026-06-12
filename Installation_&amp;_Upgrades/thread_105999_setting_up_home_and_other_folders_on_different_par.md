---
title: "setting up home and other folders on different partitions"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by daedalusman on 2005-12-19
Well this is what I want to do, I want to reconfigure my system so that my home folder and applications are not on the main system partition. I want to do this so that when I upgrade I wont have to worry about lossing a bunch of data and also so I want lose all my applications. What I need to know is what folders should I mount to their own partitions and how do I go about doing this without having to reinstall Ubuntu? I've been thinking about doing this for a while and the only way do to this that I've come up with is to just start fresh and reinstall, backing up my home folder of course. Is there possibly and easier way of doing this. At this point it would kill me to have to reinstall but I would rather wait to do that till Dapper Drake is finally released. Let me know if you need so more info and thanks for any help.

---

### Post by doitashimashite on 2005-12-19
Please post the output of the following commands:

sudo fdisk -l
cat /etc/fstab

On what partition would you like to mount your /home?

---

### Post by daedalusman on 2006-01-15
Well this is kinda of an extinsion to my first question, which I kinda forgot about because I ended up just reformatting and installing. But what I want to know now is if it is a good idea to setup a /boot on its own partition so that I could use the same boot folder for multiple linux distros, also how big should it be? If this isn't a good idea let me know. I'm not sure if this will mess up one install or thus rendering a certain distro unbootable or something along those lines. Thanks for the help, and at this point you can just ignore my first post if you want, but thanks for the reply doitashimashite.

---

