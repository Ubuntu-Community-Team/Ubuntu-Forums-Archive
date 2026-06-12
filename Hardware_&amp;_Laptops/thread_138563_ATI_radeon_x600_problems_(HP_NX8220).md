---
title: "ATI radeon x600 problems (HP NX8220)"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by o00 on 2006-03-02
Hello everyone,

I own laptop HP nx8220 and i have ati radeon x600 graphic card in it! I have several problems with X server and i can't access desktop because i probably need some other drivers. I don't know how to configure internet connection in bash (so i cant download drivers with apt-get) because i'm a newbie and i dont know what to do to finally start X and start using ubuntu in graphical enviroment. Can please, please someone help me with some good how-to? i only need commands to copy, no extra explanations are needed.

for now i can only say i did download some ati driver "xorg-driver-fglrx-dev_6.8.0-8.8.25-0ubuntu11_i386.deb" on windows, burned on cd and copy it to /home/myusername/ but after help on #ubuntu channel i still cant fix this thing out.

If someone gives me a complete solution i buy him few beerz! :)

---

### Post by dspring on 2006-03-02
Hi, I just went through this on my nx9600. To get you past that xserver window stuff... keep hitting enter until you get to the login. I trust you have set a root password up in the beginning. Log in to root at the $login by typing (su root), when the # shows you are in root type the following:

#cd /etc/X11
#cp xorg.conf xorg.conf.org

#nano xorg.conf
  
(scroll down the text in nano and add the line Option:  "noaccel" in section device above end of device line like below)

Option                  “noaccel”
End of Device

on the menu at the bottom of the nano window there is an option to write press the control key and use the appropriate letter and it will write (change the configuration file. Use control again with "X" to exit this and it will return you to the root prompt# where you started. Then just type reboot and you will get into Ubuntu graphical and it will prompt for user or root password... you're in. By the way that download you got can be used with this link:

[http://equickfixes.com/2006/02/08/hp-nx-laptop-ubuntu-linux-xwindows-configuration/#more-10](http://equickfixes.com/2006/02/08/hp-nx-laptop-ubuntu-linux-xwindows-configuration/#more-10)

I haven't tried it yet because I have slow inet and haven't gotten the driver, there are other posts here you should look for too concerning this. I must give credit for the info above to someone else here on the forum who posted it, sorry cannot remember now. My thanks to them.. I struggled for several days with other code that didn't work. Anyway have fun hope it helps you too.  
David

---

