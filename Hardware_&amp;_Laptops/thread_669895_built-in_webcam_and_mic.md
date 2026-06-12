---
title: "built-in webcam and mic"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by boboyo on 2008-01-16
i got a built-in webacm and mic on my laptop and i am using ubuntu 7.10 gusty.
on the win$hit part of my laptop they work. its called HP webcam for the webcam
on ubuntu, when i go on msn, i cant use them.

does anyone have the right program for that?
or is there a version of HP webcam for linux?

---

### Post by Ronin324 on 2008-01-16
Well working with webcams in Ubuntu can be a bit of a challange. It took me some time searching and reading to get it to work. Here are a few things you can try. There is a program called Easy Cam 2 that can be loaded under the Sympatic Package Manager or with the apt-get command from the console. This program can load drivers for some webcam automaticly. If that does not work try running a lspci command or lsusb command to try and find your webcam listed. It should list the hardware address and the manufacture and model. Then search the ubuntu forums and the net for some drivers. I will wish you luck it can be frustrating but thats how we all learn.

---

### Post by boboyo on 2008-01-20
how do i run lspci?

i cant find easy cam in synaptics

---

### Post by Ronin324 on 2008-01-20
> **boboyo said:**
> how do i run lspci?

i cant find easy cam in synaptics

lspci is a command that runs from the linux terminal. If you go to Applications >  Accessories > Terminal the command prompt terminal will open. This is where you enter all the text based linux commands. This is something that you should get familiar with in linux. Then type lspci and hit enter.  This command outputs a list of devices in the computer.

Easy Cam might not be listed in synamptics unless you have the source files configured. Go to System >  Administration > Software Sources. This will control where Ubuntu will look for packages. 

Look under Ubuntu Software tab and check most of the boxes. The only one you might want to avoid is the back ports. Then close out the sources and it will update the Synaptics list. Check there again for Easy Cam. Also you may need to run a system update as well.

Hope That Helps

---

### Post by boboyo on 2008-01-20
a guy already old me to do that and i did it
yhe only one that is not checked is the cd thing (because my friend has my ubuntu CD) and i still cant find easy cam

---

### Post by linuxwizard on 2008-01-20
You need to add EasyCam repository to your source list.

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by boboyo on 2008-01-20
i did that but i still cant find it :(

---

### Post by boboyo on 2008-01-25
i cant find webcam2 in synaptics

---

