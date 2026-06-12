---
title: "cable internet not working."
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by bajabug72 on 2005-06-20
ive got a p4 1.8(dont rememer if its overclocked to a 2.0 or not) dual boot XP media and ubuntu 5.04.  im hoping to eventually eliminate winblows entirely and go all Mac and Linux. in winblows xp my internet works fine, but when i boot to linux it doesnt work at all.  i know they are completely diffrent, but i know its not a hardware-screwed-up problem.  im kind of a newbie with linux but i have no problem digging into it to get it to work.  if it matters, i have comcast cable internet, network cable from modem box to a d-link DI-604 router and then from the first plug on the router to the NIC in the comp.  not sure if it matters, but if it does, there it is.  

thanks in advance, Jon

---

### Post by mohaham on 2005-06-20
run this command in the terminal box
sudo ifup eth0

if the above gives errors post the contents of the file /etc/network/interfaces

---

### Post by bajabug72 on 2005-06-26
sorry i havent replied earlier, ive been working.  i ran that and it still doesnt work.  im not at home now and cant remember what the file said, but regardless, its not working.  if i can get it to work i will use ubuntu more than XP mainly because im sick of windows.  all i lack is internet and i will love it.

---

### Post by bajabug72 on 2005-07-02
i figured out my problem.  ubuntu didnt like my network card.  swapped it out just for the heck of it and it works fine.  but now my resolution is set at 640 x 480 and it wont let me adjust it.  in windows i have it set to 1280 x 1024 and it being this huge is killing me!!  how do i get it to adjust to atleast 1024 x 768??  

thanks in advance, Jon

---

### Post by oofnik on 2005-07-03
Sounds like your hardware info got corrupted somehow. I would open up /etc/X11/xorg.conf and add some resolutions in the Screen section, but editing that could screw up X for good, so it's probably not such a good idea for someone who's new(er) to it. Ehh I wish I could remember the easy way to do that. :p

---

