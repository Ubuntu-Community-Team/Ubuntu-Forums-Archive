---
title: "network manager applet gone"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by jimrz on 2006-02-18
Hi,

   I have been using breezy for several moths on my pc and just installed to my IBM ThinkPad T42 today. Install went smoothly. Had a couple of issues soon after, including the fact that, after intsalling network-manager and getting nm-applet running on the panel, I carelessly managed to remove said applet from the panel. How do I get it back?

---

### Post by neoflight on 2006-02-18
hmm...same case with me... i just installed the networkmanager following the wiki at sourceforge and added it to the startup programs using system>preference>sessions... 

but nothing happens when i try nm-applet from terminal and nothing showed up on gnome panel? i can't even run it from application launcher....whats the deal?

:confused:

---

### Post by jimrz on 2006-02-18
thanks neoflight,

same here...if find a way to fix will pass it on

are you able to connect to wireless without it? so far, i am not

---

### Post by neoflight on 2006-02-18
well...No.... i had the wireless working perfectly in my laptop. then i moved to another network and then it started giving me trouble. now i cannot connect with both!!!

[i am using wired connection now: eth0]
so was trying to get the network manager installed...then this trouble...

i posted a message with additional errors [here]("http://ubuntuforums.org/showthread.php?t=132721") too..

no idea whats going on...

---

### Post by neoflight on 2006-02-18
jimrz....

it worked... i installed it again and then it showed up on the panel at the top right corner... it is wired connection now so it shows a plug like icon. 

download and install from [here]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Multiple_Wireless_Profiles") ONLY. do not use synaptic or apt-get to do this... (as i am told :D)

follow the steps there carefully.. and run the dhcdbd first... otherwise you will run into dependancy issues...

hope this helps??

---

